---
title: 지원 지표
description: 일반적인 지표를 사용하여 Adobe Commerce 구현에 대한 지원 및 유지 관리 작업을 모니터링합니다.
exl-id: a8171a08-3583-4c6a-bb18-158161be42d1
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# 지원 지표

다음 다이어그램은 L1 함수에 대해 수집 및 보고된 일반적인 지표/KPI를 보여줍니다.

![SLA 지표를 보여주는 다이어그램](../../assets/playbooks/sla-metrics.svg)

L2 서비스의 측정 및 보고(개선 사항 및 선택적 서비스)는 개발 프로젝트와 유사합니다. L2 팀의 성과 및 진도는 속도, 코드 품질, 테스트 효율성 및 생산성과 같은 지표로 측정됩니다.

| 주요 성능 측정 | UOM | 보고된 지표 |
|------------------------------|---------------------|------------------------------------------------------------------------------------|
| 속도 | 숫자 | 아니요. 그 팀이 전력 질주를 위해 할 수 있었던 |
| 스프린트 약정 효율성 | 백분율 | 총 아니요. 스프린트에 대해 헌신하는 이야기 포인트 vs. |
| 스프린트 다운 | 숫자 | 차트(보고서, 스프린트 전체에서 작업 완료를 추적합니다.) |
| 코드 품질 | 숫자, 백분율 | 스프린트에 대한 복잡성, LoC, 위반, 코드 적용 범위 |
| 요구 사항 변동성 | 숫자 | 요구 사항 수 변경/스프린트에 대한 총 요구 사항 수 |
| 결함 밀도 | 백분율 | [아니요. 발견된 유효한 결함/총 실행된 테스트 사례 수 .of]*100명 이상 |
| 테스트 효율성 | 백분율 | [유효한 결함 발생/(유효한 결함 발생 + 거부된 결함)]*100명 이상 |
| 생산성 | 번호(트렌드) | 스프린트/용량당 전달된 스토리 포인트 |
