---
title: 'ACSD-65983: 관리자에서 번들 제품 견적을 다시 구성할 때 오류 발생'
description: 백엔드의 [!UICONTROL Sales] > [!UICONTROL Quotes] > [!UICONTROL Edit] 화면에서 번들 제품을 구성하려고 할 때 오류가 표시되는 Adobe Commerce 문제를 해결하려면 ACSD-65983 패치를 적용합니다.
feature: B2B, Quotes
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a8f2b273bcbcf135677ad7ca289398bf660e02e
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# ACSD-65983: 관리자에서 번들 제품 견적을 다시 구성할 때 오류 발생

ACSD-65983 패치는 관리 백엔드에서 번들 제품 견적을 다시 구성하는 경우 오류가 반환되는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-65983입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리 백엔드에서 번들 제품 견적을 재구성하면 오류가 반환됩니다.

<u>재현 단계</u>:

1. [관리] 패널로 이동하여 **[!UICONTROL B2B Feature]**: **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Feature]**&#x200B;을(를) 활성화합니다.
1. 고정 금액이 있는 번들 제품을 만들고(예: *$10*), *0* 금액이 있는 단순 제품을 세 개 이상 추가하십시오. *옵션 1*&#x200B;의 **2** 및 *옵션 2*&#x200B;의 **기타**.
1. 프론트엔드에서 회사 계정을 만듭니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**(으)로 이동하여 만든 회사와 제품을 새/사용자 지정 공유 카탈로그에 할당합니다.
1. 프론트엔드에 **회사 사용자**(으)로 로그인하고 번들에서 간단한 제품 하나를 장바구니에 추가합니다.
1. 장바구니 페이지를 열고 **견적 요청**(으)로 제출합니다.
1. 백엔드로 이동하여 생성된 견적을 편집합니다.
1. **견적 항목** 섹션에서 **구성** 단추를 클릭합니다.
1. **옵션 2**&#x200B;에서 다른 간단한 제품을 선택하십시오.
1. 이제 **확인** 단추를 클릭하고 오류 메시지를 확인합니다.

<u>예상 결과</u>:

오류 메시지가 표시되지 않고 관리자가 요청한 견적 항목을 정상적으로 구성할 수 있습니다.

<u>실제 결과</u>:

다음과 같은 오류 메시지가 표시됩니다.

*서버에 기술적인 문제가 있어 오류가 발생했습니다. 계속하기 위해 다시 시도하십시오. 문제가 지속되면 나중에 다시 시도하십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko)

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
