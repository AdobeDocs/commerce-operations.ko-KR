---
title: 'MDVA-39993: API를 통해 수행된 인벤토리 변경은 상점 앞에 반영되지 않습니다.'
description: MDVA-39993 패치는 API를 통해 수행된 인벤토리 변경이 상점 앞에 반영되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39993입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: REST, Inventory, Orders, Storefront
role: Admin
exl-id: 5fa13635-bd58-470b-a4d5-e50cda8a46e3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-39993: API를 통해 수행된 인벤토리 변경은 상점 앞에 반영되지 않습니다.

MDVA-39993 패치는 API를 통해 수행된 인벤토리 변경이 상점 앞에 반영되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39993입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.5 - 2.3.7-p2 및 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

API를 통해 수행된 인벤토리 변경 사항은 상점 제품 페이지에 반영되지 않습니다.

<u>필수 구성 요소</u>:

인벤토리 모듈이 설치되었습니다.

<u>재현 단계</u>:

1. 큐가 cron을 사용하여 실행되도록 설정되어 있고 cron이 설치되어 실행 중인지 확인합니다.
1. 두 가지 색상(검정과 빨간색) 및 두 가지 크기(M과 L)를 사용하여 구성 가능한 제품(COC001)을 만듭니다.
1. 한 가지 옵션을 품에서 만듭니다(COC001-Red-M).
1. 상점 첫 화면에서 구성 가능한 제품 페이지를 로드하고 각 색상을 클릭하여 보십시오. **빨강**&#x200B;을(를) 클릭하면 크기 **M**&#x200B;이(가) 품절되었으므로 제외해야 합니다.
1. 다음 API 끝점 및 페이로드를 사용하여 COC001-Red-M을 재고로 만듭니다.

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. 백엔드에서 이 간단한 제품을 확인하고 제품이 In Stock으로 업데이트되었는지 확인합니다.
1. 프론트엔드에서 구성 가능한 제품을 로드하고 각 색상을 클릭합니다. **빨강**&#x200B;을(를) 클릭하면 크기가 **M**&#x200B;입니다.

<u>예상 결과</u>:

COC001-Red-M 옵션은 API를 통해 In Stock으로 업데이트했기 때문에 제외되지 않습니다.

<u>실제 결과</u>:

COC001-Red-M 옵션은 재고가 있음에도 불구하고 여전히 누락되어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서 &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
