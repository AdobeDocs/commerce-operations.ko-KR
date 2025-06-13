---
title: 'ACSD-48857:  [!DNL Page Builder](으)로 편집한 후 변경 내용을 저장할 수 없음'
description: ACSD-48857 패치를 적용하여  [!DNL Page Builder](으)로 편집한 후 사용자가 변경 사항을 저장할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace, CMS, Page Builder
role: Admin
exl-id: b03cd597-8fef-4528-9699-793dc61d34da
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-48857: [!DNL Page Builder]&#x200B;(으)로 편집한 후 변경 내용을 저장할 수 없음

ACSD-48857 패치는 [!DNL Page Builder]&#x200B;(으)로 편집한 후 사용자가 변경 사항을 저장할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48857입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Page Builder]&#x200B;(으)로 편집한 후 변경 내용을 저장할 수 없습니다.

<u>재현 단계</u>

1. 관리 웹 사이트에 로그인합니다.
1. 빈 CMS 페이지를 만들려면 **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**(으)로 이동합니다.
1. 이 SQL 스크립트를 실행하여 다음 **[!UICONTROL Content]** 필드 값을 설정하십시오.

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. 관리자의 **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**(으)로 돌아갑니다.
1. 페이지를 편집합니다.
1. **[!UICONTROL Content]** 탭으로 이동합니다.
1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>

HTML 콘텐츠 삭제화가 구현됩니다. 이렇게 하면 텍스트 편집기에서 생성된 콘텐츠에서 [!DNL Page Builder]개의 예약된 HTML 특성이 제거됩니다.

<u>실제 결과</u>

페이지가 저장되지 않은 상태로 유지되며 로더가 계속 회전합니다. 콘솔에서 다음 오류가 생성됩니다.

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
