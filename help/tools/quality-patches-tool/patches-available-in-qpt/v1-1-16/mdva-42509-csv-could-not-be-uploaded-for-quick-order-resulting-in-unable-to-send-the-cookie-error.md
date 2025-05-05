---
title: 'MDVA-42509: 빠른 주문을 위해 CSV를 업로드할 수 없어 ''쿠키를 보낼 수 없음'' 오류가 발생했습니다.'
description: MDVA-42509 패치는 빠른 주문을 위해 CSV를 업로드할 수 없어 *쿠키를 보낼 수 없음* 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42509입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: B2B, Orders
role: Admin
exl-id: 6319931b-9cf1-4004-b302-737863c53ff8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-42509: 빠른 주문을 위해 CSV를 업로드할 수 없어 &#39;쿠키를 보낼 수 없음&#39; 오류가 발생했습니다.

MDVA-42509 패치는 빠른 주문을 위해 CSV를 업로드할 수 없어 *쿠키를 보낼 수 없음* 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-42509입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.3 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

CSV를 사용하여 제품 수가 많은 빠른 주문을 만들면 쿠키 오류가 표시됩니다. *쿠키를 보낼 수 없습니다*

<u>재현 단계</u>:

1. **스토어** > **설정** > **구성** > **일반** > **B2B 기능**&#x200B;으로 이동하여 빠른 순서를 사용하도록 설정합니다.
1. 고객 계정을 만들고 맨 위의 **빠른 주문**(으)로 이동합니다.
1. 100개 이상의 SKU가 있는 CSV를 사용하여 빠른 주문을 만들어 보십시오.

<u>예상 결과</u>:

많은 SKU를 사용하여 빠른 주문을 만들 수 있습니다.

<u>실제 결과</u>:

쿠키 크기와 관련된 오류 메시지가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
