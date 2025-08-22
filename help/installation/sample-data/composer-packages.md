---
title: 샘플 데이터 작성기 패키지 다운로드
description: 다음 단계에 따라 Composer PHP Package Manager를 사용하여 Adobe Commerce 샘플 데이터를 설치합니다.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# 샘플 데이터 작성기 패키지 다운로드

이 섹션에서는 다음 방법 중 하나로 Adobe Commerce 소프트웨어를 사용하는 경우 샘플 데이터를 설치하는 방법에 대해 설명합니다.

* `https://magento.com/tech-resources/download`에서 압축된 보관 파일을 다운로드했습니다.

  GitHub에서 보관 파일을 다운로드한 경우 `composer.json` 파일에 `repo.magento.com` URL이 없으므로 이 메서드가 작동하지 않습니다.

* `composer create-project` 사용됨

이 방법으로 Adobe Commerce의 샘플 데이터를 가져올 수 있지만 응용 프로그램을 설치하는 데 사용한 것과 동일한 [인증 키](../prerequisites/authentication-keys.md)를 사용해야 합니다.

>[!NOTE]
>
>`Could not find package...` 또는 `...no matching package found...`과(와) 같은 오류가 발생하면 명령에 오타가 없는지 확인하십시오. 그래도 오류가 발생하면 특히 Adobe Commerce을 사용하는 경우 올바른 Composer 저장소에 액세스하지 못할 수 있습니다. 도움이 필요하면 [Adobe Commerce 지원](https://support.magento.com/hc/en-us)에 문의하십시오.

Composer를 사용하여 응용 프로그램을 설치하기 전이나 후에 샘플 데이터를 설치할 수 있지만, [추가 작업](remove-or-update.md)이 있을 수 있습니다.

기여 개발자인 경우 [저장소를 복제하여 설치](git-repositories.md)를 참조하십시오.

>[!WARNING]
>
>응용 프로그램이 [프로덕션 모드](../../configuration/bootstrap/application-modes.md#production-mode)로 설정된 경우 샘플 데이터를 설치하지 마십시오. 먼저 [개발자 모드](../../configuration/bootstrap/application-modes.md#developer-mode)(으)로 전환하세요. 프로덕션 모드에서 샘플 데이터를 설치하는 동안 [실패](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-)합니다.

명령줄을 사용하여 샘플 데이터를 설치하려면 `<app_root>` 디렉터리에 파일 시스템 소유자로 다음 명령을 입력하십시오.

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>응용 프로그램을 설치하는 동안 샘플 데이터 _after_&#x200B;를 설치하는 경우 `<app_root>` 디렉터리에서 데이터베이스 및 스키마를 업데이트하려면 다음 명령도 실행해야 합니다.

```bash
bin/magento setup:upgrade
```

작업을 완료하려면 [인증](../prerequisites/authentication-keys.md)해야 합니다.

## 인증 오류

다음 인증 오류가 표시될 수 있습니다.

```
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

오류가 표시되면 응용 프로그램 설치 디렉터리를 변경하고 `composer update`을(를) 실행하여 [인증 키](../prerequisites/authentication-keys.md)를 입력하라는 메시지가 표시됩니다.

## 샘플 데이터 설치를 완료합니다

{{$include /help/_includes/sample-data-complete.md}}

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
