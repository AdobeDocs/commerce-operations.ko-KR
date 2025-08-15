---
title: 'ACSD-55339: Adobe Commerce에 대한 협상 가능한 견적의 SKU 트리밍 문제 해결'
description: ACSD-55339 패치를 적용하여 앞에 영(0)이 있는 제품 SKU가 트리밍되어 협상 오류가 발생하는 Adobe Commerce 문제를 수정합니다.
feature: B2B, Quotes
role: Admin, Developer
exl-id: 7a9f92df-fb3e-4723-b731-155c6c4fc431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-55339: Adobe Commerce에 대한 협상 가능한 견적의 SKU 트리밍 문제 해결

ACSD-55339 패치는 선행 0이 있는 제품 SKU가 트리밍되어 협상 프로세스 중에 오류가 발생하는 문제를 수정합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.56이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-55339입니다. 이 문제는 Adobe Commerce B2B 1.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

앞에 0이 있는 숫자 제품 SKU는 협상 가능한 견적에 사용될 때 잘려서 수량을 업데이트하거나 가격을 설정하지 못하게 하는 오류가 발생합니다.

<u>재현 단계</u>:

1. 관리 패널의 제품 만들기 섹션으로 이동합니다.
1. 제품에 대한 [!UICONTROL SKU]을(를) 01910 설정합니다.
1. Storefront에 로그인하고 다음 작업을 수행합니다.
   1. 장바구니에 제품을 추가합니다.
   1. 장바구니를 보고 편집합니다.
   1. 견적을 요청합니다.
1. [!UICONTROL admin] > [!UICONTROL Quote] > [!UICONTROL View] 및 [!UICONTROL Add Products by SKU]&#x200B;(으)로 01910.

**참고:** SKU는 *01910* 대신 *1910*(으)로 표시됩니다. 이 불일치로 인해 카탈로그에 SKU 1910의 제품이 없으므로 사용자가 수량이나 가격을 업데이트할 수 없습니다.

<u>예상 결과</u>:

협상 가능 견적을 오류 없이 성공적으로 업데이트해야 합니다.

<u>실제 결과</u>:

제품이 존재하지 않음을 나타내는 경고 메시지가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
