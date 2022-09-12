---
title: 샘플 데이터 작성기 패키지 다운로드
description: 다음 단계에 따라 작성기 PHP 패키지 관리자를 사용하여 Adobe Commerce 및 Magento Open Source 샘플 데이터를 설치합니다.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# 샘플 데이터 작성기 패키지 다운로드

이 섹션에서는 다음 방법 중 하나로 Adobe Commerce 또는 Magento Open Source 소프트웨어를 보유한 경우 샘플 데이터를 설치하는 방법을 설명합니다.

* 에서 압축된 보관 파일 다운로드 `https://magento.com/tech-resources/download`.

   GitHub에서 아카이브를 다운로드한 경우 `composer.json` 파일에 `repo.magento.com` URL.

* 사용됨 `composer create-project`

이 방법을 사용하여 Adobe Commerce과 Magento Open Source 모두에 대한 샘플 데이터를 가져올 수 있지만 사용해야 합니다 [인증 키](../prerequisites/authentication-keys.md) 응용 프로그램을 설치하는 데 사용한 것입니다.

>[!NOTE]
>
>다음과 같은 오류가 발생하는 경우 `Could not find package...` 또는 `...no matching package found...`를 입력하여 명령에 오타가 없는지 확인합니다. 여전히 오류가 발생하면 특히 Adobe Commerce을 사용하는 경우 올바른 작성기 리포지토리에 액세스할 수 없을 수 있습니다. 연락처 [Adobe Commerce 지원](https://support.magento.com/hc/en-us) 도움이 필요합니다.

작성기 를 사용하여 애플리케이션을 설치하기 전이나 후에 샘플 데이터를 설치할 수 있습니다. 하지만 [추가 작업](remove-or-update.md).

기여 개발자인 경우 [복제 리포지토리로 설치](git-repositories.md).

>[!WARNING]
>
>응용 프로그램이 인 경우 샘플 데이터를 설치하지 마십시오 [프로덕션 모드](../../configuration/bootstrap/application-modes.md#production-mode). 다음으로 전환 [개발자 모드](../../configuration/bootstrap/application-modes.md#developer-mode) 먼저 프로덕션 모드에서 샘플 데이터 설치 [실패](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

명령줄에서 샘플 데이터를 설치하려면 다음 명령을 파일 시스템 소유자로 입력합니다 `<app_root>` 디렉토리:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>샘플 데이터를 설치하는 경우 _after_ 응용 프로그램을 설치하려면 다음 명령을 실행하여 `<app_root>` 디렉토리:

```bash
bin/magento setup:upgrade
```

다음을 수행해야 합니다. [인증](../prerequisites/authentication-keys.md) 를 눌러 작업을 완료합니다.

## 인증 오류

다음 인증 오류가 표시될 수 있습니다.

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

오류가 표시되면 응용 프로그램 설치 디렉토리로 변경한 다음 실행합니다 `composer update`에 대해 묻는 메시지가 [인증 키](../prerequisites/authentication-keys.md).

## 샘플 데이터 설치 완료

{{$include /help/_includes/sample-data-complete.md}}
