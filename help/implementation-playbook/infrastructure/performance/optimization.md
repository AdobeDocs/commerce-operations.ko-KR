---
title: 성능 최적화
description: 성능 최적화와 Adobe Commerce 구현의 성능을 검토하기 위해 취해야 할 단계에 대해 모두 알아봅니다.
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 성능 최적화

공연은 중요한 주제이다. 사용자가 느리거나 응답하지 않는 사이트를 경험하는 경우 전환에 영향을 줍니다. Adobe Commerce on cloud infrastructure 구현의 성능을 최적화하려면 다음 단계를 수행하는 것이 좋습니다.

- 문제 평가
- 성능 측정
- 성능 향상에 중요한 시스템 부분 파악
- 시스템의 일부를 수정하여 병목 현상 제거
- 수정 후 성능 측정
- 더 좋다면 채택하거나 되돌리기

## 일반적인 성능 문제

느린 경험의 영향은 보통 두 가지 지표로 정의되며, 각 요인은 여러 가지 이유로 인해 발생할 수 있습니다.

TTFB(High time-to-first-byte)는 일반적으로 서버의 응답 속도를 정의하는 표시기로 간주됩니다. 시간은 요청을 처리하기 위한 소스 코드 실행에서 비롯될 뿐만 아니라 다음 요인의 영향을 받을 수 있습니다.

- DNS 조회
- DB 계층에서 느린 쿼리
- 각 애플리케이션 계층의 CPU 시간
- 메모리 제한
- I/O 대기는 파일 읽기 및 쓰기, 소켓을 통한 서비스 연결에 영향을 미칠 수 있습니다.
- 소프트웨어 설정(nginx, PHP, MySQL, Redis, Varnish)
- 네트워크 대역폭
- 잘못된 캐싱
- 잘못된 코드
- 잘못된 통합 접근 방식
- 느린 타사 서비스 응답 종속성
- 확장성 없는 아키텍처

느린 로드 리소스는 일반적으로 정적 리소스(CSS, JavaScript, 이미지, 비디오, 서드파티 Ajax 호출 응답)를 정의하는 표시기로 간주됩니다.

Adobe Commerce은 다음과 같은 기능을 통해 비즈니스에 맞게 확장할 수 있습니다.

![Adobe Commerce의 확장 가능한 기능을 보여 주는 다이어그램](../../../assets/playbooks/scalable-capabilities.svg)

커머스에서 규모를 이끄는 핵심 요인도 있어 전체 실적에도 영향을 미친다.

- 복잡하고 규모가 큰 제품 카탈로그
- 많은 수의 관리자
- 글로벌 상점
- 높은 변수 트래픽
- 터치포인트 확장
- 대량 트랜잭션

규모에 맞게 구축된 계층화 및 캐시 가능한 아키텍처의 경우 이 그래프를 참조로 사용할 수 있습니다.

![캐시 가능한 아키텍처에서 Adobe Commerce GraphQL API를 사용하는 방법을 보여 주는 다이어그램](../../../assets/playbooks/cacheable-architecture.svg)
