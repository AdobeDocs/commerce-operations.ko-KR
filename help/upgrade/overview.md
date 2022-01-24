---
title: 업그레이드 프로세스 개요
description: Adobe Commerce 및 Magento Open Source 프로젝트를 업그레이드하여 저장소를 안전하게 유지하고 효율적으로 운영하는 방법을 알아봅니다.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 0%

---


# 업그레이드 프로세스 개요

Adobe Commerce 또는 Magento Open Source 프로젝트를 업그레이드하려면 저장소가 안전하게 유지되고 PCI 규정을 준수하고 최대의 효율로 작동할 수 있도록 하는 것이 중요합니다. 업그레이드를 준비할 때 주요 고려 사항을 안내하기 위해 이 안내서를 개발했습니다.

이 안내서에서는 일반적인 Adobe Commerce/Magento Open Source 업그레이드 여정 및 해당 여정을 따르는 모범 사례에 대한 개요를 제공합니다. 또한 Adobe Commerce/Magento Open Source 버전 2.4.4로 업그레이드하기 위한 시기 적절한 예와 단계별 지침과 함께 업그레이드 프로세스에 대한 기술 세부 사항도 설명합니다. 2.4.4 패치 릴리스는 2022년 3월 8일에 GA되므로 이 업그레이드를 일찍 준비하는 것이 중요합니다 [수명 종료(EOL)](https://devdocs.magento.com/release/lifecycle-policy.html) 날짜는 2022년 2.3 라인과 버전 2.4.0에서 2.4.3에 모두 근접하고 있습니다. 마지막으로, Adobe에서는 업그레이드 프로세스를 보다 효율적으로 수행할 수 있도록 계획 리소스와 업그레이드 도구를 제공합니다.

## 이 가이드는 누구인가요?

이 안내서의 target 대상에는 다음이 포함됩니다.

### Ecommerce Managers and Technical Directors

이 안내서는 이러한 역할을 수행하는 고객이 업그레이드 여정, 정기적으로 업그레이드의 중요성, 업그레이드를 가장 잘 계획하고 준비하는 방법을 이해하는 데 도움이 됩니다.

### 운영 및 개발 팀

이 안내서는 이러한 팀이 2.4.4(또는 모든 버전의 Adobe Commerce/Magento Open Source)으로 업그레이드하는 데 필요한 기술 단계와 프로세스를 보다 쉽고 빠르고 저렴하게 만드는 데 사용할 수 있는 도구를 학습하도록 도와줍니다.

## 업그레이드 프로세스 설명

Adobe Commerce/Magento Open Source을 선택한 이유 중 하나는 다음과 같습니다.

- 광범위한 기본 기능 세트
- 핵심 코드와는 별도로 제공되는 SaaS 기능
- 강력한 Marketplace 확장 기능 제공
- 기업의 요구 사항에 가장 잘 맞게 사이트를 사용자 지정할 수 있도록 무한 유연성을 보장하는 고유한 기능입니다.

그러나 확장성이 뛰어나고 사용자 정의 가능한 제품으로, 사용자 정의 사항이 Best Practice로 코딩되지 않을 때 잠재적인 업그레이드 문제가 발생할 수 있으므로 업그레이드 비용이 예상보다 높습니다.

_따라서... 업그레이드 이유는 무엇입니까?_

업그레이드를 통해 고객은 빠르게 변화하는 eCommerce 업계에서 민첩하게 비즈니스를 유지하고 판매 및 전환을 극대화하는 최신 기능과 항상 호환될 수 있습니다. 또한, 일반적인 유지 관리 계획에 업그레이드를 포함시키는 것은 사용자의 스토어를 안전하게 유지하고, PCI 규정을 준수하며, 최상의 효율로 작동할 수 있도록 하는 데 매우 중요합니다.

### 보안

보안은 오래된 소프트웨어에 발생한 보안 사고의 83%가 발생함에 따라 업그레이드할 수 있는 주요 이유 중 하나입니다. 에 따라 [IBM](https://www.ibm.com/security/data-breach)즉, 데이터 위반의 평균 비용은 386만 달러이며, 업그레이드를 통해 이러한 위험을 줄일 수 있는 비용보다 훨씬 높습니다. Adobe은 1년 동안 스토어를 안전하게 유지하는 두 가지 방법을 제공합니다.

- **패치 릴리스**—보안, 성능, 품질 및 우선 순위가 높은 버그 수정 사항을 포함합니다.
- **보안 패치 릴리스**—사이트 보안을 유지하고 쉽게 구현할 수 있도록 수정 사항 및 개선 사항이 포함되어 있습니다.

### 성능

Performance is another top reason for upgrading. According to [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), the first five seconds of load time have a significant effect on conversion rates and every second of latency thereafter has a –4.4% impact. 페이지 속도가 선도적인 SEO 순위 지표라는 사실과 함께 사이트 성능이 유지 관리 및 정기적으로 향상되는 중요한 요소인 이유를 보여줍니다. 각 패치 릴리스에는 성능 향상이 포함되어 있으므로 새로운 릴리스를 통해 성장 계획을 지원하고 비즈니스 경쟁력을 유지할 수 있습니다.

### 지연 비용

플랫폼 업그레이드를 지연하거나 지연하는 문제는 종종 즉시 발생할 수 있습니다. 그러나, 오래된 버전의 소프트웨어를 실행하는 데 드는 실제 비용은 훨씬 더 크고 비즈니스에 지속적인 영향을 줄 수 있습니다.

이는 직관적이지 않을 수 있지만, 정기적인 플랫폼 업데이트를 수행하는 것은 지연으로 인한 누적된 기술 부채 때문에 자주 업데이트를 수행하는 것보다 전반적인 노력이 덜 필요합니다. Adobe는 최근 소매 상점을 운영하고 있으며 드물게 일관되지 않고(연간 또는 이상) 업그레이드를 수행하는 파트너와 작업했습니다. 업그레이드 방식을 전환하고 12개월 동안 Adobe이 권장하는 일반 업그레이드 경로를 따르는 방식으로 전환함으로써, 파트너는 4주 동안의 누적 개발 시간, 노력 및 관련 비용을 고객에게 절감했으며, 이러한 모든 것들은 비즈니스 성장을 이끄는 이니셔티브로 리디렉션되었습니다.

![](../assets/upgrade-guide/waiting-is-not-a-winning-strategy.jpg)

업데이트가 정기적으로 수행되면 변경 사항이 증가하므로 해당 업그레이드 작업에도 이러한 내용이 반영됩니다. 플랫폼 업데이트가 긴 기간 동안 지연되면 더 많은 관련 프로세스가 될 수 있습니다. 또한 [Marketplace](https://marketplace.magento.com/) 및 기타 모든 타사 통합도 영향을 받을 수 있습니다. 마지막으로, 조사, 계획 및 지연된 업그레이드를 수행하는 데 걸리는 시간은 모두 연장되어, 피할 수 있는 노력과 비용이 추가됩니다.

디지털 상거래 공간의 지속적인 성장은 기업에 더 빨리, 더 자주, 그리고 예측할 수 없는 방식으로 발전하라는 압력을 가했습니다. 고객 구매 행동을 지속적으로 예측하지 못하면 가장 규모가 큰 브랜드 사이에서도 동일한 결과를 얻을 수 있습니다. 성능 및 가동 시간 없이 모든 터치포인트에 강력하고 개인화된 경험을 제공할 수 있어야 합니다. 세계 경쟁업체들을 앞서기 위해서는 제한 없이 빠르게 혁신을 이룰 수 있어야 합니다. 업그레이드를 통해, 향후 비즈니스를 정리하고 보다 나은 서비스 동적 고객 요구 사항을 충족하도록 설정하는 것입니다.

## 2022년 릴리스 일정

Adobe은 [릴리스 일정](https://devdocs.magento.com/release/) 상인의 계획 프로세스를 용이하게 하고 각 패치 릴리스 주기를 업그레이드할 것을 권장합니다. PCI 규정을 준수하려면 가맹점은 최신 패치 또는 보안 패치를 사용해야 합니다. 다음 타임라인은 2022년의 주요 릴리스 및 EOL 이벤트를 보여줍니다.

![](../assets/upgrade-guide/2022-release-timeline.svg)

주목할 중요한 이벤트는 다음과 같습니다.

- 2.3.x 지원은 2022년 4월 이후 종료됩니다
- 2.4.0 to 2.4.3 (based on PHP 7.4) reaches end of quality support in November ’22, when PHP 7.4 reaches EOL
- Based on these two events above, it is important to upgrade to version 2.4.4 or higher by November ‘22
- In line with the Adobe Commerce [lifecycle policy](https://devdocs.magento.com/release/lifecycle-policy.html), versions 2.4.4 and 2.4.5 are supported until Nov ’24