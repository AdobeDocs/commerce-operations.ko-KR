---
title: 업그레이드 체크리스트 우수 사례
description: 업그레이드 체크리스트를 만들어 사용하여 Adobe Commerce 및 Magento Open Source 업그레이드 전략을 계획하는 방법을 알아봅니다.
role: Leader
feature: Best Practices
feature-set: Commerce
source-git-commit: 644970b350c7591896f7c00d4c94661c76495c73
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---


# 업그레이드 체크리스트 우수 사례

이 체크리스트를 eCommerce 팀과의 연간 및 분기별 대화에서 사용합니다. 많은 회사들이 연간 예산과 로드맵에서 일합니다. 이러한 연례 토의를 통해, 비즈니스 목표 및 KPI에 맞는 방식과 함께 해당 연도의 플랫폼의 상태, 방향 및 업그레이드 전략에 대해 논의해야 합니다. 분기별 대화에서 작성한 연간 계획이 현재 상황과 일치하거나 그렇지 않을 경우 피벗 상태가 유지되는지 확인하십시오. 이 업그레이드 계획 체크리스트 의 목표는 연도 동안 성공적인 업그레이드 프로세스를 보장하기 위해 Adobe Commerce 업그레이드를 계획 및 예약하는 데 도움이 됩니다. 이 체크리스트는 다음 대상이 연간 계획 및 분기별 검토를 위해 사용하기 위한 것입니다.

- Director / 관리자 IT
- eCommerce Manager
- 솔루션 파트너/컨설턴트

>[!NOTE]
>
>성공적으로 업그레이드하는 기술 단계에 대한 자세한 내용은 [전체 업그레이드 사전 요구 사항](../../../upgrade/prepare/prerequisites.md) 을 참조하십시오.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 목표

▢ 현재 KPI를 검토하고 필요에 따라 조정합니다.

## 확장 및 사용자 지정

▢ 현재 모든 확장 및 사용자 지정 사항을 검토하고 비즈니스 요구 사항을 기반으로 해야 하는지 확인합니다.

▢ 최신 버전을 Adobe Commerce 버전으로 유지할 수 있는 좋은 추적 레코드가 없는 확장을 교체하는 것이 좋습니다.

## 팀

▢ 적절한 Adobe Commerce 인증 및 기술 세트를 갖춘 적절한 팀을 구성했는지 확인하십시오.

## 예산 및 시간

▢ Adobe Commerce 사용 [릴리스 일정](../../../release/schedule.md) 다음 업그레이드를 계획하고 미리 준비하려면 다음을 수행하십시오.

▢ 예상 요구 사항에 따라 어떤 버전을 채택할 것인지(전체 버전 또는 보안 전용) 설명합니다.

▢ 업그레이드에 필요한 예산과 팀 용량을 할당합니다.

## 타사 통합

▢ 해당 연도의 현재 Adobe Commerce 타사 통합 및 유지 관리 기간을 검토하고, 유지 관리 일정과 함께 업그레이드 작업을 정렬해 보십시오.

## 범위 및 배포 계획

▢ 조기 액세스 활동

- Partner 가 [Beta](../../../release/beta-program.md)
- 베타 릴리스 노트 검토.

▢ 예산, 일정, 범위에 대해 동의합니다.

▢ [업그레이드 호환성 도구](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢ 업그레이드를 사용하여 [사이트 전체 분석 도구](../../../tools/site-wide-analysis-tool/intro.md).

▢ 문서 종속성 및 PHP 또는 Elastic Search 버전과 같은 필요한 기술 스택 변경 사항입니다.

▢ Adobe Commerce 인증을 통해 프로젝트 팀을 모읍니다.

▢ 이해 당사자 통신 계획을 만듭니다.

▢ 다운타임이 예상되는 경우 유지 관리 기간을 계획합니다.

▢ 테스트 전략 검토 및 승인 Adobe Commerce 사용 고려 [테스트 프레임워크](https://developer.adobe.com/commerce/testing/) 또는 타사 자동화 세트에 포함되어 있습니다.

▢ 모든 확장 및 사용자 지정이 호환되는지 확인합니다.

▢ 출시 이후 Playbook을 검토하고 업데이트합니다. 업그레이드 중 또는 후에 문제가 발견된 경우 사용됩니다.

## 배포 후

▢ 성능, 주문 처리, 분석 등 문제에 대해 사이트를 모니터링합니다.

▢ Adobe Commerce 수행 [보안 검사](https://account.magento.com/scanner/dashboard/) 또는 기타 타사 스캔 및 잠재적 보안 취약점 검토

▢ 모든 이해 관계자와 함께 회고전을 수행하고 무엇이 잘 진행되었고 무엇이 개선되지 않았는지 그리고 어떻게 개선하는지 문서화합니다.

▢ 학습 내용을 통해 다음 업그레이드에 대한 계획을 수정합니다.
