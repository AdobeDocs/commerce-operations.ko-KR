---
title: 온프레미스 설치 개요
description: Adobe Commerce의 온-프레미스 배포를 위한 설치 프로세스에 대해 알아봅니다.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# 온프레미스 설치 개요

>[!NOTE]
>
>다음 다이어그램은 의 높은 수준의 개요를 제공합니다. _**온-프레미스**_ Adobe Commerce 설치:

![설치 작동 방식](../assets/installation/install-diagram-24.svg)

일반적인 설치 흐름은 다음과 같습니다.

1. 서버 환경을 설정합니다.

   PHP, Apache, MySQL, 검색 엔진 등 필수 구성 요소 소프트웨어를 설치합니다. 다음을 참조하십시오. [시스템 요구 사항](system-requirements.md) 추가 정보.

1. Get [인증 키](prerequisites/authentication-keys.md) Commerce Composer 리포지토리에 매핑됩니다.

1. Adobe Commerce 또는 Magento Open Source 소프트웨어를 가져옵니다.

   * (권장) [작성기 메타패키지](composer.md) 모듈 및 해당 종속성을 관리합니다.

   * Magento Open Source 코드베이스에 기여하거나 응용 프로그램을 사용자 지정하려는 경우 [복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub 리포지토리. 이 메서드를 사용하려면 GitHub와 Composer 둘 다에 익숙해야 합니다.

1. 명령줄을 사용하여 응용 프로그램을 설치합니다.

   필수 구성 요소 소프트웨어가 올바르게 설정되지 않아 단계가 실패하는 경우 [전제 조건](prerequisites/overview.md).

1. [확인](next-steps/verify.md) storefront 및 관리자를 확인하여 설치합니다.
