---
title: 다음 [!UICONTROL Security] 탭
description: 에 대해 알아보기 [!UICONTROL Security] 탭 / [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# 다음 [!UICONTROL Security] 탭

다음 **[!UICONTROL Security]** tab은 보안 문제를 설명하고 잠재적인 원인을 격리합니다. 또한 탭의 프레임에 대해서도 설명합니다.

## [!UICONTROL API calls by IP, details by URL]

다음 **[!UICONTROL API calls by IP, details by URL]** 프레임은 선택한 기간 동안 IP별로 많은 API 호출을 보여줍니다. 이 프레임에는 IP 주소와 해당 IP 주소가 액세스한 API URL이 표시됩니다.

![IP별 API 호출](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

다음 **[!UICONTROL Forgot Password]** 액세스 프레임은 선택한 기간 동안 암호 분실 시도 횟수를 보여줍니다. IP 주소에 대한 높은 활동은 사이트에 대한 공격일 수 있습니다.

![암호 분실](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

다음 **[!UICONTROL Create Account access]** 프레임은 선택한 기간 동안의 새 계정 활동 수를 보여 줍니다. 단일 IP 주소에서 활동이 많으면 공격을 나타낼 수 있습니다.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

다음 **[!UICONTROL POST activities]** 프레임은 `POST` 면처리된 사이트 활동 `client_ip` 다음에서 [!DNL Fastly] 로그. 또한 IP 주소로 액세스되는 URL도 표시됩니다.

![POST 활동](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

다음 **[!UICONTROL POST activities summary table]** 요약된 프레임 표시 `POST` 면처리된 사이트 활동 `client_ip` 다음에서 [!DNL Fastly] 로그. 또한 IP 주소로 액세스되는 URL의 카운트가 표시됩니다. 카운트는 선택한 기간에 대한 것입니다.

![POST-활동-요약](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

다음 **[!UICONTROL POST activities details table]** 프레임은 `POST` 사이트 활동: [!DNL Fastly] 로그. 또한 의 모든 세부 정보가 표시됩니다. [!DNL Fastly] 이러한 요청에 대해 기록합니다. 마지막 2000개의 요청으로 제한됩니다.
![POST-활동-세부 정보](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

다음 **[!UICONTROL Guest Carts activities]** frame은 선택한 기간 동안 액세스된 IP 주소 및 URL로 표시된 게스트 장바구니 활동 수를 보여줍니다. 손님용 카트는 카딩 공격에서 사용될 수 있습니다. 이 프레임에는 게스트 카트의 URL에 액세스하는 총 요청 수가 표시됩니다.

![guest-carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

다음 **[!UICONTROL API – forgot password, create account by Countries]** 프레임은 생성된 계정 수와 선택한 기간 동안 잊어버린 암호를 재설정하도록 요청한 수를 보여 줍니다. 해당 요청의 원산지도 함께 표시하기 위해 배치합니다. 이 프레임은 요청의 원산지 국가에 중점을 둡니다.

![api-forgot-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

다음 **[!UICONTROL API - forgot password, create account by Countries and IP address]** 프레임은 생성된 계정 수와 선택한 기간 동안 잊어버린 암호를 재설정하도록 요청한 수를 보여 줍니다. IP 주소, 액세스한 URL 및 요청 원산지를 표시하기 위해 배치됩니다. 이 프레임은 IP 수에 중점을 둡니다.

![api-forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

다음 **[!UICONTROL Guest cart activities by IP]** 프레임은 선택한 기간 동안 IP별로 장바구니 활동을 보여줍니다.

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

다음 **[!UICONTROL Guest cart activities by Countries]** 프레임은 선택한 기간 동안의 국가별 장바구니 활동을 보여 줍니다.

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
