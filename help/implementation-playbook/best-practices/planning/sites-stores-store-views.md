---
title: 사이트, 저장소 및 저장소 보기 구성에 대한 우수 사례
description: 사이트 성능을 극대화하도록 사이트, 저장소 및 저장소 보기를 구성하는 모범 사례에 대해 배웁니다.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# 사이트, 저장소 및 저장소 보기 구성에 대한 우수 사례

최상의 사이트 성능을 위해 클라우드 인프라 프로젝트에서 Adobe Commerce에 대해 최대 50개의 사이트, 50개의 저장소 및 50개의 저장소 보기를 구성합니다.

>[!NOTE]
>
>클라우드 인프라의 Adobe Commerce의 경우, 우수 사례는 통합 및 개발 환경보다 더 많은 리소스를 가질 프로덕션 환경(및 Pro 아키텍처의 스테이징이 있을 수 있음)에 특히 적용됩니다. 통합(Pro 및 Starter)과 스테이징 환경(Starter)의 경우 저장소 보기 수를 5개 또는 10개 미만으로 줄입니다(기술 검토 대상).

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 성능 향상 전략

프로젝트에 많은 사이트, 스토어 또는 저장소 보기가 필요한 경우 다음 전략을 사용하여 성능을 향상시킬 수 있습니다.

- 논리를 카테고리로 이동하여 카탈로그 재구성
- 외부 가격과 PMS(Price Management System)를 사용하여 카탈로그 데이터에서 가격 목록을 구분합니다.
- Elasticsearch과 같은 다른 noSQL 데이터 저장소 사용

## 성능에 영향을 줄 수 있음

웹 사이트 및 스토어는 카탈로그 데이터에 대한 멀티플라이어이므로 많은 웹 사이트 및 스토어를 사용하면 다음과 같은 방법으로 사이트 성능에 부정적인 영향을 줄 수 있습니다.

- 인덱스 테이블이 크면 색인 작업을 완료하는 데 필요한 시간이 늘어납니다. [가격 인덱스].
- 응용 프로그램 구성을 검색하는 시간이 증가하면 캐싱되지 않은 카탈로그 페이지에 대한 Storefront 응답 시간이 저하됩니다.
- 데이터가 각 웹 사이트에 대해 별도로 저장되므로 관리자에서 저장 작업을 완료하는 데 필요한 시간이 크게 증가합니다.


## 추가 정보

- [웹 사이트, 저장소 및 저장소 보기 이해](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [여러 웹 사이트 또는 저장소 설정](https://devdocs.magento.com/cloud/project/project-multi-sites.html)

