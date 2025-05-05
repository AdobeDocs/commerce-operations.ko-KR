---
title: 'ACSD-48212: 제품 가져오기로 인해 제품이 잘못된 소스에 할당됨'
description: ACSD-48212 패치를 적용하여 제품 가져오기로 인해 제품이 잘못된 소스에 할당되는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace, Data Import/Export, Products
role: Admin
exl-id: d573d95b-95fc-4f59-b518-18088855a154
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-48212: 제품 가져오기로 인해 제품이 잘못된 소스에 할당됨

ACSD-48212 패치는 제품 가져오기로 인해 제품이 잘못된 소스에 할당되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48212입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 가져오기로 인해 해당 제품이 잘못된 소스에 할당됩니다.

<u>재현 단계</u>:

1. 보조 인벤토리 소스를 만듭니다.
1. 기본 재고 출처로만 제품을 생성합니다.
1. 제품 내보내기.
1. `bin/magento cron:run` 실행.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**&#x200B;을(를) 엽니다.
1. 그리드에서 제품을 선택합니다.
1. *[!UICONTROL mass action]* 메뉴를 사용하여 재고 할당을 취소합니다.
1. `bin/magento cron:run` 실행.
1. *[!UICONTROL mass action]* 메뉴를 사용하여 보조 원본을 지정하십시오.
1. `bin/magento cron:run` 실행.
1. *[!UICONTROL mass action]* 메뉴를 사용하여 제품을 삭제합니다.
1. `bin/magento cron:run` 실행.
1. 이전에 내보낸 CSV를 사용하여 제품을 가져옵니다.
1. 출처 지정을 확인합니다.

<u>예상 결과</u>:

제품은 기본 소스에만 할당됩니다.

<u>실제 결과</u>:

제품은 기본 및 보조 소스 모두에 할당됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
