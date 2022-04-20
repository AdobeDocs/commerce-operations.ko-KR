---
title: 참조 아키텍처
description: Adobe Commerce 및 Magento Open Source 배포에 대한 권장 참조 아키텍처의 다이어그램을 검토합니다.
source-git-commit: 9ab52374e031bd2b0a846dd5f47c89ff788dcafa
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# 참조 아키텍처

이 항목에서는 리소스가 다른 사용자와 공유되지 않는 데이터 센터(가상화되지 않음)에서 물리적으로 호스팅되는 일반 서버를 사용하는 Adobe Commerce 및 Magento Open Source 인스턴스에 대한 일반 권장 설정에 대해 설명합니다. 호스팅 제공업체는 특히 상거래 고성능 호스팅을 전문으로 하는 경우 요구 사항에 균등하게 또는 더 효과적인 다른 설정을 추천할 수 있습니다.

클라우드 인프라 환경에 대한 Adobe Commerce의 경우 다음을 참조하십시오 [스타터 아키텍처](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] 참조 아키텍처 다이어그램

다음 [!DNL Commerce] 참조 아키텍처 다이어그램은 확장 가능 구조를 설정하는 모범 사례를 나타냅니다 [!DNL Commerce] 사이트.

다이어그램에 있는 각 요소의 색상은 요소가 Magento Open Source에 속하는지 또는 Adobe Commerce에 속하는지 여부 및 필요한 경우 나타냅니다.

* Magento Open Source에 주황색 요소가 필요합니다
* 회색 요소는 Magento Open Source에 선택 사항입니다
* 파란색 요소는 Adobe Commerce에 선택 사항입니다

![상거래 참조 아키텍처 다이어그램](../assets/performance/images/ref-architecture-2.3.png)

다음 섹션에서는 상거래 참조 아키텍처 다이어그램의 각 섹션에 대한 권장 사항 및 고려 사항을 제공합니다.

### [!DNL Varnish]

* A [!DNL Varnish] 클러스터는 사이트의 트래픽에 맞게 확장할 수 있습니다
* 필요한 캐시 페이지 수에 따라 인스턴스 크기를 조정합니다
* 트래픽이 많은 사이트에서 [!DNL Varnish] 웹 계층당 한 개의 요청(최대)을 온-캐시 플러시하도록 기본

### 웹

* 트래픽 및 중복성을 위해 노드 확장 사용
* 하나의 노드는 마스터이고 cron을 실행합니다.
* 또는 전용 관리자 및 작업자 노드를 사용합니다

### 캐시

* 세션에 대해 별도의 Redis 인스턴스 구현을 고려해 보십시오
* 캐시당 Redis 인스턴스를 가질 수 있습니다
* 예상 캐시 크기가 가장 큰 인스턴스에 크기를 지정합니다.

### 데이터베이스 및 큐

* 높은 트래픽 사이트에서는 주문/장바구니에 대해 슬레이브 DB를 사용하여 DB 성능을 튜닝하고 DB를 분할할 수 있습니다(Adobe Commerce)
* 슬레이브 DB를 사용하여 빠른 복구 및 데이터 백업을 수행할 수 있습니다
* 낮은 트래픽 사이트는 DB에 이미지를 저장할 수 있습니다

### 검색

* 검색 트래픽을 기반으로 인스턴스 수 조정

### 스토리지

* GFS 또는 GlusterFS를 pub/media 스토리지에 사용하는 것이 좋습니다
* 또는 낮은 트래픽 사이트에 DB 스토리지 사용

### 권장 [!DNL Varnish] 참조 아키텍처

Magento은 여러 개의 전체 페이지 캐싱 엔진(파일, Memcache, Redis, [!DNL Varnish]) 즉시 사용 가능하며, 확장을 통한 광범위한 범위를 제공합니다. [!DNL Varnish] 권장 전체 페이지 캐시 엔진입니다.  [!DNL Commerce] 다양한 지원 [!DNL Varnish] 구성.

고가용성이 필요하지 않은 사이트의 경우 간단한 [!DNL Varnish] nginx SSL이 종료되어 설정됩니다.

![단순 [!DNL Varnish] SSL 종료를 사용한 구성](../assets/performance/images/single-varnish-with-ssl-termination.png)

고가용성이 필요한 사이트의 경우 2-tier를 사용하는 것이 좋습니다 [!DNL Varnish] ssl 종료 로드 밸런서를 사용하는 구성.

![고가용성 2 계층 [!DNL Varnish] SSL 종료 로드 밸런서를 사용한 구성](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
