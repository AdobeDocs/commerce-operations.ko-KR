---
title: 'ACSD-46869: 구성 가능한 제품이 체크아웃 시 REST API를 사용하여 업데이트되지 않음'
description: ACSD-46869 패치는 체크아웃 시 REST API를 사용하여 구성 가능한 제품이 업데이트되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-46869입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
exl-id: f03d4b24-ac95-406e-8e9d-908149b9207c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-46869: 구성 가능한 제품이 체크아웃 시 REST API를 사용하여 업데이트되지 않음

ACSD-46869 패치는 체크아웃 시 구성 가능한 제품이 REST API를 사용하여 업데이트되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-46869입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL QPT] 랜딩 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)에서 호환성을 확인하십시오. 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품은 체크아웃 중에 REST API를 사용하여 업데이트되지 않습니다.

<u>재현 단계</u>:

1. 색상 및 크기 속성을 사용하여 구성 가능한 제품을 만듭니다.
1. **[!UICONTROL Options]**&#x200B;을(를) 선택하고 제품을 장바구니에 추가하십시오.
1. **[!UICONTROL Checkout]**(으)로 이동하여 수량을 제외한 크기를 여러 번 업데이트하고 요청 및 응답을 확인합니다.
1. 크기를 업데이트할 때 다음과 같은 응답을 받게 됩니다.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>예상 결과</u>:

값은 변경 사항에 따라 업데이트됩니다.

<u>실제 결과</u>:

`option_value`이(가) 업데이트되지 않았으므로 주문을 할 때 이전 크기 값을 갖습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: 품질 패치 도구 안내서의 [[!DNL Quality Patches Tools] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
