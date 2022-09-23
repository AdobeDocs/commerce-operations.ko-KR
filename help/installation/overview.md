---
title: 온-프레미스 설치 개요
description: Adobe Commerce 및 Magento Open Source의 온-프레미스 배포에 대한 설치 프로세스에 대해 알아봅니다.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# 온-프레미스 설치 개요

>[!NOTE]
>
>다음 다이어그램은 _**온-프레미스**_ Adobe Commerce 및 Magento Open Source 설치:

![설치 작동 방식](../assets/installation/install-diagram-24.svg)

일반적인 설치 흐름은 다음과 같습니다.

1. 서버 환경을 설정합니다.

   PHP, Apache, MySQL 및 검색 엔진을 비롯한 사전 요구 사항 소프트웨어를 설치합니다. 자세한 내용은 [시스템 요구 사항](system-requirements.md) 추가 정보.

1. Get [인증 키](prerequisites/authentication-keys.md) 를 전자 상거래 작성기 리포지토리에 추가합니다.

1. Adobe Commerce 또는 Magento Open Source 소프트웨어를 가져옵니다.

   * (권장) [작성기 메타카지](composer.md) 모듈 및 해당 종속성을 관리합니다.

   * Magento Open Source 코드 베이스에 기여하거나 응용 프로그램을 사용자 정의하려면 [복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) gitHub 리포지토리. 이 메서드를 사용하려면 GitHub 및 Composer에 익숙해야 합니다.

1. 명령줄을 사용하여 응용 프로그램을 설치합니다.

   필수 구성 요소 소프트웨어가 올바르게 설정되지 않아 단계가 실패하면 [전제 조건](prerequisites/overview.md).

1. [확인](next-steps/verify.md) 저장소 및 관리자를 확인하여 설치를 수행합니다.
