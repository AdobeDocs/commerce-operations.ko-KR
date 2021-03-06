---
title: Adobe Commerce 통합 옵션
description: 다른 시스템과 Adobe Commerce 구현을 통합하는 옵션을 살펴보십시오.
exl-id: 10de70d2-ff3b-4f10-b370-01d805b745dc
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 일반적인 통합 지점 및 데이터 흐름

통합과 데이터 흐름에 대한 두 가지 주요 접근 방법이 있는데, 이 접근 방식은 매우 유사하지만 한 가지 주요 차이점이 있습니다.

## 모놀리식

다음 다이어그램은 Adobe Commerce을 백엔드 시스템과 Storefront 애플리케이션 모두로 사용하는 획일적인 접근 방식을 설명합니다.

![Adobe Commerce 모노리스 다이어그램](../../assets/playbooks/integration-monolith.svg)

## 헤드리스

다음 다이어그램은 DXP/CMS/사용자 지정 애플리케이션과 통합된 백엔드 시스템으로 Adobe Commerce을 사용하는 헤드리스 접근 방식을 Storedfront 애플리케이션으로 설명합니다.

![Adobe Commerce 헤드리스 다이어그램](../../assets/playbooks/integration-headless.svg)

모놀리식 방식과 헤드리스 방식 간의 유일한 차이점은 Storefront 통합입니다. 이러한 통합은 고객의 사용자 경험에 영향을 줍니다. 모놀리시는 Adobe Commerce storefront를 사용하여 직접 타사 서비스와 통합하지만, 헤드리스는 자체 스토어에 의존하여 동일한 서비스와 사용자 지정 및 통합합니다. 결제 및 SSO(Single Sign-On)와 같은 일부 서비스에는 통합 흐름을 완료하려면 storefront 및 Adobe Commerce 사용자 지정 기능이 모두 필요합니다.

## 타사 시스템

일부 인기 있는 서비스에는 이미 Adobe Commerce 또는 인기 있는 상점(예: PWA Studio, Adobe Experience Manager 및 Value Storefront)을 지원하는 뛰어난 확장이 있으며, 이러한 확장은 확장 마켓플레이스나 관련 타사 웹 사이트에서 찾을 수 있습니다. 기존 확장이 없더라도 Adobe Commerce과 다른 헤드리스 스토어프런트 간의 통합을 구현하려는 노력은 유사합니다. 모든 타사 서비스에는 일반적으로 통합 방법을 설명하는 문서가 있습니다. 그러한 서비스는 단지 몇 가지 예일 뿐입니다. 여러 나라와 시장들이 다른 선택을 할 수 있다.

## 엔터프라이즈 통합

일반적으로 백엔드 통합이라고도 하는 엔터프라이즈 시스템 통합의 경우 비즈니스 데이터 흐름에 영향을 줍니다. 다양한 비즈니스 유형과 요구 사항에 따라 이미 소개된 세 가지 서로 다른 통합 옵션을 사용할 수 있습니다.

SKU, 재고 및 기본 가격과 같은 제품 필수 데이터는 일반적으로 ERP에서 가져오지만 일반적으로 판매 가격은 각 판매 채널(예: Adobe Commerce)이나 CPQ(B2B 또는 비공개 판매)에서 관리됩니다. 제품 필수 데이터(인벤토리 제외)는 자주 변경되지 않으므로 가장 좋은 방법은 REST API 또는 대량 파일 가져오기를 통해 예약된 배치 업데이트를 사용하는 것입니다. Inventory의 경우, Best Practice는 Over-Sales를 방지하기 위해 다른 판매 채널과 공유되는 제품 인벤토리에 대해 일별로 전체 업데이트를 수행하는 것입니다. 또한 24시간 이내에 예약된 ERP의 변경 사항도 증가시킵니다.

제품 카탈로그, 메타데이터 및 마케팅 콘텐츠는 각 판매 채널(예: Adobe Commerce)이나 중앙 PIM에서 별도로 관리할 수 있습니다. 메타데이터도 자주 변경되지 않으므로 REST API 또는 벌크 파일 가져오기를 통해 예약된 배치 업데이트를 사용하는 것이 좋습니다.

주문 데이터에는 일반적으로 중앙 집중식 OMS 및 WMS 시스템에서 관리되는 주문, 견적(B2B), 배송, 반품 및 교환 데이터가 포함됩니다. 주문 데이터는 가능한 한 빨리 동기화되어야 하므로 REST API 가 일반적으로 가장 적합한 옵션입니다. 더 나은 성능을 위해 API 호출 수를 줄이는 것이 좋습니다. 주문 상태, 선적, 반품 및 교환 데이터의 경우 REST 배치 업데이트 API 예약을 시간 또는 분 단위로 고려하십시오.

B2B 데이터는 일반적으로 중앙 집중식 CRM에서 관리됩니다. 실시간 API는 기존 고객을 확인하고 새 고객을 만드는 데 사용됩니다. B2B의 경우 Adobe Commerce과 CRM 또는 CPQ 간에 서로 다른 회사 직원, 그룹 및 가격 목록을 동기화하는 데 더 많은 API를 도입해야 할 수 있습니다.

전자 메일 마케팅 및 비즈니스 데이터 분석을 위한 비즈니스 인텔리전스를 위한 eDM과 같은 다른 시스템 통합도 있습니다. 이러한 통합은 일반적으로 REST API 또는 파일 내보내기/가져오기를 통해 수행되며, 일반적으로 기존 확장에서 지원합니다.
