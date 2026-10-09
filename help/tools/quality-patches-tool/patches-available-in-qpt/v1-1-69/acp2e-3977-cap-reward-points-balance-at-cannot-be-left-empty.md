---
title: 'ACP2E-3977: [!UICONTROL Cap Reward Points Balance At] 필드는 비워 둘 수 없습니다.'
description: ACP2E-3977 패치를 적용하여 **[!UICONTROL Rewards Points Balance Redemption Threshold]** 필드가 설정된 경우 **[!UICONTROL Cap Reward Points Balance At]** 필드를 비워 둘 수 없어 유효성 검사 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Configuration, Rewards
role: Admin, Developer
type: Troubleshooting
exl-id: 5275911f-4f8c-4b37-af11-24ceb69406c9
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4069cee6-4dc8-5a83-81de-232af6a7c9e9
    internal-label: Rewards
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%
---
# ACP2E-3977: **[!UICONTROL Cap Reward Points Balance At]** 필드는 비워 둘 수 없습니다.

ACP2E-3977 패치는 허용되어야 하는 경우에도 **[!UICONTROL Cap Reward Points Balance At]** 필드를 비워 둘 수 없는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACP2E-3977입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p10

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Cap Reward Points Balance At]**&#x200B;을(를) 비워 두면 유효성 검사 오류가 트리거됩니다. 단, 비워 두면 캡이 비활성화됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward points]**(으)로 이동합니다.
1. **[!UICONTROL Rewards Points Balance Redemption Threshold]** = *30*&#x200B;을(를) 설정합니다.
1. **[!UICONTROL Cap Reward Points Balance At]**&#x200B;을(를) 비워 둡니다.
1. 저장.

<u>예상 결과</u>:

**[!UICONTROL Cap Reward Points Balance At]**&#x200B;에 대해 빈 값이 허용되며 제한을 사용할 수 없습니다.

<u>실제 결과</u>:

*상한 보상 포인트 잔액이 잘못되었습니다. 잔고는 양수이거나 비워둘 필요가 있다. 확인하고 다시 시도하십시오.* 오류가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
