---
title: 'ACSD-63326: 백엔드에서 주문을 한 후 관리자 리디렉션 문제를 수정합니다'
description: ACSD-63326 패치를 적용하여 관리자가 백엔드에서 주문한 후 손상된 페이지로 리디렉션되는 Adobe Commerce 문제를 수정합니다.
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 8fffc3ad-11a4-4e62-b747-1c4c7b493ada
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63326: 백엔드에서 주문을 한 후 관리자 리디렉션 문제를 수정합니다

ACSD-63326 패치는 백엔드에서 명령을 수행한 후 관리자가 손상된 페이지로 리디렉션되는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63326입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자는 백엔드에서 고객에 대한 주문을 성공적으로 수행한 후 손상된 레이아웃이 있는 페이지로 리디렉션됩니다.

<u>재현 단계</u>:

1. 관리 패널의 **[!UICONTROL Customers]** 섹션으로 이동합니다.
1. 고객을 선택하고 **[!UICONTROL Edit]**&#x200B;을(를) 클릭합니다.
1. 고객 세부 정보 페이지의 상단 메뉴에서 **[!UICONTROL Create Order]**&#x200B;을(를) 클릭합니다.
1. [!UICONTROL FR French] 스토어를 선택하고 사용 가능한 제품을 주문에 추가하십시오.
1. 체크 아웃 시 필요한 세부 정보를 입력하고 **[!UICONTROL Get shipping methods and rates]**&#x200B;을(를) 클릭합니다.
1. 주문하려면 **[주문 제출]**&#x200B;을 클릭하세요.

<u>예상 결과</u>:

관리자가 올바른 레이아웃으로 주문 확인 또는 감사 페이지로 리디렉션됩니다.

<u>실제 결과</u>:

관리자가 레이아웃이 끊어진 페이지로 리디렉션됩니다. 페이지를 새로 고친 후에만 레이아웃이 수정됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
