---
title: 참조 아키텍처
description: Adobe Systems Commerce 배포를 위한 권장 참조 아키텍처의 다이어그램을 검토하십시오.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# 참조 아키텍처

이 항목에서는 리소스가 다른 사용자와 공유되지 않는 데이터 센터(가상화되지 않음)에서 물리적으로 호스팅되는 일반 서버를 사용하는 Adobe Systems Commerce 인스턴스에 대한 일반적인 권장 설정에 대해 설명합니다. 호스팅 공급자, 특히 Commerce 고성능 호스팅을 전문으로 하는 경우 요구 사항에 따라 동일하거나 더 효과적인 다른 설정을 추천할 수 있습니다.

클라우드 인프라 환경에 대한 Adobe Commerce의 경우 [Starter 아키텍처](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture)를 참조하십시오.

## [!DNL Commerce] 참조 아키텍처 다이어그램

[!DNL Commerce] 참조 아키텍처 다이어그램은 확장 가능한 [!DNL Commerce] 사이트를 설정하는 모범 사례 방법을 나타냅니다.

다이어그램의 각 요소 색상은 요소가 Magento Open Source의 일부인지 Adobe Commerce의 일부인지 여부와 필요한 경우 이 요소를 나타냅니다.

* Magento Open Source 시 주황색 요소가 필요합니다.
* 회색 요소는 Magento Open Source 시 선택 사항입니다
* 파란색 요소는 Adobe Commerce에서 선택 사항입니다

![상거래 참조 아키텍처 다이어그램](../assets/performance/images/ref-architecture-2.3.png)

다음 섹션에서는 상거래 참조 아키텍처 다이어그램의 각 섹션에 대한 권장 사항 및 고려 사항을 제공합니다.

### [!DNL Varnish]

* 클러스터는 [!DNL Varnish] 사이트의 트래픽 수에 맞게 확장할 수 있습니다
* 필요한 캐시 페이지 수에 따라 인스턴스 크기를 조정합니다
* 트래픽이 많은 사이트에서 [!DNL Varnish]을(를) 기본으로 사용하여 웹 계층당 하나의 요청을 캐시에서 플러시합니다

### 웹

* 트래픽 및 중복을 위한 노드 확장 활성화
* 하나의 노드가 마스터이고 cron을 실행합니다.
* 또는 전용 관리자 및 작업자 노드를 사용합니다

### 캐시

* 세션에 대해 별도의 Redis 인스턴스 구현 고려
* 캐시 당 Redis 인스턴스 를 가질 수 있습니다
* 가장 큰 예상 캐시 크기를 포함하도록 인스턴스 크기 조정

### 데이터베이스 및 큐

* 트래픽이 많은 사이트는 슬레이브 DB로 DB 성능을 조정하고 주문/장바구니에 대한 DB를 분할할 수 있습니다(Adobe Commerce).
* 빠른 복구 및 데이터 백업을 위해 슬레이브 DB를 사용하는 것이 좋습니다
* 트래픽이 적은 사이트는 DB에 이미지를 저장할 수 있습니다.

### 검색 {#search-heading}

* 검색 트래픽에 따라 인스턴스 수 조정

### 스토리지

* GFS 또는 GlusterFS를 사용하여 Pub/Media 스토리지를 사용하는 것이 좋습니다.
* 또는 트래픽 빈도가 낮은 사이트에 DB 스토리지를 사용합니다

### 권장되는 [!DNL Varnish] 참조 아키텍처

Magento는 확장을 통해 범위를 확장하는 것과 함께 몇 가지 전체 페이지 캐싱 엔진(파일, Memcache, [!DNL Varnish]Redis 등)을 즉시 사용할 수 있도록 지원합니다. [!DNL Varnish] 은 권장되는 전체 페이지 캐시 엔진입니다.  [!DNL Commerce][!DNL Varnish] 다양한 구성을 지원합니다.

고가용성이 필요하지 않은 사이트의 경우 Nginx SSL 종료와 함께 간단한 [!DNL Varnish] 설정을 사용하는 것이 좋습니다.

![SSL 종료를 사용한 간단한 [!DNL Varnish] 구성](../assets/performance/images/single-varnish-with-ssl-termination.png)

고가용성이 필요한 사이트의 경우 SSL 종료 로드 밸런서와 함께 2계층 [!DNL Varnish] 구성을 사용하는 것이 좋습니다.

SSL이 부하 분산 장치를 종료하는 ![고가용성 2계층 [!DNL Varnish] 구성](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
