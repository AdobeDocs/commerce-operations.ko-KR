---
title: 패치 적용
description: Adobe Commerce 또는 Magento Open Source 프로젝트에 패치를 적용하는 방법에 대해 알아봅니다.
source-git-commit: e2ddb30da8dd86236e1dcf33a3f911b67384a6d7
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# 패치 적용

다음 방법 중 하나를 사용하여 패치를 적용할 수 있습니다.

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}
- [명령줄](../patches/apply.md#command-line)
- [작성기](../patches/apply.md#composer)

## 작성기

>[!IMPORTANT]
>
>공식 품질 패치를 적용하려면 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}. 사용자 정의 패치를 배포하기 전에 항상 포괄적인 테스트를 수행합니다.

작성기를 사용하여 사용자 지정 패치를 적용하려면

1. 명령줄 응용 프로그램을 열고 프로젝트 디렉토리로 이동합니다.
1. 추가 `cweagans/composer-patches` 플러그인에 대한 `composer.json` 파일.

   ```bash
   composer require cweagans/composer-patches
   ```

1. 편집 `composer.json` 파일을 추가하고 다음 섹션을 추가하여 지정합니다.
   - **모듈:** *\&quot;magento/module-payment\&quot;*
   - **제목:** *\&quot;MAGETWO-56934: 잘못된 신용 카드가 있는 Authorize.net으로 주문할 때 체크아웃 페이지가 중지됩니다.\&quot;*
   - **패치 경로:** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

   For example:

   ```json
   "extra": {
       "composer-exit-on-patch-failure": true,
       "patches": {
           "magento/module-payment": {
               "MAGETWO-56934: Checkout page freezes when ordering with Authorize.net with invalid credit card": "patches/composer/github-issue-6474.diff"
           }
       }
   }
   ```

   패치가 여러 모듈에 영향을 주는 경우 여러 모듈을 대상으로 하는 여러 패치 파일을 생성해야 합니다.

1. 패치를 적용합니다. 를 사용하십시오 `-v` 디버깅 정보를 보려는 경우에만 옵션을 선택합니다.

   ```bash
   composer -v install
   ```

1. 업데이트 `composer.lock` 파일. 잠금 파일은 개체의 각 작성기 패키지에 적용된 패치를 추적합니다.

   ```bash
   composer update --lock
   ```

## 명령줄

명령줄에서 패치를 적용하려면

1. 로컬 파일을 `<Magento_root>` FTP, SFTP, SSH 또는 일반적인 전송 방법을 사용하여 서버의 디렉토리입니다.
1. 서버로 로그인합니다. [관리자 사용자](../../configuration/cli/config-cli.md#prerequisites) 그리고 파일이 올바른 디렉토리에 있는지 확인합니다.
1. 명령줄 인터페이스에서 패치 확장에 따라 다음 명령을 실행합니다.

   ```bash
   patch < patch_file_name.patch
   ```

   이 명령은 패치할 파일이 패치 파일을 기준으로 있다고 가정합니다.

   >[!NOTE]
   >
   >명령줄에 다음이 표시되는 경우: `File to patch:`즉, 경로가 올바른 경우에도 의도한 파일을 찾을 수 없음을 의미합니다. 명령줄 터미널에 표시된 상자에서 첫 번째 줄에 패치할 파일이 표시됩니다. 파일 경로를 복사하여 `File to patch:` 프롬프트 `Enter` 그리고 패치가 완료되어야 합니다.

1. 변경 사항을 반영하려면 아래의 관리자에서 캐시를 새로 고칩니다. **시스템** > 도구 > **캐시 관리**.

   또는 패치를 동일한 명령을 사용하여 로컬에 적용한 다음 커밋하고 정상적으로 푸시할 수 있습니다.
