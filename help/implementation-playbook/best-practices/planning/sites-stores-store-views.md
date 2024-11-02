---
title: 사이트, 스토어 및 스토어 보기 구성에 대한 우수 사례
description: 사이트 성과를 극대화하기 위해 사이트, 스토어 및 스토어 보기를 구성하는 우수 사례를 알아봅니다.
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# 사이트, 스토어 및 스토어 보기 구성에 대한 우수 사례

클라우드 인프라 기반 Adobe Systems Commerce의 경우 우수 사례는 특히 통합 및 개발 환경보다 더 많은 리소스가 있는 프로덕션 환경(및 리소스 제약 조건에 따라 Pro 아키텍처의 스테이징)에 적용됩니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) :

- 클라우드 인프라 기반 Adobe Systems Commerce
- Adobe Systems Commerce 온-프레미스

## 성능 향상을 위한 전략

프로젝트에 많은 사이트, 상점 또는 스토어 보기가 필요한 경우 다음 전략을 사용하여 성능을 향상시킬 수 있습니다.

- 논리를 카테고리로 이동하여 카탈로그 재구성Restructure catalog by shifting logic to categories
- 외부 가격 및 PMS(가격 관리 시스템)를 사용하여 카탈로그 데이터에서 가격표를 분리합니다.
- 대체 noSQL 데이터 스토리지 좋아요 Elasticsearch 사용

## 잠재적인 성능 영향

웹 사이트와 상점은 카탈로그 데이터의 승수이므로 웹 사이트와 상점이 많으면 다음과 같은 방식으로 사이트 성과에 부정적인 영향을 줄 수 있습니다.

- 인덱스 테이블이 클수록 인덱싱 작업을 [완료하는 데 필요한 시간이 늘어납니다. 가격 지수].
- 애플리케이션 구성을 검색하는 데 걸리는 시간이 늘어나면 캐시되지 않은 카탈로그 페이지에 대한 상점 응답 시간이 느려집니다.
- 데이터가 각 웹 사이트에 대해 별도로 저장되므로 관리자에서 저장 작업을 완료하는 데 필요한 시간이 크게 늘어납니다.


## 추가 정보

- [웹 사이트, 스토어 및 스토어 보기 이해](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [여러 웹 사이트 또는 스토어 설정](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites)
