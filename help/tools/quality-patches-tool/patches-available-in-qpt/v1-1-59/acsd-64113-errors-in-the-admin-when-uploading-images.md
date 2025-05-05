---
title: 'ACSD-64113:  [!DNL Media Gallery]을(를) 통해 높이보다 작은 너비로 이미지를 업로드하는 동안 관리자 오류가 발생했습니다.'
description: ACSD-64113 패치를 적용하여  [!DNL Media Gallery]을(를) 통해 높이에 비해 상대적으로 작은 너비로 이미지를 업로드할 때(또는 그 반대로) 관리자에서 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
source-git-commit: b9433897d2658ecbe0b8d7f9932c15824f2ecca6
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64113: [!DNL Media Gallery]을(를) 통해 높이보다 작은 너비로 이미지를 업로드하는 동안 관리자 오류가 발생했습니다.

ACSD-64113 패치는 [!DNL Media Gallery]을(를) 통해 높이에 비해 상대적으로 작은 너비의 이미지를 업로드할 때(또는 그 반대로) 관리자에서 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-64113입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자는 [!DNL Media Gallery]을(를) 통해 높이에 비해 상대적으로 작은 너비의 이미지를 업로드할 때 오류가 발생합니다(또는 그 반대의 경우).

<u>재현 단계</u>:

1. **[!UICONTROL Content]** > **[!UICONTROL Media]** > **[!UICONTROL Media Gallery]**(으)로 이동하여 **[!UICONTROL wysiwyg]** 디렉터리를 선택합니다.
1. 높이에 비해 상대적으로 작은 너비로 이미지를 업로드합니다(또는 그 반대로).

<u>예상 결과</u>:

이미지가 오류 없이 업로드됩니다.

<u>실제 결과</u>:

1. 다음 오류 메시지가 표시됩니다.

   *서버에 기술적인 문제가 있어 오류가 발생했습니다. 계속하기 위해 다시 시도하십시오. 문제가 지속되면 나중에 다시 시도하십시오.*
1. `var/log/exception.log`에 포함된 항목:

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   또는

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
