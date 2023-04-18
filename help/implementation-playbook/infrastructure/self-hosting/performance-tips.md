---
title: 자체 호스팅 Adobe Commerce 성능 팁
description: 고려해야 할 자체 호스팅 성능 팁 아이디어 및 개념과 모범 사례에 대해 알아봅니다.
landing-page-description: Adobe Commerce을 직접 호스팅할 때 고려해야 할 몇 가지 성능 팁 개념과 사항을 알아봅니다.
short-description: Adobe Commerce을 직접 호스팅하기 위한 전략 및 성능 팁 개념을 알아봅니다.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: ab099b2a8a353c2462424831cf8100e7e281b1be
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---


# 자체 호스팅 Adobe Commerce 성능 팁

유연하고 강력한 전자 상거래 플랫폼을 사용한다고 해서 성과를 희생하는 것은 아닙니다. Adobe Commerce이 도입된 이후 핵심 애플리케이션에 대한 다양한 개선 사항이 있었습니다. 버전 2.5.4에서 Adobe Commerce 엔지니어링 팀은 애플리케이션을 벤치마킹하기 위해 세트 테스트를 수행했습니다. 테스트 결과에 따르면 Adobe Commerce이 2억 4천만 SKU가 넘는 대용량 카탈로그를 처리할 수 있고 API 요청 시간이 평균 300ms이며 시간당 페이지 보기 수 및 주문 수가 200만 페이지 보기 수와 시간당 20만 8,000개의 주문 수에 도달하는 것이 매우 드문 것으로 나타났습니다.

로 이동하여 최신 벤치마크 결과를 확인합니다. [Experience League - Adobe Commerce - 구현 Playbook - 벤치마크](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

가능한 한 최적화를 유지하려면 사용자 지정 및 추가 복잡성을 프로젝트에 추가할 때 다음 표준을 따르십시오.

다음 섹션에서는 자체 호스팅 구현을 최적화하는 방법에 대한 고려 및 조언에 대해 설명합니다.

## 바니쉬

Varnish는 캐시가 있는 HTTP 역방향 프록시입니다. 복잡하게 보일 수 있지만, 소스에서 항목을 가져와야 하는 경우보다 더 빨리 요청이 반환되도록 하는 데 도움이 되는 빠른 응답이 나타납니다. 일부 버전의 Varnish를 사용하지 않고 Adobe Commerce 사이트를 실행하면 페이지 로드 속도가 느려지고 기타 주요 지표가 발생합니다. Varnish는 직접 설정하고 관리하는 것은 약간 어려울 수 있지만, Experience League에서 이 주제를 가지고 있습니다 [바니쉬 구성](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} Adobe Commerce을 사용하는 방법을 보다 잘 이해할 수 있도록 해줍니다. 아니면 클라우드 기반 솔루션을 사용하는 것입니다. 고려해야 할 사항이 많지만, Apple이 클라우드에서 Adobe Commerce을 위한 솔루션으로 선택되었습니다. VCL과 여러 패싯을 사용하는 페이터적이고 클라우드 기반의 버전입니다.

애플리케이션, 구성, 예산 및 기술 기능에 가장 적합한 솔루션을 찾는 것은 어려운 작업입니다. 클라우드 기반 옵션을 사용하면 관리, 구성, 서버 및 기타 인프라 구성 요소가 고려되는 한 모든 하드 부품이 사라집니다. 성능, 확장성, 처리량 및 기타 여러 주요 지표 때문에 클라우드 팀의 Adobe Commerce이 솔루션을 선택하고 있습니다.

Varnish와 관련된 프로젝트에 적합한 솔루션을 선택하면 고객을 위한 최상의 성능을 위해 자신을 설정하고 상거래 애플리케이션을 필요한 것보다 더 열심히 작업하지 않도록 할 수 있습니다.

## CDN

Adobe Commerce 프로젝트의 중요한 자산인 Varnish와 함께, 그 다음 줄은 CDN입니다. CDN은 Varnish와 함께 CSS에 대해 캐시된 인스턴스를 제공하여 Adobe Commerce 애플리케이션으로 전송되는 대역폭을 줄이는 데 도움이 되는 이미지와 같은 페이지 자산을 제공할 수 있습니다. 헤드리스 Adobe Commerce 사이트의 이점을 더 나아가 GraphQL 응답을 캐시할 수 있습니다. 일부 CDN은 이미지 최적화, 웹 애플리케이션 방화벽 및 기타 기능을 제공합니다.

Adobe Commerce on cloud에서는 Varnish 캐시에 페이스테리를 사용하지만 CDN으로도 사용하도록 선택했습니다. 이 단일 솔루션은 클라우드 고객의 Adobe Commerce에 유용한 경험을 제공하기 위해 다양한 기능을 제공합니다. Experience League에서 기본 서비스 개요를 읽을 수 있습니다 [기본 서비스 개요](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

CDN은 Adobe Commerce 프로젝트에 최적화된 보안 전달 컨텐츠를 제공합니다. 이 구성 요소가 프로젝트에 필수 구성 요소가 아닐 수 있는 경우 사이트 성숙과 방문자 수가 증가함에 따라 고려되어야 합니다. CDN을 제공하여 각 요청에서 제거되어 있기 때문에 인프라에 추가 하드웨어를 추가하거나 기존 인프라의 확장을 지연할 수 있습니다.

## 모듈 사용 안 함

사용하지 않는 모듈을 비활성화하는 것은 고려하되 가볍게 간주하지 마십시오. 이 기술을 사용하면 일부 요청의 오버헤드 및 처리 시간이 단축되지만, 고려해야 하는 부작용이 있습니다. 개발자가 기능을 만들 때 모듈을 사용할 수 있다고 가정하는 경우가 종종 있습니다. 비활성화된 모듈에서 발견된 일부 클래스를 사용하지 않도록 선택하지 않은 경우에는 이러한 작업이 종종 안전합니다.

기본 &quot;뉴스레터&quot;와 같은 모듈을 비활성화하는 것은 매우 일반적인 이벤트입니다. 이는 특히 스토어 소유자에게 뉴스레터를 관리하는 타사 회사가 있을 때 적용됩니다. 문제가 될 수 있는 경우는 타사 모듈이 설치된 경우이며, 일부 이유로 뉴스레터의 클래스를 사용하기로 했습니다. 이러한 우발적 종속성은 일부 초기 설치 및 테스트 중에 포착될 수 있지만, 이 타사 모듈을 유지할지 여부를 결정하고, 뉴스레터를 활성화한 다음 회귀 테스트를 통해 도입된 이상한 동작을 찾습니다. 또는 해당 타사 모듈을 교체해 줄 수 있습니까? 두 결정 모두 위험, 시간, 그리고 아마도 버그가 있다.

사용하지 않는 모듈을 비활성화하려면 먼저 단위, [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} 영향을 받을 수 있는 테스트 또는 API 요청을 로드합니다.

## 모든 끌어오기 요청에 대해 Adobe Commerce 및 PHP 코딩 표준을 준수해야 합니다.

Adobe Commerce에는 [코딩 표준](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. 이러한 기능은 소프트웨어 개발 유형에 관계없이 유사한 패턴, 스타일 및 예상 디자인을 따를 수 있도록 해줍니다. Adobe Commerce 코드 베이스에 기여할 때 이것은 요구 사항입니다. 그러나 사용자 정의 개발을 위한 이러한 방법을 따르도록 선택하면 현재 및 미래 모든 개발자를 위한 견고한 초석이 설정됩니다. 모든 가져오기 요청이 코드 표준을 전달하도록 할 때는 모든 사람이 동일한 일관된 개발 패턴을 이해하고 예상할 수 있도록 하는 데 도움이 됩니다.

Adobe Commerce 코딩 표준을 준수하기 위해 사용되는 다른 기본 코딩 표준은 PHP입니다. 개발자 가이드에서 따라야 하는 표준 및 수락할 수 있는 모든 장치를 명확히 정의해야 합니다. 그러나 다음에 있는 공개 유지 관리 안내서에 대한 대체 방법을 사용해야 합니다. [PHP-FIG](https://www.php-fig.org){target="_blank"}.

PSR-1 및 PSR-12에 대한 확고한 입장. 프로젝트에 참여하는 개발자가 따라야 하는지 확인하는 것은 이상한 구조화된 파일 및 패턴이 없는지 확인하는 데 도움이 됩니다. 또한 향후 개발자가 검토 중인 코드를 신속하게 읽고 이해할 수 있도록 해줍니다. 이러한 패턴과 코딩 표준을 잘 따르게 되면 향후 개발 노력을 보다 쉽게 읽고 신속하게 구현할 수 있습니다.

## 각 배포 후 로드 테스트 실행

각 배포 후 로드 테스트를 수행하는 것은 과도한 것으로 보일 수 있습니다. 그러나 이 방법을 따를 경우 새로 도입된 기능을 통해 성능 저하를 초래하는 기회를 추적하고 완화할 수 있습니다.

새 코드에서 성능이 저하되는 것을 감지하는 것 외에도 사이트의 주요 지표에 대한 내역 참조를 사용하면 새 도구 또는 변경 인프라가 활성화된 경우를 파악할 수 있습니다. 예를 들어, 호스팅 회사에 비용을 지불하여 환경을 최대화하고 예상한 성능 증가를 기대하기 전에 새 구성으로 스테이징 환경을 설정하고 로드 테스트를 실행하여 실제 결과가 무엇인지 확인할 수 있습니다.

이러한 테스트는 자동화되고 CI/CD 파이프라인의 일부로 포함될 수 있습니다. 이로 인해 규범에서 너무 많은 편차가 발생하는 경우 결과를 가져오고 피쳐의 병합을 차단하는 규칙을 제자리에 배치할 수도 있습니다. 이 데이터에 대한 사용 사례 수는 무한하지만, 이 프로세스를 시작하지 않으면 절대 그 가능성을 실현하지 못할 수 있습니다.

Adobe Commerce에는 Experience League에 있는 이 주제에 대한 적절한 목록이 있습니다 [성능 테스트 팁](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
