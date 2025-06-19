---
title: 'MDVA-41350: 관리자가 액세스 권한 외부에 제품을 추가할 때 예외 발생'
description: MDVA-41350 패치는 관리자 사용자가 액세스 권한 밖에 있는 SKU별로 제품을 추가할 때 제한된 액세스 알림 대신 예외 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-41350입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Admin Workspace, Products
role: Admin
exl-id: 4dc5ee5c-bd93-42e1-9c63-93ffb8e5f21c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-41350: 관리자가 액세스 권한 외부에 제품을 추가할 때 예외 발생

MDVA-41350 패치는 관리자 사용자가 액세스 권한 밖에 있는 SKU별로 제품을 추가할 때 제한된 액세스 알림 대신 예외 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-41350입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

액세스 권한이 제한된 관리자가 액세스 권한 밖에서 SKU로 제품을 추가할 때 사용자에게 액세스 권한을 제한했음을 알리는 메시지 대신 예외가 발생합니다.

<u>재현 단계</u>:

1. 특정 웹 사이트에만 액세스할 수 있는 사용자로 관리자에 로그인합니다.
1. **판매** > **주문**(으)로 이동한 다음 **새 주문 만들기**&#x200B;를 클릭합니다.
1. 고객 및 스토어 뷰를 선택합니다.
1. **SKU별 제품 추가**&#x200B;를 클릭합니다.
1. 웹 사이트에 할당되지 않았거나 액세스 권한이 있는 웹 사이트에 할당되지 않은 SKU를 검색합니다.
1. **주문에 추가**&#x200B;를 클릭합니다.

<u>예상 결과</u>:

적절한 오류 메시지가 표시됩니다.

<u>실제 결과</u>:

예외가 발생했습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
