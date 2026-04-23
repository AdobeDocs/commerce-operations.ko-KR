---
title: 'ACSD-64111:  [!DNL Page Builder]에서 제품 구성 요소에 대한 중첩 조건을 설정할 때 *InvalidArgumentException: 클래스가 없음* 오류를 수정합니다'
feature: Products, Page Builder
role: Admin, Developer
exl-id: dc39c65b-fb78-4105-b0e8-92a78b49adaf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-64111: [!DNL Page Builder]에서 제품 구성 요소에 대한 중첩 조건을 설정할 때 *InvalidArgumentException: 클래스가 존재하지 않습니다* 오류가 수정되었습니다.

ACSD-64111 패치가 [!DNL Page Builder]에서 제품 구성 요소에 대한 중첩 조건을 설정할 때 `vendor/magento/module-rule/Model/ConditionFactory.php:50`에서 *InvalidArgumentException: 클래스가 존재하지 않습니다* 오류가 발생하는 문제를 해결했습니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-64111입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 메서드)  2.4.6-p8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

오류 *InvalidArgumentException: 클래스가 /app/&lt;project id\>/vendor/magento/module-rule/Model/ConditionFactory.php*&#x200B;에 존재하지 않습니다. [!DNL Page Builder] 제품 위젯 조건에 *[!UICONTROL Conditions Combination]*&#x200B;을(를) 추가할 때 throw됩니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자에 로그인합니다.
1. **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**(으)로 이동합니다.
1. 새 페이지를 추가(또는 기존 페이지 편집)합니다.
1. **[!UICONTROL Content]** 섹션을 확장하고 **[!UICONTROL Edit with Page Builder]**&#x200B;을(를) 클릭합니다.
1. 새 행을 추가한 다음 **[!UICONTROL Products]** 위젯을 추가합니다.
1. **[!UICONTROL Products]** 위젯을 구성합니다.
1. **[!UICONTROL Select Products By]**&#x200B;에서 **[!UICONTROL Condition]**&#x200B;을(를) 선택합니다.
1. 새 조건을 추가하고 드롭다운에서 **[!UICONTROL Conditions Combination]**&#x200B;을(를) 선택합니다.

<u>예상 결과</u>:

로그에 오류가 없습니다.

<u>실제 결과</u>:

아래 예외는 로그에 기록됩니다.

*report.CRITICAL: InvalidArgumentException: vendor/magento/module-rule/Model/ConditionFactory.php:50*&#x200B;에 클래스가 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
