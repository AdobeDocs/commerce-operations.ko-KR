---
title: 카탈로그 이미지 크기 조정 우수 사례
description: Adobe Commerce 사이트의 프로덕션 시작 전에 성능 저하를 방지하는 방법을 알아봅니다.
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---


# 카탈로그 이미지 크기 조정 우수 사례

스토어가 프로덕션으로 전환되기 전에 모든 카탈로그 이미지의 크기를 조정해야 합니다. 프로덕션 전에 이미지 크기를 조정하지 않으면 페이지 로드 중 이미지 크기가 조정되어 사이트 속도가 크게 감소하고 시작 후 첫 날부터 몇 주 동안 서버 로드가 증가합니다.

## 천천히 가는 길

기본 CLI 명령을 사용하여 모든 이미지 크기를 조정합니다.

```bash
bin/magento catalog:images:resize
```

이 접근 방식의 단점은 다음과 같습니다.

- 이 프로세스는 단일 스레드입니다
- 이 프로세스는 이미 크기가 조정된 이미지의 크기를 조정합니다
- 프로세스를 중단할 수 없으며 며칠이 걸릴 수 있습니다

## 빠른 방법

비동기 이미지 크기 조정은 Adobe Commerce 2.4에 도입되었으며 이미지 크기를 더 빠르게 조정할 수 있습니다.

1. 모든 웹 서버에서 추가 큐 핸들러를 일시적으로 시작합니다(서버당 실제 프로세서 수의 두 배).

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. 큐 핸들러가 실행 중인지 확인합니다.

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. 모든 이미지 크기 조정 요청으로 큐를 채웁니다.

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. 모든 이미지 크기를 조정한 후 프로세스를 종료합니다.

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## 빠른 방법

프론트엔드를 사용하여 이미지 크기를 조정할 수 있는 다른 방법이 있습니다.

이 접근 방식의 장점은 다음과 같습니다.

- 프로세스가 다중 스레드됩니다.
- 이 프로세스는 다중 서버입니다(여러 웹 노드, 로드 밸런서 및 `media/` directory)
- 이미 크기가 조정된 이미지는 건너뜁니다

이 방법은 8시간 이내에 이미지 100,000개의 크기를 조정하는 반면, CLI 명령은 완료하는 데 6일이 소요됩니다.

1. 서버에 로그인.
1. 다음으로 이동 `pub/media/catalog/product` 해시 중 하나를 기록해 둡니다(예: 0047d83143a5a3a4683afdf1116df680).
1. 다음 예에서 `www.example.com` 를 저장소의 도메인으로 바꾸고 해시를 기록한 도메인으로 바꿉니다.

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB 공성전]

의 단점 `siege` 동시성이 10으로 설정된 경우 10번의 모든 URL을 방문한다는 것입니다.

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB 컬]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

다음 `-P` 인수는 스레드 수를 결정합니다.

>[!TAB 배시 원라이너]

The one-liner for the `find/curl` 예를 들어 다음을 실행할 수 있는 경우 `curl` 이미지가 있는 동일한 컴퓨터에서:

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

다시, 바꾸기 `www.example.com` (웹 사이트의 도메인 및 세트 포함) `-P` 서버가 충돌하지 않고 처리할 수 있는 스레드 수.

>[!ENDTABS]

출력에서 스토어의 모든 제품 이미지 목록을 반환합니다. 이미지를 크롤링할 수 있습니다( 사용). `siege` 또는 다른 모든 크롤러)를 사용할 수 있는 모든 서버와 프로세서 코어를 사용하고 다른 접근 방식보다 훨씬 빠른 속도로 크기 조정 캐시를 생성합니다.

이미지 캐시 URL 하나를 방문하면 아직 존재하지 않는 경우 백그라운드에서 모든 이미지 크기가 생성됩니다. 또한 이미 크기가 조정된 파일을 건너뜁니다.

>[!NOTE]
>
>- 클라우드 인프라 프로젝트의 Adobe Commerce은 제품 이미지 크기 조정을 Fastly 서비스로 오프로드할 수 있습니다. 다음을 참조하십시오 [심층 이미지 최적화](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=en#deep-image-optimization) 다음에서 _Cloud 안내서_.
>- 원격 스토리지 모듈을 사용하는 경우 이미지 크기 조정을 nginx로 오프로드할 수도 있습니다. 다음을 참조하십시오 [원격 스토리지에 대한 이미지 크기 조정 구성](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html) 다음에서 _구성 안내서_.
