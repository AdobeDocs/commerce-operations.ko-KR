---
title: 'ACSD-62758: 구성 가능한 제품 페이지에서 비디오 렌더링 문제가 해결되었습니다.'
description: URL에 사전 선택된 견본 옵션이 포함되어 있을 때 구성 가능한 제품 세부 사항 페이지의 제품 비디오가 올바르게 렌더링되지 않는 Adobe Commerce 문제를 해결하려면 ACSD-62758 패치를 적용합니다.
feature: Catalog Management
role: Admin, Developer
exl-id: 084b497d-4471-4458-bc1d-2a452bfe2662
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-62758: 구성 가능한 제품 페이지에서 비디오 렌더링 문제가 해결되었습니다.

ACSD-62758 패치는 URL에 사전 선택된 견본 옵션이 포함되어 있을 때 구성 가능한 제품 세부 사항 페이지의 제품 비디오가 올바르게 렌더링되지 않는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62758입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

URL에 사전 선택된 견본 옵션이 포함되어 있는 경우 구성 가능한 제품 세부 사항 페이지에서 제품 비디오가 올바르게 렌더링되지 않아 비디오 대신 정적 이미지가 표시됩니다.

<u>재현 단계</u>:

1. [!UICONTROL Stores] > [!UICONTROL Attributes] > [!UICONTROL Product] (으)로 이동합니다.
1. **[!UICONTROL Color]** 특성을 선택하고 편집하십시오.
1. 다음 설정을 업데이트합니다.
   1. [!UICONTROL Catalog Input Type for Store Owner]을(를) [!UICONTROL Visual Swatch] (으)로 설정합니다.
   1. **[!UICONTROL Update Product Preview Image]**&#x200B;을(를) **[!UICONTROL Yes]**(으)로 설정합니다.
1. 이 속성에 대한 몇 가지 옵션을 만듭니다.
1. **[!UICONTROL Color]** 특성을 사용하여 새 범주를 만들고 구성 가능한 새 제품을 추가합니다.
1. 단일 임의 이미지를 상위 제품에 추가합니다.
1. 새로 만든 구성 가능한 하위 제품을 편집하고 해당 미디어 갤러리에 비디오를 추가합니다.
   1. **[!UICONTROL Add Video]**&#x200B;을(를) 클릭하고 테스트 비디오 URL: https://vimeo.com/12860646을 사용합니다.
1. 제품을 저장하고 캐시를 지운 다음 스토어를 다시 인덱싱합니다.
1. 상점에서 새로 만든 제품을 열고 견본 옵션 중 하나를 선택한 다음 플레이어 버튼이 표시된 상태에서 비디오가 올바르게 로드되는지 확인합니다.
1. 비디오가 예상대로 로드되고 플레이어 버튼이 표시됩니다.
1. 이제 견본 옵션 중 하나를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Inspect]**&#x200B;을(를) 선택한 다음 특성 ID와 옵션 ID를 찾습니다. 제품 URL을 복사하고 끝에 `www.product-url.com/producit-test#attribute_id=option_id`을(를) 추가합니다. 견본 옵션을 미리 선택합니다. 새 창에서 업데이트된 URL을 엽니다.

<u>예상 결과</u>:

견본 옵션을 수동으로 선택하는 경우와 마찬가지로 비디오가 올바르게 로드되어야 합니다.

<u>실제 결과</u>:

비디오 대신 정적 이미지가 표시됩니다. 비디오 초기화 실패를 나타내는 콘솔 오류가 기록됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).

