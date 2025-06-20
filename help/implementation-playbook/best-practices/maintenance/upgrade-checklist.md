---
title: 업그레이드 체크리스트 모범 사례
description: 업그레이드 체크리스트를 만들고 사용하여 Adobe Commerce 업그레이드 전략을 계획하는 방법을 알아봅니다.
role: Leader
feature: Best Practices
exl-id: c9b644fa-290c-4f33-b5a7-19f7122ff08e
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# 업그레이드 체크리스트 모범 사례

전자 상거래 팀과의 연간 및 분기별 대화 중에 이 체크리스트를 사용하십시오. 많은 회사들이 연간 예산과 로드맵으로 일하고 있다. 이러한 연례 토론 중에 비즈니스 전반의 목표와 KPI에 어떻게 적합한지 그 해의 플랫폼 상태, 방향 및 업그레이드 전략에 대해 언급하는 것이 중요합니다. 분기별 대화 중에 만든 연간 계획이 현재 상황과 일치하는지, 그렇지 않은 경우 피벗되는지 확인하십시오. 이 업그레이드 계획 확인 목록의 목표는 해당 연도 동안 성공적인 업그레이드 프로세스를 보장하기 위해 Adobe Commerce 업그레이드를 계획하고 예약하는 데 도움이 되는 것입니다. 이 체크리스트는 연간 계획 및 분기별 검토에 다음 대상이 사용하기 위한 것입니다.

- Director / 관리자 IT
- eCommerce 관리자
- 솔루션 파트너/컨설턴트

>[!NOTE]
>
>업그레이드하기 위한 기술 단계에 대한 자세한 설명은 사용자 설명서에서 [업그레이드 필수 구성 요소 완료](../../../upgrade/prepare/prerequisites.md)를 참조하세요.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 목표

▢ 현재 KPI를 검토하고 필요에 따라 조정합니다.

## 확장 및 사용자 지정

▢ 모든 현재 확장 및 사용자 지정을 검토하고 비즈니스 요구 사항을 기반으로 이러한 확장이 계속 필요한지 확인합니다.

▢ Adobe Commerce 버전을 최신 상태로 유지한 실적이 좋지 않은 확장을 교체하는 것이 좋습니다.

## 팀

▢ 적절한 Adobe Commerce 인증 및 스킬 세트를 갖춘 올바른 팀이 있는지 확인하십시오.

## 예산 및 시간

▢ Adobe Commerce [릴리스 일정](../../../release/schedule.md)을(를) 사용하여 다음 업그레이드를 계획하고 미리 준비하십시오.

▢ 예상되는 요구 사항에 따라 채택할 버전(전체 또는 보안 전용)에 대해 논의합니다.

▢ 업그레이드에 필요한 예산과 팀 용량을 확보합니다.

## 타사 통합

▢ 현재 Adobe Commerce 타사 통합 및 해당 연도의 유지 관리 기간을 검토하고 유지 관리 일정에 맞게 업그레이드 작업을 조정할 것을 고려합니다.

## 범위 및 배포 계획

▢ 액세스 활동 만들기

- 파트너가 [Beta](../../../release/beta.md)에 참여함
- Beta 릴리스 노트 검토.

▢ 예산, 일정, 범위에 동의합니다.

▢0&rbrace;호환성 업그레이드 도구[&#128279;](../../../upgrade/upgrade-compatibility-tool/overview.md)를 실행하십시오.

▢ [사이트 전체 분석 도구](../../../tools/site-wide-analysis-tool/intro.md)에서 식별된 문제를 해결하려면 업그레이드를 사용하는 것이 좋습니다.

▢ 문서 종속성과 PHP 또는 Elastic Search 버전과 같은 기술 스택 변경 사항이 필요합니다.

▢ Adobe Commerce 인증을 보유한 프로젝트 팀을 수집합니다.

▢ 관련자 커뮤니케이션 계획 만들기

▢이 예상되는 경우 계획 유지 관리 창을 엽니다.

▢ 테스트 전략을 검토하고 승인합니다. Adobe Commerce [테스트 프레임워크](https://developer.adobe.com/commerce/testing/) 또는 타사 자동화 제품군을 사용하는 것이 좋습니다.

▢ 모든 확장 및 사용자 지정이 호환되는지 확인합니다.

▢ 업그레이드 도중 또는 업그레이드 후에 문제가 발견되는 경우 사용할 실행 후 플레이북을 검토하고 업데이트합니다.

## Post 배포

▢ 성능, 주문 처리, 분석 등의 문제에 대한 사이트 모니터링

▢ Adobe Commerce [보안 검사](https://account.magento.com/scanner/dashboard/) 또는 기타 타사 검사를 수행하고 잠재적인 보안 취약점을 검토하십시오.

▢ 모든 이해 당사자와 회고전을 수행하고 무엇이 잘 진행되었고 무엇이 실패했으며 어떻게 개선되었는지 문서화합니다.

▢ 학습 내용을 참조하여 다음 업그레이드 계획을 수정하십시오.
