---
title: Adobe Commerce 통합 전략
description: Adobe Commerce 구현을 위한 통합 전략 및 옵션을 검토하십시오.
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Adobe Commerce 통합 전략

플랫폼을 통합하는 기능은 &quot;협상 불가&quot; 입니다. 기업들은 다양한 터치포인트에서 액세스할 수 있고 기술 시스템, 특히 ERP에 완벽하게 통합되기를 원합니다. 고객의 요구 사항, 글로벌 확장성 및 경제성도 최종 플랫폼 구매에 중요한 역할을 합니다.

GraphQL API, 포괄적인 REST API 및 Adobe Commerce과 다른 시스템 또는 서비스 간에 일괄 파일 가져오기로 상점 및 백엔드 시스템에 대한 포괄적인 통합 접근 방식이 지원됩니다.

Adobe Commerce GraphQL API는 다음과 같은 다른 스토어프런트와의 통합에 사용할 수 있는 포괄적인 스토어프론트 범위를 제공합니다.

- Adobe Experience Manager 및 Bloomreach와 같은 DXP(디지털 경험 플랫폼)
- Drupal 및 WordPress와 같은 CMS(콘텐츠 관리 시스템)
- Adobe Commerce, PWA Studio 및 Value Storefront와 같은 최신 사용자 정의 상점 전면 애플리케이션

GraphQL은 효율적이고 채널별 응답, 데이터 오버페치 및 새로운 터치 포인트 기능의 민첩한 배포를 제공합니다. 또한 모바일 기본 앱, POS, IoT, 소셜 채널 및 Facebook, Google, Instagram, WeChat 및 TikTok과 같은 실시간 스트리밍 상거래 채널과 통합하도록 선택되는 경우가 많습니다.

Adobe Commerce REST API는 제품 및 카탈로그를 포함한 포괄적인 시스템 구성 적용 범위 및 데이터 관리 기능을 제공합니다. 장바구니, 견적 및 체크아웃 고객, 계정 및 회사 및 주문 및 반품. REST API는 벌크 작업, 여러 인증 모드 및 세부 인증을 지원하므로 다음과 같이 엔터프라이즈 시스템과 통합하기 위해 REST API를 선택하는 경우가 많습니다.

- SAP와 같은 ERP(Enterprise Resource Planning) 시스템
- Akeneo와 같은 PIM(제품 정보 관리) 시스템
- Salesforce와 같은 CRM(고객 관계 관리) 시스템
- MOM, Manhattan, SAP와 같은 주문 관리 시스템(OMS)
- oracle, NetSuite, SAP WM과 같은 WMS(Warehouse Management System) 또는 타사 물류(3PL)
- SalesforceCPQ와 같은 구성, 가격, 견적(CPQ)
- Adobe DAM과 같은 DAM(디지털 자산 관리).

또한 배치 파일 가져오기는 ERP 및 PIM과 같은 엔터프라이즈 시스템을 통합할 수 있는 좋은 옵션으로 간주되며, 이러한 데이터는 자주 변경되지 않으며 예약된 파일 가져오기로 성능이 향상됩니다. 따라서 배치 파일 가져오기는 일반적으로 일별/주별 및 월별 전체 데이터 동기화에 대해 일괄 데이터 동기화를 위해 선택되지만, 증가분 데이터 변경 동기화를 위해 REST API가 선택되므로 성능이 향상됩니다. 이 작업은 또한 예약된 작업으로만 간주되지만, 비즈니스 요구 사항에 따라 15분에서 1시간 간격으로 자주 수행할 수 있습니다.

## 통합 옵션

Adobe Commerce은 세 가지 유연한 통합 옵션을 제공합니다.

- 사전 설치된 커넥터와 시스템 간 직접 통합. 일부 시스템에는 Adobe Commerce Marketplace 또는 자체 웹 사이트에서 Adobe Commerce 확장이 이미 있을 수 있습니다.

- 사용자 정의 미들웨어를 통한 시스템 간 통합. 배포된 사용자 지정 미들웨어 솔루션은 프로세스 데이터 매핑, 번역 및 관리에 사용됩니다.

- Mulesoft, Boomi 및 소프트웨어 AG와 같이 EAI(Enterprise Application Integration Platform)라고도 하는 iPaaS(Integration Platform-as-a-Service)를 통한 시스템 간 통합.

![Adobe Commerce 통합 옵션](../../assets/playbooks/integration-options.svg)

보통 실시간 통합이 필요하지만 일부 시나리오에는 필요하지 않습니다. Adobe Commerce은 기본적으로 비동기 프로세스를 활성화하기 위해 메시지 버스로 RabbitMQ를 지원합니다. 이 기능은 실시간으로 교환하지 않아도 되지만, 배치 파일 교환 또는 REST 배치 데이터 프로세스 API로 업데이트하여 비동기적으로 처리하는 것이 좋습니다.
