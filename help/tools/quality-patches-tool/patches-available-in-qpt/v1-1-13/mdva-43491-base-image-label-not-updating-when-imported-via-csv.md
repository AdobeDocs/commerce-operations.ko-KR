---
title: 'MDVA-43491: CSV를 통해 가져올 때 기본 이미지 레이블이 업데이트되지 않음'
description: MDVA-43491 패치는 다중 스토어 웹 사이트용 CSV 파일을 통해 가져올 때 'base_image_label'이 업데이트되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43491입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Data Import/Export
role: Admin
exl-id: f6a5f641-aaf0-4b6e-afa9-7f436f8f59e6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-43491: CSV를 통해 가져올 때 기본 이미지 레이블이 업데이트되지 않음

MDVA-43491 패치는 다중 스토어 웹 사이트용 CSV 파일을 통해 가져올 때 `base_image_label`이(가) 업데이트되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43491입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.5 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다중 스토어 웹 사이트용 CSV 파일을 사용하여 가져올 때 `base_image_label`이(가) 업데이트되지 않습니다.

<u>필수 구성 요소</u>:

하나 이상의 기존 기본이 아닌 웹 사이트, 스토어 및 스토어 조회수.

<u>재현 단계</u>:

1. 새 제품을 만듭니다.

   * 이미지를 업로드합니다.
   * 제품을 새로 만든 웹 사이트에 할당합니다.

1. 제품을 CSV로 내보냅니다.
1. CSV 파일의 기본 행을 복제하여 각 스토어 보기에 대한 `base_image_label`을(를) 업데이트합니다.
1. CSV 파일을 가져옵니다. 각 스토어에 대한 레이블을 올바르게 업데이트하며, 이 레이블은 제품 편집 페이지의 **이미지 및 비디오** 탭에서 확인할 수 있습니다.
1. CSV 파일을 다시 내보내고 `base_image_label` 열을 다른 값으로 업데이트하십시오.
1. CSV 파일을 다시 가져옵니다.
1. 관리자에서 제품을 열고 각 스토어 보기에 대해 레이블이 업데이트되었는지 확인합니다.

<u>예상 결과</u>:

대체 텍스트(이미지 레이블)가 CSV 파일에 따라 저장소별 값으로 업데이트됩니다.

<u>실제 결과</u>:

대체 텍스트(이미지 레이블)가 CSV 파일의 `base_image_label` 값으로 업데이트되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
