---
title: 패치 적용
description: Adobe Commerce 프로젝트에 패치를 적용하는 방법에 대해 알아봅니다.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 패치 적용

다음 방법 중 하나를 사용하여 패치를 적용할 수 있습니다.

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko){target="_blank"}
- [명령줄](../patches/apply.md#command-line)
- [작성기](../patches/apply.md#composer)


>[!TIP]
>
>엔터프라이즈 규모의 Adobe Commerce에 대한 중앙 집중식 패치에 대한 자세한 내용은 [모범 사례](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md)를 참조하세요.

## 작성기

>[!IMPORTANT]
>
>공식 품질 패치를 적용하려면 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko){target="_blank"}을(를) 사용합니다. 사용자 정의 패치를 배포하기 전에 항상 포괄적인 테스트를 수행하십시오.

작성기를 사용하여 사용자 정의 패치를 적용하려면 다음을 수행합니다.

1. 명령줄 응용 프로그램을 열고 프로젝트 디렉터리로 이동합니다.
1. `cweagans/composer-patches` 플러그인을 `composer.json` 파일에 추가합니다.

   ```bash
   composer require cweagans/composer-patches
   ```

1. `composer.json` 파일을 편집하고 다음 섹션을 추가하여 지정하십시오.
   - **모듈:** *\&quot;magento/module-payment\&quot;*
   - **제목:** *\&quot;MAGETWO-56934: 잘못된 신용 카드로 Authorize.net을 사용하여 주문할 때 체크아웃 페이지가 중지됩니다\&quot;*
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

   패치가 여러 모듈에 영향을 주는 경우 여러 모듈을 대상으로 하는 여러 패치 파일을 만들어야 합니다.

1. 패치를 적용합니다. 디버깅 정보를 보려면 `-v` 옵션을 사용하십시오.

   ```bash
   composer -v install
   ```

1. `composer.lock` 파일을 업데이트합니다. 잠금 파일은 개체의 각 Composer 패키지에 적용된 패치를 추적합니다.

   ```bash
   composer update --lock
   ```

## 명령줄

명령줄에서 패치를 적용하려면 다음을 수행합니다.

1. FTP, SFTP, SSH 또는 일반적인 전송 방법을 사용하여 서버의 `<Magento_root>` 디렉터리에 로컬 파일을 업로드합니다.
1. 서버에 [admin user](../../configuration/cli/config-cli.md#prerequisites)(으)로 로그인하고 파일이 올바른 디렉터리에 있는지 확인하십시오.
1. 명령줄 인터페이스에서 패치 확장에 따라 다음 명령을 실행합니다.

   ```bash
   patch < patch_file_name.patch
   ```

   이 명령은 패치할 파일이 패치 파일을 기준으로 있다고 가정합니다.

   >[!NOTE]
   >
   >명령줄에 `File to patch:`이(가) 표시되면 경로가 올바른 것 같더라도 의도한 파일을 찾을 수 없다는 의미입니다. 명령줄 터미널에 표시된 상자에서 첫 번째 줄에 패치할 파일이 표시됩니다. 파일 경로를 복사하여 `File to patch:` 프롬프트에 붙여 넣고 `Enter`을(를) 누르면 패치가 완료됩니다.

1. 변경 사항을 반영하려면 **시스템** > 도구 > **캐시 관리**&#x200B;에서 관리자의 캐시를 새로 고치십시오.

   또는 동일한 명령으로 패치를 로컬에 적용한 다음 커밋하고 정상적으로 푸시할 수 있습니다.
