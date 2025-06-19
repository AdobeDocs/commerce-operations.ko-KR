---
title: 'ACSD-65127: 프로덕션 모드에서 JavaScript 축소를 수행하면 브라우저에  [!DNL TinyMCE] 6 오류가 발생합니다.'
description: ACSD-65127 패치를 적용하여 프로덕션 모드에서 JavaScript 축소를 활성화하면  [!DNL TinyMCE] 6에서 브라우저 콘솔에 오류가 발생하여 기능 및 사용자 환경에 영향을 주는 Adobe Commerce 문제를 해결합니다.
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: c878d5a4-8059-4bfc-93a8-0a9606e866fc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-65127: 프로덕션 모드에서 JavaScript 축소를 수행하면 브라우저에 [!DNL TinyMCE] 6개의 오류가 발생합니다

ACSD-65127 패치는 프로덕션 모드에서 JavaScript 축소를 활성화하면 [!DNL TinyMCE] 6에서 브라우저 콘솔에 오류가 발생하여 기능과 사용자 환경에 영향을 주는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-65127입니다. 이 문제는 Adobe Commerce 2.4.8에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 페이지에서 호환성을 확인하십시오. 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

프로덕션 모드에서 JavaScript 축소를 사용하도록 설정하면 [!DNL TinyMCE] 6에서 브라우저 콘솔에서 오류가 발생하여 기능 및 사용자 환경에 영향을 줍니다.

<u>재현 단계</u>:

1. 아래 명령을 실행하여 구성을 설정합니다.

```
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

1. 프로덕션 모드를 활성화합니다.

```
bin/magento deploy:mode:set production
```

1. 관리 사이드바에서 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동합니다. 나열된 제품에서 **[!UICONTROL Edit]**&#x200B;을(를) 클릭하고 **[!UICONTROL Content]**(으)로 스크롤한 다음 **[!UICONTROL Show Editor]**&#x200B;을(를) 선택합니다.

<u>예상 결과</u>:

브라우저 콘솔에 JS 오류가 없습니다.

<u>실제 결과</u>:

js `tiny_mce_6/plugins/help/js/i18n/keynav/en.js`에 대한 브라우저 콘솔에서 *404* 오류가 발생했습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
