---
title: 'ACSD-59366: 팀 목록에 표시되지 않는 비활성화된 사용자가 있는 팀 삭제'
description: ACSD-59366 패치를 적용하여 팀 목록에 표시되지 않는 비활성화된 사용자가 포함된 팀을 삭제하려고 할 때 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, Companies
role: Admin, Developer
exl-id: 406d2242-38f9-4852-b311-0ee57c4a7c26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-59366: 팀 목록에 표시되지 않는 비활성화된 사용자가 있는 팀 삭제

ACSD-59366 패치는 팀 목록에 표시되지 않는 비활성화된 사용자가 포함된 팀을 삭제하려고 할 때 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-59366입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

팀 목록에 표시되지 않는 비활성화된 사용자가 포함된 팀을 삭제할 때 오류가 발생합니다.

<u>필수 구성 요소</u>:

Adobe Commerce B2B 모듈이 설치되고 회사가 활성화됩니다.

<u>재현 단계</u>:

1. 회사 사용자를 만들고 로그인합니다.
1. 회사 구조에서 새 팀을 만듭니다.
1. 새 팀 아래에서 새 사용자를 만듭니다.
1. 새 사용자를 편집하고 비활성화합니다.
1. 팀을 선택하고 삭제합니다.

<u>예상 결과</u>:

팀에는 비활성 사용자가 한 명 이상 있습니다. 팀을 삭제하면 이 사용자의 할당이 취소됩니다. [!UICONTROL Company Users] 섹션에서 비활성 사용자를 찾을 수 있습니다.

<u>실제 결과</u>:

비활성화된 사용자가 있는 팀을 삭제하려고 하면 오류가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
