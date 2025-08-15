---
title: 'MDVA-38799: 스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않음'
description: MDVA-38799 패치는 스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38799입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.
feature: Products, Staging
role: Admin
exl-id: 0ae665a8-cda2-4340-91e7-5b9b969a6607
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-38799: 스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않음

MDVA-38799 패치는 스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-38799입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0-2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않습니다. 사용자에게 다음과 같은 오류 메시지가 표시됩니다. *다운로드 가능한 샘플은 제품과 관련이 없습니다. 링크를 확인하고*&#x200B;을(를) 다시 시도하십시오.

<u>재현 단계</u>:

1. **카탈로그** > **제품**(으)로 이동합니다.
1. 제품 추가 옆에 있는 드롭다운을 클릭하고 다운로드 가능한 제품을 선택합니다.
   * 제품의 이름, SKU, 가격 및 수량을 입력합니다.
1. 다운로드 가능한 정보 페이지로 스크롤합니다.
1. 샘플에서 **링크 추가**&#x200B;를 클릭합니다.
   * 제목, 파일 업로드 를 채웁니다(파일 유형은 중요하지 않음).
1. **저장**&#x200B;을 클릭합니다. 다음 메시지가 표시됩니다. *제품을 저장했습니다*.
1. 페이지 맨 위에서 **새 업데이트 예약**&#x200B;을 클릭합니다.
   * 업데이트 이름과 법적 시작 날짜 및 종료 날짜를 입력합니다.
1. 스테이징 업데이트에서 **저장**&#x200B;을 클릭합니다.
1. 제품에서 **저장**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

제품이 오류 없이 저장됩니다.

<u>실제 결과</u>:

다음 오류 메시지가 나타납니다. *다운로드 가능한 샘플은 제품과 관련이 없습니다. 링크를 확인하고*&#x200B;을(를) 다시 시도하십시오.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서 ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
