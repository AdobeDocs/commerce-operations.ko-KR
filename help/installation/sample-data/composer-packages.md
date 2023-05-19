---
title: 샘플 데이터 작성기 패키지 다운로드
description: 다음 단계에 따라 Composer PHP Package Manager를 사용하여 Adobe Commerce 및 Magento Open Source 샘플 데이터를 설치합니다.
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# 샘플 데이터 작성기 패키지 다운로드

이 섹션에서는 다음 방법 중 하나로 Adobe Commerce 또는 Magento Open Source 소프트웨어를 설치한 경우 샘플 데이터를 설치하는 방법에 대해 설명합니다.

* 에서 압축된 아카이브를 다운로드했습니다. `https://magento.com/tech-resources/download`.

   GitHub에서 아카이브를 다운로드한 경우 다음과 같은 이유로 이 메서드가 작동하지 않습니다. `composer.json` 파일에 `repo.magento.com` URL.

* 사용됨 `composer create-project`

이 방법을 사용하여 Adobe Commerce과 Magento Open Source 모두에 대한 샘플 데이터를 가져올 수 있지만, 동일한 데이터를 사용해야 합니다 [인증 키](../prerequisites/authentication-keys.md) 응용 프로그램을 설치하는 데 사용한

>[!NOTE]
>
>오류가 발생하면 다음과 같이 `Could not find package...` 또는 `...no matching package found...`를 클릭하고, 명령에 오타가 없는지 확인합니다. 그래도 오류가 발생하면 특히 Adobe Commerce을 사용하는 경우 올바른 Composer 저장소에 액세스하지 못할 수 있습니다. 연락처 [Adobe Commerce 지원](https://support.magento.com/hc/en-us) 도와주세요.

Composer를 사용하여 애플리케이션을 설치하기 전이나 후에 샘플 데이터를 설치할 수 있지만, [추가 작업](remove-or-update.md).

기여 개발자인 경우 다음을 참조하십시오. [저장소를 복제하여 설치](git-repositories.md).

>[!WARNING]
>
>애플리케이션이 로 설정된 경우 샘플 데이터를 설치하지 마십시오. [프로덕션 모드](../../configuration/bootstrap/application-modes.md#production-mode). 다음으로 전환 [개발자 모드](../../configuration/bootstrap/application-modes.md#developer-mode) 첫 번째. 프로덕션 모드에서 샘플 데이터 설치 [실패](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

명령줄을 사용하여 샘플 데이터를 설치하려면 다음 명령을 파일 시스템 소유자로 `<app_root>` 디렉터리:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>샘플 데이터를 설치하는 경우 _이후_ 응용 프로그램을 설치하는 동안 다음 명령을 실행하여 의 데이터베이스 및 스키마를 업데이트해야 합니다 `<app_root>` 디렉터리:

```bash
bin/magento setup:upgrade
```

다음을 수행해야 합니다. [인증](../prerequisites/authentication-keys.md) 을 클릭하여 작업을 완료합니다.

## 인증 오류

다음 인증 오류가 표시될 수 있습니다.

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

오류가 표시되면 응용 프로그램 설치 디렉토리로 변경하고 를 실행합니다 `composer update`을 묻는 메시지가 표시됩니다. [인증 키](../prerequisites/authentication-keys.md).

## 샘플 데이터 설치를 완료합니다

{{$include /help/_includes/sample-data-complete.md}}
