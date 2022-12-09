---
title: "다음 [!UICONTROL Security] tab"
description: 에 대해 알아보기 [!UICONTROL Security] 탭 [!DNL Observation for Adobe Commerce].
source-git-commit: 297c3fed4c0f7ad1a3cb40addef1d33fa8d41525
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# 다음 [!UICONTROL Security] 탭

다음 **[!UICONTROL Security]** 탭에서는 보안 문제에 대해 설명하고 잠재적인 원인을 파악합니다. 또한 탭의 프레임이 설명되어 있습니다.

## [!UICONTROL API calls by IP, details by URL]

다음 **[!UICONTROL API calls by IP, details by URL]** 프레임은 선택한 기간에 대해 IP별로 여러 API 호출을 보여줍니다. 이 프레임은 해당 IP 주소에서 액세스한 IP 주소와 API URL을 표시합니다.

![IP별 API 호출](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

다음 **[!UICONTROL Forgot Password]** 액세스 프레임은 선택한 기간에 걸친 암호 찾기 시도 횟수를 보여줍니다. IP 주소에 대한 높은 활동은 사이트에 대한 공격일 수 있습니다.

![암호 분실](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

다음 **[!UICONTROL Create Account access]** 프레임은 선택한 기간의 새 계정 활동 수를 보여줍니다. 단일 IP 주소에서 높은 활동이 있으면 공격이 발생할 수 있습니다.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

다음 **[!UICONTROL POST activities]** 프레임이 `POST` 사이트에 대한 활동, 면처리된 `client_ip` 에서 [!DNL Fastly] 로그. 또한 IP 주소로 액세스하는 URL을 표시합니다.

![POST 활동](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

다음 **[!UICONTROL POST activities summary table]** 프레임은 요약된 `POST` 사이트에 대한 활동, 면처리된 `client_ip` 에서 [!DNL Fastly] 로그. 또한 IP 주소로 액세스하는 URL에 대한 개수도 표시됩니다. 선택한 기간에 대한 개수입니다.

![POST-activities-summary](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

다음 **[!UICONTROL POST activities details table]** 프레임이 `POST` 사이트에서 활동에 대한 활동 [!DNL Fastly] 로그. 또한 [!DNL Fastly] 이러한 요청에 대해 기록합니다. 이는 마지막 2000개의 요청으로 제한됩니다.
![POST-activities-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

다음 **[!UICONTROL Guest Carts activities]** 프레임은 선택한 시간대의 게스트 장바구니 활동 수를 IP 주소 및 액세스한 URL별로 면처리하여 보여줍니다. 차량 공격시 손님카트를 사용할 수 있습니다 이 프레임은 게스트 장바구니의 URL을 액세스하는 총 요청 수를 보여줍니다.

![게스트 장바구니 활동](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

다음 **[!UICONTROL API – forgot password, create account by Countries]** 프레임은 선택한 일정 동안 생성된 계정 수와 잊어버린 암호를 재설정하도록 요청하는 요청을 보여줍니다. 이번 요청의 원산지 표시 역시 실용적이다. 이 프레임은 요청의 원본 국가에 중점을 둡니다.

![api를 잊어버린 국가](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

다음 **[!UICONTROL API - forgot password, create account by Countries and IP address]** 프레임은 선택한 일정 동안 생성된 계정 수와 잊어버린 암호를 재설정하도록 요청하는 요청을 보여줍니다. IP 주소, 액세스한 URL 및 요청의 원산지 국가를 표시하는 것도 패싯입니다. 이 프레임은 IP 개수에 중점을 둡니다.

![api-forgot-country-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

다음 **[!UICONTROL Guest cart activities by IP]** 프레임은 선택한 일정 동안 IP별로 게스트 장바구니 활동을 보여줍니다.

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

다음 **[!UICONTROL Guest cart activities by Countries]** 프레임은 선택한 일정 간의 국가별 게스트 장바구니 활동을 보여줍니다.

![게스트 장바구니-국가](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
