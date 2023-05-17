---
title: 성능 벤치마크
description: Adobe 클라우드 인프라에서 호스팅되는 Adobe Commerce 구현의 성능 벤치마크 결과를 검토합니다.
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
source-git-commit: eeb7146a8051e8692ebf974d65db75a4999cf2e6
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# 벤치마크 요약

Adobe Commerce 2.4.5 성능 벤치마크 결과는 다음 인프라 및 추가 구성 요소와 함께 배포된 Adobe Commerce 인스턴스에서 측정된 성능을 반영합니다.
- [Pro 클라우드 환경](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) with [스케일 아키텍처](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [Adobe Commerce용 B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

추가 사용자 지정 사항이 없습니다.

다음 정보는 벤치마크 결과를 요약하고 테스트 중에 사용되는 환경 및 데이터에 대한 정보를 제공합니다.

## 주요 성능 지표

다음 그림은 성능 벤치마크에 대한 상거래 저장소 구성과 테스트 결과의 주요 성능 지표를 보여줍니다.

![성능 벤치마크 JMeter 및 프로덕션 인프라](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

엔터프라이즈 B2C 조직을 모방하는 테스트 기준에 따라, 시스템이 표준 로드 플로우에서 피크 시간 동안 요청된 트래픽 및 주문 번호를 처리할 수 있다.

### 성능 특징

- **주문**—99번째 백분위수에 대한 응답 시간을 2초 미만으로 유지한 채 분당 3,481개의 주문을 처리했습니다(요청의 99%가 2초 미만의 응답 시간으로 처리됨).
- **페이지 보기 수**- 99번째 백분위수에 대해 2초 미만의 응답 시간을 유지하면서 시간당 200만 개 이상의 페이지 보기를 처리합니다.
- **유효 SKU**—고객 프로필에는 2억 4,200만 개의 다양한 가격 변형이 포함되어 있습니다(<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>) 를 사용하십시오.
- **GraphQL 요청**—99번째 백분위수에 대해 2초 미만의 응답 시간을 유지하면서 분당 10,500개의 GraphQL에서 캐시되지 않은 요청 수로 시스템 크기가 조정되었습니다.
- **동시 관리 사용자**—99번째 백분위수에 대해 2초 미만의 응답 시간을 유지하면서 동시 관리 사용자 500명을 지원하도록 시스템이 확장되었습니다.

## 테스트 환경

성능 벤치마크 결과는 크기가 조정된 아키텍처로 Pro 클라우드 환경에 배포된 Adobe Commerce 2.4.5 인스턴스에 대해 테스트하여 얻습니다. 또한 인스턴스에는 Adobe Commerce B2B, Inventory management 및 Adobe Stock 통합 모듈이 설치, 구성 및 활성화되었습니다.

테스트 프로필에 대한 성능 테스트 데이터가 <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Performance Toolkit</a>.

성능 측정은 고객 및 비즈니스 사용자를 위한 일상적인 저장소 활동을 시뮬레이션하여 측정한 것입니다. 이 값은 각 사례에 대해 최대 처리량을 반영하지만 개인 판매 또는 플래시 판매와 같은 고유한 비즈니스 모델을 반영하지는 않습니다.

- **LUMA 상점**
   - 3000명의 동시 사용자
   - 30% CDN 캐시 적중률로 설정

      캐시 레이어를 효율적으로 사용하면 시간당 페이지 보기 수가 증가합니다.

- **GraphQL API**
   - 250개의 동시 스레드
   - 0% CDN 캐시 적중률로 설정

      GraphQL 앞에 캐싱 레이어를 사용하면 응답 시간이 크게 개선됩니다.

- **관리 웹**
   - 동시 사용자 500명
   - 0% CDN 캐시 적중률로 설정

## 테스트 환경 사양

Adobe Commerce 인스턴스에 대해 실행된 JMeter 로드 프로필을 사용하여 로드 테스트가 완료되었습니다. 테스트 중에 세 개의 웹 노드와 세 개의 서비스 노드가 사용되었습니다. 다음 이미지는 JMeter 및 프로덕션 인프라의 시작 지점을 자세히 설명합니다.

![성능 벤치마크 JMeter 및 프로덕션 인프라](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### 애플리케이션

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> pro 아키텍처를 사용하여 클라우드 인프라에 배포됩니다.

### 인프라

성능 벤치마크를 위해 Adobe Commerce 2.4.5가 [확장 가능한 인프라](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) 다음 용량을 사용할 수 있습니다.

- **웹 노드 사양**
   - vCPU 216(3 노드 72개)
   - 메모리 432 GiB(144 x 3 노드)
   - 네트워크 대역폭 768Gbps(256x3노드)
   - EBS 대역폭 57000 Mbps(19000 x 3 노드)
   - 프로비저닝된 스토리지 100GB

- **서비스 노드 사양**
   - vCPU 192(3 노드 64개)
   - 메모리 768 GiB(256 x 3 노드)
   - 네트워크 대역폭 60Gbps(3 노드 20개)
   - EBS 대역폭 40800 Mbps(13600 x 3 노드)
   - 프로비저닝된 스토리지 1100GB
