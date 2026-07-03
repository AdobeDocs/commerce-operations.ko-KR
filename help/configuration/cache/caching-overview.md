---
title: 캐싱 개요 및 구성 옵션
description: 백엔드 스토리지, 프론트엔드 구성 및 Varnish, Redis, Valkey 및 L2 캐시를 사용한 전체 페이지 캐싱을 포함하여 Adobe Commerce의 캐싱에 대해 알아봅니다.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 7171e5abfad69ad0f2d3f4c4b5eb57c13d07feb4
workflow-type: tm+mt
source-wordcount: 593
ht-degree: 0%

---

# 캐싱 개요 및 구성 옵션

Adobe Commerce은 다중 계층 캐싱 아키텍처를 기반으로 데이터베이스 로드를 줄이고 중복 처리를 최소화하며 페이지 전달을 가속화합니다. 애플리케이션 수준에서 Commerce은 구성, 레이아웃, 블록 HTML 및 컬렉션과 같은 12개 이상의 [캐시 유형](../cli/manage-cache.md#clean-and-flush-cache-types)을 유지 관리하며, 각 캐시 유형은 [Redis](config-redis.md) 또는 [Valkey](config-valkey.md)과(와) 같은 전용 스토리지 백엔드로 라우팅할 수 있습니다. 온-프레미스 배포의 전체 페이지 캐싱의 경우 [Vannish](config-varnish.md)을(를) 강력히 권장합니다. Commerce on Cloud 배포는 Fastly를 사용합니다. [L2 캐싱](level-two-cache.md) 및 [정적 콘텐츠 서명](static-content-signing.md)과 같은 추가 계층은 높은 트래픽, 다중 노드 배포의 성능을 더욱 향상시킵니다.

이 안내서에서는 각 캐싱 레이어의 작동 방식을 설명하고 배포 요구 사항에 맞게 프론트엔드, 백엔드 및 고급 옵션을 구성하는 방법을 보여 줍니다.

## 캐싱 프론트엔드

캐시 프론트엔드는 Commerce과 캐시 스토리지 백엔드 간의 인터페이스입니다. 각각 다른 백엔드 설정을 사용하는 여러 프론트엔드를 정의한 다음 각 프론트엔드에 특정 [캐시 유형](../cli/manage-cache.md#clean-and-flush-cache-types)을(를) 할당할 수 있습니다. 구성에 대한 자세한 내용은 [캐시 프론트엔드 및 형식 구성](cache-types.md)을 참조하십시오.

## 백 엔드 캐싱

캐시 백엔드는 캐시된 데이터의 기본 스토리지 메커니즘입니다. Commerce은 기본 파일 시스템 백엔드를 제공하지만, 향상된 성능 및 확장성을 위해 Redis 또는 Valkey와 같은 다른 백엔드를 구성할 수 있습니다. 사용 가능한 옵션에 대한 자세한 내용은 [캐시 백 엔드 옵션](cache-options.md)을 참조하십시오.

## 바니시를 사용한 전체 페이지 캐싱

[바니시 캐시](config-varnish.md)는 메모리에 전체 페이지를 캐시하는 HTTP 가속기입니다. 온-프레미스 프로덕션 환경의 경우 기본 제공 전체 페이지 캐시보다 훨씬 빠르기 때문에 Adobe에서는 Vannish를 강력히 권장합니다. 클라우드 환경의 Commerce은 전체 페이지 캐싱에 바니시 대신 [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly)를 사용합니다.

>[!NOTE]
>
>Vannish는 웹 서버 앞에서 역방향 프록시로 작동하므로 Commerce 캐시 백엔드 구성을 변경할 필요가 없습니다.

## L2(2단계) 캐싱

[L2 캐시](level-two-cache.md)는 원격 캐시(Redis 또는 Valkey)를 신뢰할 수 있는 소스로 사용하는 동안 각 웹 노드에 로컬로 캐시 데이터를 저장합니다. 이렇게 하면 웹 노드와 원격 캐시 간의 네트워크 트래픽이 감소하여 트래픽이 많은 사이트의 성능이 향상됩니다.

## 정적 콘텐츠 캐싱

[정적 콘텐츠 서명](static-content-signing.md)은(는) 배포 버전을 파일 URL에 포함시켜 정적 리소스(CSS, JavaScript, 이미지)에 대한 브라우저 캐시를 무효화합니다.

## 캐싱 용어

[!DNL Commerce]은(는) 다음 캐싱 용어를 사용합니다.

- **Frontend** — [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend)에서 구현한 캐시 저장소에 대한 인터페이스 또는 게이트웨이입니다.
- **캐시 형식** — [!DNL Commerce]&#x200B;(예: `config`, `layout`, `block_html`, `full_page`) 또는 [사용자 지정 형식](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/)과(와) 함께 제공되는 기본 제공 형식 중 하나입니다.
- **백엔드** — [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)에서 구현한 [캐시 저장소](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)의 세부 정보를 지정합니다.
- **두 수준 백 엔드** - 로컬(빠른) 캐시와 원격(공유) 캐시, 이렇게 두 백 엔드에 캐시 레코드를 저장합니다. [L2 캐시 구성](level-two-cache.md)을 참조하세요.

## 구성 옵션

프론트엔드 간 매핑 및 캐시 구성 구문의 경우:

**온-프레미스**—캐시 구성이 다음 두 파일에 저장됩니다.

- `<magento_root>/app/etc/di.xml` — 전역 종속성 삽입 구성입니다. 제공된 `default` 캐시 프런트 엔드를 변경하려면 이 파일을 수정하십시오.
- `<magento_root>/app/etc/env.php` — 환경별 구성입니다. 이 파일을 수정하여 사용자 지정 캐시 프론트엔드를 구성합니다. 이 파일은 `di.xml`의 해당 구성을 재정의합니다.

자세한 내용은 다음을 참조하십시오.

- [캐시 프런트 엔드와 형식 구성](cache-types.md)—캐시 프런트 엔드를 특정 캐시 형식과 연결합니다.
- [캐시 백 엔드 옵션](cache-options.md)—백 엔드 옵션 참조

**클라우드의 Adobe Commerce**—`.magento.env.yaml`에서 `CACHE_CONFIGURATION`을(를) 사용하여 캐싱을 구성합니다. [Redis 및 Valkey 서비스 구성에 대한 모범 사례](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md)를 참조하세요.
