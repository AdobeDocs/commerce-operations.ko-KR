---
title: '[!UICONTROL Security] 탭'
description: '[!UICONTROL Security]의  [!DNL Observation for Adobe Commerce] 탭에 대해 알아봅니다.'
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!UICONTROL Security] 탭

**[!UICONTROL Security]** 탭은 보안 문제를 설명하고 잠재적인 원인을 격리합니다. 또한 탭의 프레임에 대해서도 설명합니다.

## [!UICONTROL API calls by IP, details by URL]

**[!UICONTROL API calls by IP, details by URL]** 프레임에는 선택한 일정 동안 IP별로 여러 개의 API 호출이 표시됩니다. 이 프레임에는 IP 주소와 해당 IP 주소가 액세스한 API URL이 표시됩니다.

![IP별 API 호출](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

**[!UICONTROL Forgot Password]** 액세스 프레임에 선택한 일정 동안의 암호 찾기 시도 횟수가 표시됩니다. IP 주소에 대한 높은 활동은 사이트에 대한 공격일 수 있습니다.

![암호 찾기](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

**[!UICONTROL Create Account access]** 프레임에는 선택한 일정 동안의 새 계정 활동 수가 표시됩니다. 단일 IP 주소에서 활동이 많으면 공격을 나타낼 수 있습니다.

![계정 만들기 액세스](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

**[!UICONTROL POST activities]** 프레임에는 `POST` 로그에서 `client_ip`에 패싯된 사이트에 대한 [!DNL Fastly] 활동이 표시됩니다. 또한 IP 주소로 액세스되는 URL도 표시됩니다.

![사후 활동](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

**[!UICONTROL POST activities summary table]** 프레임에는 `POST` 로그에서 `client_ip`에 패싯된 사이트에 대한 요약된 [!DNL Fastly] 활동이 표시됩니다. 또한 IP 주소로 액세스되는 URL의 카운트가 표시됩니다. 카운트는 선택한 기간에 대한 것입니다.

![POST-activities-summary](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

**[!UICONTROL POST activities details table]** 프레임에는 `POST` 로그에서 사이트에 대한 [!DNL Fastly] 활동이 표시됩니다. 또한 이러한 요청에 대한 [!DNL Fastly] 로그의 모든 세부 정보를 표시합니다. 마지막 2000개의 요청으로 제한됩니다.
![POST-activities-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

**[!UICONTROL Guest Carts activities]** 프레임은 IP 주소 및 URL을 통해 액세스된 선택한 일정의 장바구니 활동 수를 표시합니다. 손님용 카트는 카딩 공격에서 사용될 수 있습니다. 이 프레임에는 게스트 카트의 URL에 액세스하는 총 요청 수가 표시됩니다.

![guest-carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

**[!UICONTROL API – forgot password, create account by Countries]** 프레임에는 선택한 일정 동안 만든 계정의 수와 잊어버린 암호를 재설정하도록 요청하는 내용이 표시됩니다. 해당 요청의 원산지도 함께 표시하기 위해 배치합니다. 이 프레임은 요청의 원산지 국가에 중점을 둡니다.

![api-forgot-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

**[!UICONTROL API - forgot password, create account by Countries and IP address]** 프레임에는 선택한 일정 동안 만든 계정의 수와 잊어버린 암호를 재설정하도록 요청하는 내용이 표시됩니다. IP 주소, 액세스한 URL 및 요청 원산지를 표시하기 위해 배치됩니다. 이 프레임은 IP 수에 중점을 둡니다.

![api-forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

**[!UICONTROL Guest cart activities by IP]** 프레임에는 선택한 기간 동안 IP별 게스트 장바구니 활동이 표시됩니다.

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

**[!UICONTROL Guest cart activities by Countries]** 프레임에는 선택한 일정 동안의 국가별 장바구니 활동이 표시됩니다.

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
