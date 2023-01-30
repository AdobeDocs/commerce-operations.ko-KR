---
title: Redis 서비스 구성에 대한 우수 사례
description: Adobe Commerce 2.3.5의 확장된 Redis 캐시 구현을 사용하여 캐싱 성능을 향상시키는 방법을 알아봅니다.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 12de523cc7ea1486c894d54efe6944d92d87ded0
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Redis 서비스 구성에 대한 우수 사례

- 클라우드 인프라에 배포된 Adobe Commerce 2.3.3 이상의 경우 Redis 버전 5.0으로 업그레이드하십시오.
- Adobe Commerce 버전 2.3.5 이상의 경우 확장된 Redis 캐시 구현을 사용하십시오. 이 구현에는 Adobe Commerce의 각 요청에 대해 수행되는 Redis 쿼리 수를 최소화하기 위한 다음 최적화 기능이 포함되어 있습니다.
   - Redis와 Adobe Commerce 간의 네트워크 데이터 전송 크기 감소
   - 로드해야 하는 사항을 자동으로 결정할 수 있는 어댑터의 기능을 개선하여 CPU 사이클의 Redis가 줄어듭니다
   - Redis 쓰기 작업에 대한 경합 조건 감소

## 영향을 받는 제품 및 버전

버전 2.3.3 이상을 사용하는 클라우드 인프라의 Adobe Commerce
Adobe Commerce(모든 배포 방법), 버전 2.3.5 이상

## 클라우드 배포를 위한 Redis 버전 업데이트

Adobe Commerce 2.3.3 이상을 사용하는 클라우드 인프라에 배포하는 Adobe Commerce의 경우 Redis 서비스를 Redis 버전 5.0으로 업그레이드하십시오. 지침은 클라우드 인프라 설명서의 Adobe Commerce 항목을 참조하십시오.

- [Redis 서비스 설정](https://devdocs.magento.com/cloud/project/services-redis.html)
- [서비스 버전 변경](https://devdocs.magento.com/cloud/project/services.html#change-service-version)

## 확장된 Redis 캐시 구현 구성

Adobe Commerce 2.3.5 이상의 경우 확장된 Redis 캐시 구현을 사용하도록 구성을 업데이트하십시오 `\Magento\Framework\Cache\Backend\Redis`.

### 클라우드 배포를 위한 구성

사용 `ece-tools` 2002.1.1 이상, 향상된 Redis 캐시를 설정 `REDIS_BACKEND` 환경 구성 파일의 배포 변수, `.magento.env.yaml`

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

자세한 내용은 [변수 배포 > `REDIS_BACKEND`](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) 을 참조하십시오.

>[!NOTE]
>
> 명령줄에서 을(를) 사용하여 로컬 클라우드 환경에 설치된 ece-tools 버전을 확인합니다. `composer show magento/ece-tools` 명령. 필요한 경우 [ece-tools 버전 업데이트](https://devdocs.magento.com/cloud/project/ece-tools-update.html).

>[!WARNING]
>
>작업 _not_ 클라우드 인프라 프로젝트에 대한 Redis 슬레이브 연결 구성 [스케일 아키텍처](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). 이로 인해 Redis 연결 오류가 발생합니다. 자세한 내용은 [Redis 구성 지침](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 에서 _클라우드 기반의 상거래_ 안내서.


### 온-프레미스 배포에 대한 구성

Adobe Commerce 온-프레미스 배포의 경우, `bin/magento:setup` 명령. 자세한 내용은 [기본 캐시에 Redis 사용](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## 추가 정보

- [Adobe Commerce 릴리스 v2.3.5 - 성능 향상](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#performance-boosts)
- [Redis 페이지 캐시](../../../configuration/cache/redis-pg-cache.md)


