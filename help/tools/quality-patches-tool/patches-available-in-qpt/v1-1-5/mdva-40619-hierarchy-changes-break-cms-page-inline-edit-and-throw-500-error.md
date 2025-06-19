---
title: 'MDVA-40619: 계층 구조 변경으로 CMS 페이지 인라인 편집이 중단되고 500 오류가 발생합니다.'
description: MDVA-40619 패치는 CMS 페이지 계층 구조가 변경되어 CMS 페이지 인라인 편집이 중단되고 "500 오류"가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40619입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
feature: CMS
role: Admin
exl-id: 148cb0a5-5a6c-4cfa-bf95-4bafc57beec6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40619: 계층 구조 변경으로 CMS 페이지 인라인 편집이 중단되고 500 오류가 발생합니다.

MDVA-40619 패치는 CMS 페이지 계층 구조가 변경되어 CMS 페이지 인라인 편집이 중단되고 &quot;500 오류&quot;가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40619입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

CMS 페이지 계층 구조 변경 사항이 CMS 페이지 인라인 편집을 중단하고 &quot;500 오류&quot;를 발생시킵니다.

<u>재현 단계</u>:

1. 관리 패널 > **컨텐츠** > **계층 구조**(으)로 이동합니다.
1. &quot;기본 스토어 보기&quot;를 선택합니다.
1. &quot;상위 노드 계층 사용&quot;을 선택 취소합니다.
1. 수동으로 페이지를 선택하고 **저장**&#x200B;을 클릭하세요.
1. 그런 다음 **컨텐츠** > **페이지**(으)로 이동합니다.
1. 그리드에서 CMS 페이지를 편집해 보십시오.
1. **저장**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

페이지가 저장되었습니다.

<u>실제 결과</u>:

다음 오류가 발생합니다.

*서버에 기술적인 문제가 있어 오류가 발생했습니다. 계속하기 위해 다시 시도하십시오. 문제가 지속되면 나중에 다시 시도하십시오.*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
