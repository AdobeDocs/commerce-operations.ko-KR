---
title: 'ACSD-59865: 제품 수량이 부족하여 [!UICONTROL Cart Price Rule]이(가) 이전 규칙을 취소하지 못했습니다.'
description: ACSD-59865 패치를 적용하여 *고정 금액 할인,* *제품 가격 할인의 퍼센트* 및 *구매 X가 Y*를 얻는 경우* [!UICONTROL Cart Price Rules]에 해당하는 *할인 수량 단계* 값이 더 이상 이전 규칙의 작업을 취소하지 않는 Adobe Commerce 문제를 해결합니다.
feature: Price Rules
role: Admin, Developer
exl-id: 5838a740-018d-44c2-8135-54426ea08627
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865: 제품 수량이 부족하여 [!UICONTROL Cart Price Rule]이(가) 이전 규칙을 취소하지 못했습니다.

ACSD-59865 패치는 *[!UICONTROL Discount quantity step]*,*[!UICONTROL Fixed amount discount]*,*[!UICONTROL Percent of product price discount]및* *[!UICONTROL Buy X get Y]*&#x200B;의 [!UICONTROL Cart Price Rules] 값이 더 이상 이전 규칙의 작업을 취소하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-59865입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니에 제품 수량이 부족하여 [!UICONTROL Cart Price Rule]이(가) 이전에 적용한 규칙을 취소하지 못했습니다.

<u>재현 단계</u>:

1. 관리자로 로그인합니다.
1. **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**(으)로 이동한 다음 **[!UICONTROL Add New rule]**&#x200B;을(를) 클릭합니다.
   * **[!UICONTROL Rule Name]** = *테스트 - 1* 설정
   * *웹 사이트* 및 *고객 그룹* 모두 선택
   * **[!UICONTROL Priority]** = *0* 설정
   * **[!UICONTROL Actions]** 섹션으로 이동:
      * **[!UICONTROL Apply]** = *제품 가격 할인의 비율* 설정
      * **[!UICONTROL Discount amount]** = *10* 설정
      * **[!UICONTROL Maximum Qty Discount is Applied To]** = *100* 설정
      * **[!UICONTROL Discount Qty Step (Buy X)]** = *0* 설정
      * **[!UICONTROL Discard subsequent rules]**&#x200B;을(를) *아니요*(으)로 설정
1. 캐시를 지웁니다.
1. 상점으로 이동하여 장바구니에 항목 하나를 추가한 다음 *체크아웃/장바구니*&#x200B;로 진행합니다.
1. 장바구니에 *10%* 할인이 적용되었는지 확인하십시오.
1. **[!UICONTROL Cart Price Rules]**(으)로 돌아가서 새 규칙을 만듭니다.
   * **[!UICONTROL Rule Name]** = *테스트 - 2* 설정
   * **[!UICONTROL Websites]** 및 **[!UICONTROL Customer Groups]** 모두 선택
   * **[!UICONTROL Priority]** = *2* 설정
   * **[!UICONTROL Actions]** 섹션으로 이동합니다.
      * **[!UICONTROL Apply]** = *제품 가격 할인의 비율* 설정
      * **[!UICONTROL Discount amount]** = *20* 설정
      * **[!UICONTROL Maximum Qty Discount is Applied To]** = *100* 설정
      * **[!UICONTROL Discount Qty Step (Buy X)]** = *3* 설정
1. 캐시를 지웁니다.
1. 다시 상점가로 가보세요
1. 장바구니를 업데이트하여 규칙을 새로 고칩니다. *10%* 할인이 더 이상 적용되지 않는지 확인하십시오.
1. 수량이 두 번째 규칙에 필요한 *단계* 값을 만족할 때까지 장바구니에 항목을 추가하십시오.

<u>예상 결과</u>:

두 번째 규칙의 조건이 충족될 때 첫 번째 [!UICONTROL Cart Price Rule]이(가) 적용됩니다.

<u>실제 결과</u>:

가격 규칙은 관리자 대시보드에 구성된 대로 적용됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
