---
title: 'MDVA-42046: 제품 특성에 잘못된 값이 할당됨'
description: MDVA-42046 패치는 날짜 입력 필드가 있는 제품을 업데이트하는 동안 제품 특성에 잘못된 값이 지정되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42046입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Attributes, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-42046: 제품 특성에 잘못된 값이 할당되었습니다.

MDVA-42046 패치는 날짜 입력 필드가 있는 제품을 업데이트하는 동안 제품 특성에 잘못된 값이 지정되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-42046입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.4 - 2.3.5-p2 및 2.4.0 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품을 `news_from_date` 및/또는 `news_to_date` 필드와 함께 저장한 후 해당 필드의 값이 기본값으로 재설정됩니다.

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다.
1. 1단계에서 만든 제품을 내보냅니다.
1. 내보낸 CSV 파일에서 `news_from_date` 및 `news_to_date` 필드에 일부 값을 입력합니다. 예: 2021-05-15 및 2021-06-18.
1. 수정된 CSV 파일을 사용하여 제품을 가져옵니다.
1. 제품 그리드에 &quot;Set Product as New from Date&quot; 및 &quot;Set Product as New to Date&quot; 열을 추가합니다.
1. 제품에 대한 편집 페이지를 열고 변경 내용 없이 **저장**&#x200B;을 클릭하세요.
1. 제품 그리드로 돌아가서 제품에 대한 데이터를 확인합니다.

<u>예상 결과</u>:

&quot;새 제품 시작 날짜로 설정&quot;과 &quot;새 제품 시작 날짜로 설정&quot;은 모두 저장 전과 동일합니다.

<u>실제 결과</u>:

* &quot;제품을 새로운 시작 날짜로 설정&quot; 및 &quot;제품을 새로운 종료 날짜로 설정&quot; 열의 값이 변경됩니다.

* 새 제품 시작 날짜로 설정 열에는 현재 날짜가 표시되고 새 제품 시작 날짜로 설정 열에는 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
