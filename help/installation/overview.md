---
title: 온프레미스 설치 개요
description: Adobe Commerce 및 Magento Open Source의 온프레미스 배포를 위한 설치 프로세스에 대해 알아봅니다.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 9ad18dac76f171ad0f90330e1a1347baa056403b
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 2%

---


# 온프레미스 설치 개요

이 페이지에서는 자체 인프라에 Adobe Commerce을 설치하는 방법에 대한 개요를 제공합니다. 설치 프로세스에는 서버 환경 설정, 필요한 소프트웨어 및 자격 증명 획득, 설치 명령 실행 등이 포함됩니다.

약 30~60분 내에 Adobe Commerce 온프레미스 소프트웨어를 설치할 수 있습니다. 그러나 설치 전에 서버 환경을 설정하는 데 필요한 시간은 사용자 경험과 선택하는 기술에 따라 다릅니다.

>[!TIP]
>
>성공적으로 진행하려면 중간 기술 지식과 서버 액세스 권한이 있어야 합니다.

설치를 통해 [고객 응대 상점](https://experienceleague.adobe.com/ko/docs/commerce-admin/start/storefront/storefront) 및 [관리 패널](https://experienceleague.adobe.com/ko/docs/commerce-admin/start/admin/admin)이 모두 포함된 완전한 기능의 Adobe Commerce 스토어가 만들어집니다. 프로세스를 시작하기 전에 데이터베이스 자격 증명, 도메인 정보 및 인증 키를 준비해야 합니다.

## 판매자 책임

Adobe Commerce 온프레미스를 사용하면 서버, 호스팅 환경 및 시스템 유지 관리를 포함한 자체 인프라를 호스팅 및 관리할 수 있습니다. Adobe은 다음을 포함하여 핵심 Commerce 애플리케이션에 대한 지원을 특별히 제공합니다.

- 제품 업데이트 및 수정 사항에 대한 액세스
- 취약점 해결을 위한 보안 패치
- 자체 호스팅 솔루션의 관리 및 최적화에 도움이 되는 포괄적인 설명서

고객은 환경을 완벽하게 제어할 수 있으므로 사용자 정의 및 유연성을 향상시킬 수 있지만 인프라의 성능, 보안 및 확장성을 보장할 책임이 있습니다. 예를 들어, 다음 책임은 귀하에게 있습니다.

- 모든 Adobe Commerce 온프레미스 시스템의 디자인, 구현, 구성, 유지 관리, 문제 해결 및 성능 테스트.
   - 서버, 운영 체제, 데이터베이스, [!DNL PHP], 검색, 캐싱, 전체 페이지 캐시 및 콘텐츠 전달 네트워크. 일반적인 테마는 [!DNL Nginx/Apache], [!DNL PHP], [!DNL MySQL/MariaDB], [!DNL Redis], [!DNL Elasticsearch/OpenSearch], [!DNL RabbitMQ], [!DNL Varnish], [!DNL DNS], [!DNL SSL/TLS certificates] 및 사용된 모든 [!DNL CDN]을(를) 포함할 수 있습니다(이에 국한되지 않음).
- 용량 계획, 자동 확장, 클러스터링, 백업, 재해 복구
- 모든 제품 및 고객 데이터, 디자인, 구성 및 설정, 애플리케이션 및 데이터베이스 유지 보수, 코드 배포, 버전 업그레이드 및 패치 애플리케이션
- APM/로깅/경고를 통한 모니터링 및 경고(예: [!DNL New Relic], [!DNL Datadog], [!DNL ELK])
- 운영 체제, [!DNL PHP], 데이터베이스, 미들웨어 강화 및 업데이트를 위한 보안 패치

## 워크플로

다음 다이어그램은 온-프레미스 환경용 Adobe Commerce 설치와 관련된 주요 단계를 보여 줍니다.

![설치 작동 방식](../assets/installation/on-premises-install.drawio.svg)

### 서버 환경 설정

[필수 구성 요소](prerequisites/overview.md)에 따라 PHP, 웹 서버, 데이터베이스 및 검색 엔진을 설치하고 구성합니다.

### 인증 키 가져오기

Commerce Marketplace에서 새 [인증 키](prerequisites/authentication-keys.md)를 생성하거나 기존 키를 복사하여 Adobe Commerce Composer 패키지에 액세스합니다.

### Adobe Commerce 소프트웨어 다운로드

[작성기](prerequisites/commerce.md)(권장)를 사용하여 다운로드하거나 개발 기여를 위해 GitHub에서 복제하십시오.

Magento Open Source 코드베이스에 기여하거나 애플리케이션을 사용자 지정하려면 GitHub 리포지토리를 [복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)합니다. 이 메서드를 사용하려면 GitHub와 Composer 둘 다에 익숙해야 합니다.

### 애플리케이션 설치

특정 구성을 사용하여 설치 명령을 실행합니다. 전체 예제는 [빠른 시작](composer.md)을 참조하세요.

>[!NOTE]
>
>필수 구성 요소 소프트웨어가 올바르게 설정되지 않아 단계가 실패하면 [필수 구성 요소](prerequisites/overview.md)를 검토하십시오.

### 설치 확인

모든 것이 올바르게 작동하는지 확인하려면 상점 및 관리자 패널을 [테스트](next-steps/verify.md)하십시오.

## 일반적인 설치 문제

- **권한 오류**: 파일 시스템 소유권 및 사용 권한이 올바른지 확인하십시오.
- **데이터베이스 연결 실패**: 데이터베이스 자격 증명과 네트워크 연결을 확인하십시오.
- **인증 키 오류**: Commerce Marketplace 키가 유효하고 활성 상태인지 확인하십시오
- **메모리 제한**: PHP 메모리 할당이 충분한지 확인합니다(최소 2GB 권장).
