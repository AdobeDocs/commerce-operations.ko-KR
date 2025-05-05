---
title: 원격 스토리지 구성
description: 온-프레미스 Commerce 애플리케이션에 대한 원격 저장소 모듈을 구성하는 방법에 대해 알아봅니다.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 419a21604d1fda0a76dd0375ae2340fd6e59ec89
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# 원격 스토리지 구성

원격 스토리지 모듈은 미디어 파일을 저장하고 AWS S3와 같은 스토리지 서비스를 사용하여 영구적인 원격 스토리지 컨테이너에 가져오기 및 내보내기를 예약하는 옵션을 제공합니다.

기본적으로 Adobe Commerce 애플리케이션은 애플리케이션이 포함된 동일한 파일 시스템에 미디어 파일을 저장합니다. 이는 복잡한 다중 서버 구성에서 비효율적이며 리소스를 공유할 때 성능이 저하될 수 있습니다. 원격 저장소 모듈을 사용하면 미디어 파일을 `pub/media` 디렉터리에 저장하고 원격 개체 저장소의 `var` 디렉터리에 파일을 가져오거나 내보내 서버측 이미지 크기 조정을 활용할 수 있습니다.

>[!BEGINSHADEBOX]

원격 저장소 _과(와)_ 데이터베이스 저장소를 동시에 사용하도록 설정할 수 없습니다. 원격 저장소를 활성화하기 전에 데이터베이스 저장소를 비활성화해야 합니다.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

원격 저장소를 사용하도록 설정하면 설정된 개발 경험 환경에 영향을 줄 수 있습니다. 예를 들어, 특정 PHP 파일 함수가 예상대로 작동하지 않을 수 있습니다. 파일 작업에 Commerce Framework를 사용해야 합니다. 금지된 PHP 기본 함수 목록은 magento-coding-standard[&#128279;](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php) 저장소에서 사용할 수 있습니다.

>[!ENDSHADEBOX]

>[!INFO]
>
>- 원격 저장소는 Commerce 버전 2.4.2 이상에서만 사용할 수 있습니다. [2.4.2 릴리스 정보](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-2)를 참조하세요.
>
>- 원격 스토리지 모듈에 클라우드 인프라의 Adobe Commerce에 대한 _제한_ 지원이 있습니다. Adobe이 타사 스토리지 어댑터 서비스의 문제를 완전히 해결할 수 없습니다. 클라우드 프로젝트를 위한 원격 스토리지 구현에 대한 지침은 Commerce on Cloud 인프라[&#128279;](cloud-support.md)에 대한 원격 스토리지 구성을 참조하십시오.

![스키마 이미지](../../assets/configuration/remote-storage-schema.png)

## 원격 저장소 옵션

CLI 명령과 `remote-storage` 함께 옵션을 사용하여 원격 스토리지를 [`setup` 구성할 수 있습니다](../../installation/tutorials/deployment.md). 이 `remote-storage` 옵션은 다음 구문을 사용합니다.

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

`parameter-name` 특정 원격 저장소 매개 변수 이름을 나타냅니다. 다음 표에는 원격 저장소를 구성하는 데 사용할 수 있는 매개 변수가 나열되어 있습니다.

| 명령줄 매개 변수 | 매개 변수 이름 | 설명 | 기본값 |
|--- |--- |--- |--- |
| `remote-storage-driver` | 드라이버 | 어댑터 이름<br>가능한 값:<br>**파일**: 원격 스토리지를 사용하지 않도록 설정하고 로컬 파일 시스템을 사용&#x200B;<br>**aws-s3**: [Amazon Simple Storage Service(Amazon S3) 사용](remote-storage-aws-s3.md) | 없음 |
| `remote-storage-bucket` | 버킷 | 개체 저장소 또는 컨테이너 이름 | 없음 |
| `remote-storage-prefix` | 접두사 | 선택적 접두사(오브젝트 스토리지 내부 위치) | 비우다 |
| `remote-storage-region` | 지역 | 지역 이름 | 없음 |
| `remote-storage-key` | 액세스 키 | 선택적 액세스 키 | 비우다 |
| `remote-storage-secret` | 비밀 키 | 선택적 비밀 키 | 비우다 |

### 스토리지 어댑터

기본 저장소 위치는 로컬 파일 시스템에 있습니다. _저장소 어댑터_&#x200B;을(를) 사용하면 저장소 서비스에 연결하여 어디에나 파일을 저장할 수 있습니다. [!DNL Commerce]에서 다음 저장소 서비스 구성을 지원합니다.

- [Amazon Simple Storage Service(Amazon S3)](remote-storage-aws-s3.md)

## 원격 저장소 활성화

Adobe Commerce 설치 중에 원격 저장소를 설치하거나 기존 Commerce 인스턴스에 원격 저장소를 추가할 수 있습니다. 다음 예에서는 Commerce `setup` CLI 명령과 함께 매개 변수 집합을 `remote-storage` 사용하는 각 방법을 보여줍니다. 최소한 스토리지 `driver`, `bucket`, 및 `region`를 제공해야 합니다.

- 예: 원격 스토리지로 Commerce 설치

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- 예: 기존 Commerce에서 원격 스토리지 활성화

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>클라우드 인프라의 Adobe Commerce에 대해서는 [클라우드 인프라의 Commerce에 대한 원격 저장소 구성](cloud-support.md)을 참조하십시오.

## 콘텐츠 마이그레이션

특정 어댑터에 대해 원격 스토리지를 사용으로 설정한 후 CLI를 사용하여 기존 _미디어_ 파일을 원격 스토리지로 마이그레이션할 수 있습니다.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>동기화 명령은 디렉토리에 `pub/media` 있는 파일만 마이그레이션하고 _디렉토리에 있는 `var` 가져오기/내보내기 파일은 마이그레이션하지 않습니다_. Commerce 2.4 사용 안내서에서 _예약된 가져오기/내보내기[&#128279;](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html)를 참조하십시오._

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
