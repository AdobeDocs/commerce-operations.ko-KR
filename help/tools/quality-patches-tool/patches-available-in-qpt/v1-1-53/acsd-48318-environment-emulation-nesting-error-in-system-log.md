---
title: 'ACSD-48318: ''system.log''에 환경 에뮬레이션 중첩 오류'
description: ACSD-48318 패치를 적용하여 송장 이메일이 전송될 때마다 *main.ERROR:Environment 에뮬레이션 중첩이 허용되지 않음* 오류 메시지가 'system.log'에 표시되는 Adobe Commerce 문제를 해결합니다.
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-48318: `system.log`에 환경 에뮬레이션 중첩 오류가 있습니다.

ACSD-48318 패치는 송장 전자 메일이 전송될 때마다 `system.log`에 *main.ERROR:Environment 에뮬레이션 중첩이 허용되지 않는* 오류 메시지가 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48318입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

송장 전자 메일이 전송될 때마다 *환경 에뮬레이션 중첩이 허용되지 않습니다* 오류 메시지가 `system.log`에 나타납니다.

<u>재현 단계</u>:

1. 주문을 하고 송장을 생성합니다.
1. Admin에서 송장을 열고 **[!UICONTROL Send Email]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Send Email]**&#x200B;을(를) 클릭하여 *신용 메모* 및 *배송*&#x200B;에 대해 동일한 단계를 수행합니다.

<u>예상 결과</u>:

`system.log`에 오류가 없습니다.

<u>실제 결과</u>:

`system.log`이(가) *main.ERROR로 가득 찼습니다. 환경 에뮬레이션 중첩이 허용되지 않습니다* 오류.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

[[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
