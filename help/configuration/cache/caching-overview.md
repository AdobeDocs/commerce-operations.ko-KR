---
title: 캐싱 개요 및 구성 옵션
description: 백엔드 스토리지, 프론트엔드 구성 및 Varnish, Redis, Valkey 및 L2 캐시를 사용한 전체 페이지 캐싱을 포함하여 Adobe Commerce의 캐싱에 대해 알아봅니다.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 536
ht-degree: 0%

---

# 캐싱 개요 및 구성 옵션

Adobe Commerce은 여러 캐싱 계층을 사용하여 반복적인 처리를 줄이고 데이터베이스 로드를 줄이며 응답 시간을 개선합니다. 이러한 계층은 요청 및 에셋 전달의 다양한 지점에서 작동합니다.

- **응용 프로그램 캐싱**&#x200B;은(는) Commerce 캐시 형식을 사용하여 생성되거나 처리된 데이터를 저장합니다.
- **HTTP 전체 페이지 캐싱**&#x200B;은(는) Commerce 응용 프로그램에 도달하기 전에 전체 HTTP 응답을 저장합니다.
- **L2 캐싱**&#x200B;은(는) 공유 원격 캐시 저장소 앞에 있는 각 웹 노드에 로컬 캐시를 추가할 수 있습니다.
- **정적 콘텐츠 캐싱**&#x200B;을 사용하면 브라우저에서 CSS, JavaScript, 이미지 및 기타 정적 리소스를 다시 사용할 수 있습니다.

이 페이지에서는 이러한 레이어의 개념적인 개요와 구성 지침에 대한 링크를 제공합니다. 백 엔드 선택 사항, 구현 세부 정보 및 버전별 설정은 [캐시 백 엔드 옵션 및 저장소 참조](cache-options.md)를 참조하십시오.

## 레이어 캐싱

### 애플리케이션 캐싱

Commerce 애플리케이션 캐싱은 다음과 같이 구성됩니다.

>[!BEGINSHADEBOX]

캐시 유형 → 캐시 프론트엔드 → 캐시 백엔드

>[!ENDSHADEBOX]

**캐시 형식**&#x200B;은(는) 구성, 레이아웃, 블록 HTML 또는 전체 페이지 콘텐츠와 같이 캐시되는 데이터의 종류를 식별합니다. **캐시 프런트 엔드**&#x200B;는 하나 이상의 캐시 형식을 저장소에 연결합니다. **캐시 백 엔드**&#x200B;에서 저장소 구현을 제공합니다.

별도의 캐시 설정이나 저장소가 필요할 때 서로 다른 프론트엔드에 서로 다른 캐시 유형을 할당할 수 있습니다. 구성에 대한 자세한 내용은 [캐시 프론트엔드 및 형식 구성](cache-types.md)을 참조하십시오.

### 전체 페이지 HTTP 캐싱

HTTP 전체 페이지 캐싱은 HTTP 또는 CDN 계층에서 전체 응답을 저장합니다. 프로덕션 배포의 경우

- **Adobe Commerce 온-프레미스**—Adobe에서는 전체 페이지 캐싱에 [바니시](config-varnish.md)를 권장합니다. Vannish는 웹 서버 앞에서 역방향 프록시로 작동합니다.
- 클라우드 인프라의 **Adobe Commerce**&#x200B;은(는) Edge 및 전체 페이지 캐싱 레이어에 [Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly){target="_blank"}을(를) 사용합니다. 클라우드 인프라는 별도로 관리되는 Varnish 서비스를 사용하지 않습니다.

>[!NOTE]
>
>Commerce 애플리케이션 캐시 백엔드를 변경해도 Varnish 또는 Fastly가 구성되지 않습니다. 전체 페이지 HTTP 캐싱은 하위 수준 애플리케이션 캐시와 별도로 구성 및 관리됩니다.

### L2 캐싱

L2(2-level) 캐싱은 공유 원격 캐시 스토리지를 유지하면서 각 Commerce 웹 노드에 로컬 캐시를 추가합니다. 자주 액세스하는 데이터를 로컬로 제공할 수 있으므로 다중 노드 배포에서 원격 캐시와의 통신을 줄일 수 있습니다.

L2 구성 및 지원되는 구현은 Commerce 버전 및 배포 유형에 따라 다릅니다. 자세한 내용은 [L2 캐시 구성](level-two-cache.md)을 참조하십시오.

### 정적 콘텐츠 캐싱

Commerce은 URL에 배포 버전을 추가하여 CSS, JavaScript 및 이미지와 같은 정적 리소스에 대한 브라우저 캐싱을 향상시킬 수 있습니다. 콘텐츠가 변경되면 URL이 변경되어 브라우저가 이전 캐시된 사본을 사용하는 대신 새 리소스를 요청합니다.

## 배포별 구성

다음 구성 작업은 배포 유형에 따라 다릅니다.

| 작업 | 온-프레미스 | 클라우드 인프라 |
| --- | --- | --- |
| 애플리케이션 캐시 백엔드 | [캐시 백 엔드 옵션 및 저장소 참조](cache-options.md) | [Valkey 및 Redis 서비스 구성에 대한 모범 사례](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md) |
| HTTP 전체 페이지 캐싱 | [바니시 구성](config-varnish.md) | [Fastly 서비스 개요](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly) |

다음 작업은 모든 배포 유형에 적용됩니다.

- **캐시 형식과 프런트 엔드를 구성합니다** [캐시 프런트 엔드와 형식을 구성합니다](cache-types.md) 캐시 형식을 캐시 프런트 엔드와 연결합니다.
- **L2 캐싱 구성**—[L2 캐시 구성](level-two-cache.md).
- **정적 콘텐츠에 대한 브라우저 캐시 무효화 구성**—[정적 콘텐츠 서명 및 브라우저 캐시 무효화](static-content-signing.md).
