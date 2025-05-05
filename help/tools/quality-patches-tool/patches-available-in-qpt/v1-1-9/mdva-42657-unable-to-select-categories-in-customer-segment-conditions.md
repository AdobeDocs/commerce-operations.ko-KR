---
title: 'MDVA-42657: 고객 세그먼트 조건에서 범주를 선택할 수 없음'
description: MDVA-42657 패치는 관리자 사용자가 고객 세그먼트 조건에서 범주를 선택할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42657입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Categories, Console, Customer Service
role: Admin
exl-id: 115bad99-a603-4940-897e-034974ed1a6c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-42657: 고객 세그먼트 조건에서 범주를 선택할 수 없음

MDVA-42657 패치는 관리자 사용자가 고객 세그먼트 조건에서 범주를 선택할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-42657입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자 사용자가 고객 세그먼트 조건에서 범주를 선택할 수 없습니다.

<u>재현 단계</u>:

1. **고객** > **세그먼트**(으)로 이동합니다.
1. 새 세그먼트를 만듭니다.
1. 새로 만든 세그먼트로 이동하여 왼쪽 탐색에서 **조건**&#x200B;을 클릭하세요.
1. 녹색 더하기 기호를 클릭합니다.
1. Products에서 Product History 를 선택합니다.
1. &quot;확인함&quot;을 &quot;정렬됨&quot;으로 변경합니다.
1. &quot;모두&quot;를 &quot;모두&quot;로 변경합니다.
1. 중첩된 녹색 더하기 기호를 클릭하고 범주 를 선택합니다.
1. **..** 기호를 클릭한 다음 선택 아이콘(확인 표시 왼쪽의)을 클릭합니다.
1. 브라우저 개발 콘솔을 엽니다.
1. 모든/여러 카테고리에 대한 확인란을 선택하고 콘솔에 throw된 Javascript 오류를 확인합니다.
1. **저장** 단추를 클릭합니다.
1. 조건으로 다시 이동하고 선택한 범주가 저장되었는지 확인합니다.

<u>예상 결과</u>:

세그먼트 조건을 보거나 편집할 때 선택한 카테고리가 저장되고 선택됩니다.

<u>실제 결과</u>:

선택한 범주가 누락되어 제대로 저장되지 않았습니다. 콘솔에 다음 오류가 발생합니다.

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
