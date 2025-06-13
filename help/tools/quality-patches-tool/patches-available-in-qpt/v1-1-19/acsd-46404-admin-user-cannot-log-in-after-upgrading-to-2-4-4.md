---
title: 'ACSD-46404: 2.4.4로 업그레이드한 후 관리자가 로그인할 수 없음'
description: ACSD-46404 패치는 2.4.4로 업그레이드한 후 관리자가 로그인할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19가 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-46404입니다. 이 문제는 Adobe Commerce 2.4.5에서 해결되었습니다.
feature: Admin Workspace
role: Admin
exl-id: f475ca56-5e06-4d4d-be42-f760c95968cf
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-46404: 2.4.4로 업그레이드한 후 관리자가 로그인할 수 없음

ACSD-46404 패치는 2.4.4로 업그레이드한 후 관리자가 로그인할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-46404입니다. 이 문제는 Adobe Commerce 2.4.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자가 2.4.4로 업그레이드한 후 로그인할 수 없습니다.

<u>재현 단계</u>:

1. 관리 패널에 로그인
1. 저장소 > **설정** > **구성** > **고급** > **시스템** > **보안**&#x200B;으로 이동합니다.
1. 관리자의 최대 세션 크기를 **0**(으)로 설정하고 저장합니다.

<u>예상 결과</u>:

관리자 사용자가 성공적으로 로그인할 수 있습니다.

<u>실제 결과</u>:

관리자 사용자가 로그아웃되어 로그인할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
