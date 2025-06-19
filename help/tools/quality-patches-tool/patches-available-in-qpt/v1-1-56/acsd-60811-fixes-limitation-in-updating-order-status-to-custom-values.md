---
title: 'ACSD-60811: 주문 상태를 사용자 지정 값으로 업데이트하는 제한 사항 수정'
description: ACSD-60811 패치를 적용하여 현재 상태가 '처리 중' 또는 '사기'인 경우에만 사용자 지정 값 또는 댓글로 주문 상태를 업데이트할 수 있는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-60811: 주문 상태를 사용자 지정 값으로 업데이트하는 제한 사항 수정

ACSD-60811 패치는 현재 상태가 &#39;[!UICONTROL Processing]&#39; 또는 &#39;[!UICONTROL Suspected Fraud]&#39;인 경우에만 사용자 지정 값 또는 댓글로 순서 상태를 업데이트할 수 있는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-60811입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 메서드) 2.4.7. 2.4.7-p1, 2.4.7-p2, 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

현재 상태가 *처리 중* 또는 *사기*&#x200B;인 경우에만 사용자 지정 값 또는 댓글로 주문 상태를 업데이트할 수 있습니다. 새 상태를 선택하고 제출하면 주문 상태는 변경되지 않습니다.

<u>재현 단계</u>:

1. 관리 패널에서 사용자 지정 순서 상태를 만들려면 **[!UICONTROL Stores]** > **[!UICONTROL Order Status]**(으)로 이동합니다.
1. 주문 상태에 사용자 지정 상태를 할당하려면 **[!UICONTROL Assign Status to State]**&#x200B;을(를) 클릭하십시오.
1. 관리 패널의 주문 보기 페이지에서 주문 상태를 변경합니다.

<u>예상 결과</u>:

관리자는 관리 패널에서 주문 상태를 사용자 정의 주문 상태로 변경할 수 있어야 합니다.

<u>실제 결과</u>:

주문 상태는 새 주문 상태를 선택하고 제출할 때 동일하게 유지됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
