---
title: 'ACSD-62971: 숫자가 아닌 수량 값을 가진 재고 출처 임포트는 수량을 0으로 설정합니다.'
description: ACSD-62971 패치를 적용하여 '수량' 열에 숫자가 아닌 값이 있는 재고 소스를 가져오면 수량이 0으로 설정되는 Adobe Commerce 문제를 해결합니다.
feature: Data Import/Export, Inventory
role: Admin, Developer
exl-id: ece23153-4932-4ac5-b46e-49327a8e84a1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-62971: 숫자가 아닌 수량 값을 가진 재고 출처 임포트는 수량을 0으로 설정합니다.

ACSD-62971 패치는 &#39;quantity&#39; 열에 숫자가 아닌 값이 있는 재고 소스를 가져오면 수량이 0으로 설정되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62971입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Quantity]** 열에 숫자가 아닌 값이 있는 재고 소스를 가져오면 수량이 0으로 설정되는 문제를 해결했습니다.

<u>재현 단계</u>:

1. 수량=100인 **[!UICONTROL Simple Product]** 만들기
1. 수량이 잘못된 파일(&quot;abc&quot;)을 사용하여 **[!UICONTROL Stock Sources]** 가져오기 수행

   ```table
   source_code    sku    status    quantity
     default     simple    1         abc
   ```

1. 가져오기 후 수량을 확인합니다.

<u>예상 결과</u>:
데이터 가져오기 유효성 검사에 실패합니다.

<u>실제 결과</u>:
단순 제품의 수량이 0이 되었으며 제품이 [!UICONTROL Out of Stock]&#x200B;(으)로 업데이트되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
