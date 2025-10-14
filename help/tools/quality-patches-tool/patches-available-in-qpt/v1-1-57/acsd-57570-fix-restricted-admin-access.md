---
title: 'ACSD-57570: 공유 카탈로그에 대한 제한된 관리자 액세스 수정'
description: ACSD-57570 패치를 적용하여 특정 스토어에 대한 액세스 권한이 있는 제한된 관리자가 제품에 할당된 모든 공유 카탈로그를 일관되게 보거나 고객 정보를 저장할 수 없어 시스템 불일치가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 3eeaf1f1-0338-459f-99ec-53764f3f12db
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# ACSD-57570: 공유 카탈로그에 대한 제한된 관리자 액세스 수정

ACSD-57570 패치는 특정 스토어에 대한 액세스 권한이 있는 제한된 관리자가 제품에 할당된 모든 공유 카탈로그를 일관되게 보거나 고객 정보를 저장할 수 없어 시스템 불일치가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57570입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4-p9

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

특정 스토어에 대한 액세스 권한이 있는 제한된 관리 사용자가 항상 모든 공유 카탈로그를 보거나 고객을 저장할 수 없으므로 일치하지 않습니다. 여러 스토어가 있는 제한된 관리자는 새 회사 또는 사용자 지정 공유 카탈로그를 볼 수 없습니다.

<u>재현 단계</u>:

1. 다음 순서로 스토어를 설정합니다.
   * W2라는 새 웹 사이트를 만듭니다.
   * 기본 웹 사이트에 대한 새 스토어 보기를 만듭니다.
   * 웹 사이트 W2에 대해 W2S2라는 이름의 새 스토어를 만듭니다.
   * 스토어 W2S2에 대해 W2S2SV1이라는 새 스토어 뷰를 만듭니다.
   * W2S2 스토어에 대해 W2S2SV2라는 새 스토어 뷰를 만듭니다.
   * W2용 회사를 만듭니다.
1. 제품 할당:
   * 일부 제품을 W1에만 할당합니다.
   * 일부 제품을 W2에만 할당합니다.
   * 일부 제품을 W1과 W2에 모두 할당합니다.
1. 사용자 지정 공유 카탈로그를 만들고 모든 제품을 이 카탈로그에 할당합니다.
1. **W2**&#x200B;이(가) 아닌 **W2S2**&#x200B;에만 액세스할 수 있는 사용자 지정 관리자 역할을 만드십시오.
1. 제한된 관리자 사용자를 새 사용자 지정 관리자 역할에 할당합니다.
1. 제한된 관리자로 로그인합니다.
1. 액세스 확인:
   * 볼 수 있는 회사를 확인합니다.
   * 볼 수 있는 공유 카탈로그를 확인합니다.
   * 제품 목록을 열고 제품이 지정된 모든 공유 카탈로그를 볼 수 있는지 확인합니다.

<u>예상 결과</u>:

동작은 일관되어야 합니다.

<u>실제 결과</u>:

웹 사이트, 스토어 및 스토어 보기를 한 개만 더 만드는 경우, 제한된 관리자는 제품 목록에서 회사, 공유 카탈로그 및 두 공유 카탈로그를 모두 볼 수 있습니다. 위의 설정으로 제한된 관리자는 새 회사 또는 사용자 지정 공유 카탈로그를 볼 수 없으며 제품 목록에 기본 공유 카탈로그만 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
