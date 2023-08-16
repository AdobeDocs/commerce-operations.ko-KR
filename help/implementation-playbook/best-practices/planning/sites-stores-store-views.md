---
title: 사이트, 스토어 및 스토어 조회수 구성에 대한 우수 사례
description: 사이트 성능을 극대화하기 위한 사이트, 스토어 및 스토어 보기 구성 모범 사례에 대해 알아봅니다.
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# 사이트, 스토어 및 스토어 뷰 구성에 대한 우수 사례

최상의 사이트 성능을 위해 클라우드 인프라 프로젝트에서 Adobe Commerce에 대해 최대 50개의 사이트, 50개의 스토어 및 50개의 스토어 보기를 구성합니다.

>[!NOTE]
>
>클라우드 인프라의 Adobe Commerce의 경우 모범 사례는 통합 및 개발 환경보다 더 많은 리소스를 보유하고 있는 프로덕션 환경(및 리소스 제한에 따라 Pro 아키텍처에서 스테이징)에 특히 적용됩니다. 통합(Pro 및 Starter)과 스테이징 환경(Starter)의 경우, 스토어 조회수를 5 또는 10 미만으로 줄이십시오(기술 검토에 따름).

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 성능 향상을 위한 전략

프로젝트에 많은 사이트, 스토어 또는 스토어 보기가 필요한 경우 다음 전략을 사용하여 성능을 향상시킬 수 있습니다.

- 논리를 카테고리로 이동하여 카탈로그 재구성
- 외부 가격 및 가격 관리 시스템(PMS)을 사용하여 카탈로그 데이터와 가격 목록을 구분합니다.
- Elasticsearch과 같은 대체 noSQL 데이터 저장소 사용

## 성능에 영향을 미칠 수 있음

웹 사이트 및 저장소는 카탈로그 데이터의 승수이므로, 많은 웹 사이트 및 저장소가 있으면 다음과 같은 방식으로 사이트 성능에 부정적인 영향을 줄 수 있습니다.

- 인덱스 테이블이 클수록 인덱싱 작업을 완료하는 데 필요한 시간이 늘어남 [물가지수].
- 애플리케이션 구성을 검색하는 시간이 늘어나면 캐시되지 않은 카탈로그 페이지에 대한 storefront 응답 시간이 감소합니다.
- 각 웹 사이트에 대해 데이터가 별도로 저장되므로 관리자에서 저장 작업을 완료하는 데 필요한 시간이 크게 증가합니다.


## 추가 정보

- [웹 사이트, 스토어 및 스토어 조회수 이해](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [여러 웹 사이트 또는 스토어 설정](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
