---
title: 'ACSD-64149: [!UICONTROL Date range] 상태의 고객 세그먼트는 한 날짜만 편집할 때 저장할 수 있습니다.'
description: 날짜 중 하나만 편집할 때 **[!UICONTROL Date range]** 조건을 가진 고객 세그먼트를 저장할 수 있는 Adobe Commerce 문제를 해결하려면 ACSD-64149 패치를 적용하십시오.
feature: Customers, Admin Workspace
role: Admin, Developer
source-git-commit: c1c5256aee44ce65e9339cf3985e53f710fc7c8a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# ACSD-64149: [!UICONTROL Date range] 상태의 고객 세그먼트는 한 날짜만 편집할 때 저장할 수 있습니다.

ACSD-64149 패치는 날짜 중 하나만 편집할 때 날짜 범위 조건이 있는 고객 세그먼트를 저장할 수 있는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-64149입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

날짜 범위에서 지정한 장바구니 내 제품에 대한 조건으로 기존 고객 세그먼트를 편집할 때 소비자 `matchCustomerSegmentProcessor`이(가) SQL 오류로 실패합니다.

<u>재현 단계</u>:

1. 소비자 `matchCustomerSegmentProcessor`이(가) 실행 중인지 확인합니다.

   ```bash
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. **[!UICONTROL Magento backend]**(으)로 이동합니다.
1. **[!UICONTROL Customers]** > **[!UICONTROL Segments]**(으)로 이동합니다.
1. **[!UICONTROL Add Segment]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Segment Name]**&#x200B;을(를) 입력하고 **[!UICONTROL Assigned to Website]**&#x200B;에서 웹 사이트를 선택한 다음 **[!UICONTROL Status]**&#x200B;이(가) *활성*(으)로 설정되어 있는지 확인하십시오.
1. **[!UICONTROL Save and Continue Edit]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Conditions]** 탭으로 이동하여 새 조건: *제품{} > {}제품 목록*{*}*&#x200B;을(를) 추가합니다.
1. **[!UICONTROL Date range]**&#x200B;에 대한 하위 조건을 추가하고 올바른 **[!UICONTROL Date range]**&#x200B;을(를) 설정합니다.
1. **[!UICONTROL Date range]** 옆에 있는 녹색 확인 단추를 클릭합니다.
1. **[!UICONTROL Date range]**&#x200B;을(를) 다시 클릭하고 날짜 선택기를 선택한 다음 날짜 값 중 하나를 편집하고 녹색 단추를 클릭하여 확인합니다.

<u>예상 결과</u>:

**[!UICONTROL Date range]** 선택기는 편집할 때 날짜에 시간을 추가하지 않아야 합니다.

<u>실제 결과</u>:

* **[!UICONTROL Date range]** 선택기가 날짜에 시간을 추가합니다.
   * 한 날짜에는 날짜만 있고 다른 날짜에는 날짜와 시간이 모두 지정되어 있습니다.
* 다음 오류가 로그에 나타납니다.

  ```
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 업그레이드 및 패치 > 패치 적용.

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
