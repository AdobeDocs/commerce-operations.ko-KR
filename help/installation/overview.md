---
title: 온프레미스 설치 개요
description: Adobe Commerce 및 Magento Open Source의 온프레미스 배포를 위한 설치 프로세스에 대해 알아봅니다.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 7%

---

# 온프레미스 설치 개요

>[!NOTE]
>
>다음 다이어그램은 Adobe Commerce의 _&#x200B;**온-프레미스**&#x200B;_ 설치에 대한 높은 수준의 개요를 제공합니다.

![설치 작동 방식](../assets/installation/install-diagram-24.svg)

일반적인 설치 흐름은 다음과 같습니다.

1. 서버 환경을 설정합니다.

   PHP, Apache, MySQL, 검색 엔진 등 필수 구성 요소 소프트웨어를 설치합니다. 자세한 내용은 [시스템 요구 사항](system-requirements.md)을 참조하십시오.

1. Commerce 작성기 저장소에 [인증 키](prerequisites/authentication-keys.md)를 가져옵니다.

1. Adobe Commerce 소프트웨어를 가져옵니다.

   * (권장) 모듈 및 해당 종속성을 관리하려면 [Composer 메타패키지](composer.md)를 가져옵니다.

   * Magento Open Source 코드베이스에 기여하거나 애플리케이션을 사용자 지정하려면 GitHub 리포지토리를 [복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)합니다. 이 메서드를 사용하려면 GitHub와 Composer 둘 다에 익숙해야 합니다.

1. 명령줄을 사용하여 응용 프로그램을 설치합니다.

   필수 구성 요소 소프트웨어가 올바르게 설정되지 않아 단계가 실패하면 [필수 구성 요소](prerequisites/overview.md)를 검토하십시오.

1. 상점 및 관리자를 보고 [설치를 확인](next-steps/verify.md)합니다.
