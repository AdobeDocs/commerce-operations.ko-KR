---
title: 자체 호스팅 Adobe Commerce 성능 팁
description: 자체 호스팅 성능에 대해 알아보고 아이디어 및 개념과 고려해야 할 모범 사례에 대해 알아봅니다.
landing-page-description: Adobe Commerce을 직접 호스팅할 때 고려해야 할 몇 가지 성능 팁 개념과 사항에 대해 알아봅니다.
short-description: Adobe Commerce을 직접 호스팅하기 위한 전략 및 성능 팁 개념을 알아봅니다.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 95ff0c79-21d0-4514-991c-d88f616db68f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---

# 자체 호스팅 Adobe Commerce 성능 팁

유연하고 강력한 전자 상거래 플랫폼을 사용한다고 해서 성과를 희생해야 하는 것은 아닙니다. Adobe Commerce이 시작된 이후 핵심 애플리케이션에 대한 수많은 개선 사항이 있었습니다. 버전 2.5.4에서 Adobe Commerce 엔지니어링 팀은 애플리케이션을 벤치마킹하기 위해 세트 테스트를 수행했습니다. 테스트 결과는 Adobe Commerce이 2억 4천만 SKU가 넘는 대규모 카탈로그를 처리할 수 있으며 API 요청 시간이 평균 300ms에 달하며, 시간당 페이지 보기 수와 주문 수가 시간당 2백만 페이지 보기 수와 208,000건의 주문으로 놀라운 성과를 보인다는 것을 입증했습니다.

로 이동하여 최신 벤치마크 결과 확인 [Experience League - Adobe Commerce - 구현 플레이북 - 벤치마크](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

프로젝트에 사용자 정의 및 추가 복잡성을 추가할 때 최대한 최적의 상태를 유지하려면 다음 표준을 따르십시오.

다음 섹션에서는 자체 호스팅 구현을 최적화하는 방법에 대한 고려 사항 및 조언을 제공하는 항목을 다룹니다.

## 니스

Vannish 는 캐시가 있는 HTTP 역방향 프록시입니다. 복잡하게 보일 수 있지만, 그 결과는 소스에서 항목을 가져와야 하는 경우보다 요청이 더 빨리 반환되도록 하는 데 도움이 되는 빠른 응답입니다. 일부 버전의 Vannish 없이 Adobe Commerce 사이트를 실행하면 페이지 로드 및 기타 주요 지표가 느려집니다. 바니쉬는 자신을 설정하고 관리하는 데 다소 어려울 수 있지만, Experience League에 이 주제가 있습니다 [바니시 구성](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} Adobe Commerce 사용에 대한 이해를 높이십시오. 다른 방법은 클라우드 기반 솔루션을 사용하는 것입니다. 고려해야 할 사항이 많지만 Fastly는 클라우드에서 Adobe Commerce을 위한 솔루션으로 선택되었습니다. 그것은 VCL과 바니시의 많은 면을 사용하는 Fastly, 클라우드 기반의 버전입니다.

애플리케이션, 구성, 예산 및 기술 능력에 가장 적합한 솔루션을 찾는 것은 어려운 일입니다. 클라우드 기반 옵션을 사용하면 관리, 구성, 서버 및 기타 인프라 구성 요소를 고려하는 한 모든 하드 부품이 사라집니다. 이 솔루션은 성능, 확장성, 처리량 및 기타 주요 지표로 인해 Adobe Commerce on cloud 팀에 의해 선택되었습니다.

Varnish와 관련하여 프로젝트에 적합한 솔루션을 선택하면 고객을 위한 최상의 성능을 제공할 수 있으며 커머스 애플리케이션이 필요 이상으로 작동하지 않도록 보호할 수 있습니다.

## CDN

Varnish 는 Adobe Commerce 프로젝트의 중요한 자산이 될 뿐만 아니라 다음 라인에 CDN이 있습니다. Vannish와 함께 CDN은 CSS에 대해 캐시된 인스턴스를 제공하고, 이미지와 같은 페이지 자산을 제공하여 Adobe Commerce 애플리케이션으로 들어오는 대역폭을 줄일 수 있습니다. Headless Adobe Commerce 사이트의 이점을 더 많이 제공하는 GraphQL 응답을 캐시할 수 있습니다. 일부 CDN은 이미지 최적화, 웹 애플리케이션 방화벽 및 기타 기능을 제공합니다.

Adobe Commerce on cloud는 Fastly를 Varnish 캐시에 사용하지만 CDN으로도 사용하도록 선택했습니다. 이 단일 솔루션은 Adobe Commerce on cloud 고객에게 훌륭한 경험을 제공할 수 있는 다양한 기능을 제공합니다. Experience League에서 Fastly 서비스 개요를 읽을 수 있습니다 [Fastly 서비스 개요](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

CDN은 Adobe Commerce 프로젝트에 대해 최적화되고 안전한 게재 콘텐츠를 제공합니다. 이 구성 요소가 프로젝트에 필요하지 않은 경우 사이트가 완성되고 방문자의 수가 증가하면 고려 되어야 합니다. CDN을 제공하면 각 요청에서 제거된 로드로 인해 인프라에 하드웨어를 추가하거나 기존 인프라의 확장을 지연시킬 수 있습니다.

## 모듈 비활성화

사용하지 않는 모듈을 비활성화하는 것을 고려하되 가볍게 생각해서는 안 됩니다. 이 기법은 일부 요청에 대한 처리 시간과 약간의 오버헤드를 감소시키지만, 고려해야 하는 부작용이 있습니다. 종종 개발자가 기능을 만들 때 모듈을 사용할 수 있다고 가정하는 경우가 있습니다. 비활성화된 모듈에 있는 일부 클래스를 사용하도록 선택하지 않은 경우 이 문제가 종종 발생할 수 있습니다.

기본 &quot;뉴스레터&quot;와 같은 모듈을 비활성화하는 것은 매우 일반적인 이벤트입니다. 이것은 특히 가게 주인이 자신들의 뉴스레터를 관리하는 제3의 회사를 가지고 있을 때 더욱 그렇다. 이러한 문제가 발생할 수 있는 경우는 서드파티 모듈이 설치되어 있고 어떤 이유로든 뉴스레터의 클래스를 사용하기로 결정한 경우입니다. 이 우발적 종속성은 일부 초기 설치 및 테스트 중에 걸릴 수 있지만, 이 타사 모듈을 유지할지, 뉴스레터를 활성화할지, 도입된 이상한 동작이 있는지 사이트를 회귀 테스트할지 결정해야 합니다. 또는 해당 타사 모듈에 대한 대체 요소를 찾을 수 있습니까? 두 결정 모두 위험, 시간 및 버그가 있을 수 있습니다.

사용하지 않는 모듈을 비활성화하기 전에 장치, [MTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} 로드 테스트 또는 영향을 받을 수 있는 API 요청.

## 모든 가져오기 요청에 대해 Adobe Commerce 및 PHP 코딩 표준이 준수되어야 함

Adobe Commerce에는 [코딩 표준](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. 이를 통해 소프트웨어 개발 유형에 관계없이 유사한 패턴, 스타일 및 예상 디자인이 준수되도록 할 수 있습니다. Adobe Commerce 코드베이스에 기여할 때 이것이 필수 요건입니다. 그러나 사용자 정의 개발을 위해 이 방법을 따르도록 선택한다면 현재 및 미래 모두 모든 개발자를 위한 견고한 초석을 구축할 수 있습니다. 코드 표준을 전달하기 위해 모든 가져오기 요청이 필요한 경우에는 모든 사람이 동일한 일관된 개발 패턴을 이해하고 기대할 수 있도록 하는 데 도움이 됩니다.

Adobe Commerce 코딩 표준을 준수하기 위해 사용되는 다른 기반은 PHP 기본 코딩 표준입니다. 따라야 하는 표준 및 허용되는 모든 편차에 대해 개발자 안내서에 명확히 정의해야 합니다. 단, 다음 위치에 있는 공개적으로 유지 관리되는 안내서에 대한 대체 함수는 [PHP-FIG](https://www.php-fig.org){target="_blank"}.

PSR-1 및 PSR-12에 대한 확고한 입장. 프로젝트에 기여하는 개발자가 이러한 사항을 따르도록 하면 구조가 특이한 파일과 패턴이 없도록 할 수 있습니다. 이는 향후 개발자가 검토 중인 코드를 빠르게 읽고 이해할 수 있도록 도와줍니다. 이러한 패턴과 코딩 표준을 더 가까이 따라갈수록 향후 개발 노력이 읽기 쉬워지고 구현 속도가 빨라져야 함을 의미합니다.

## 각 배포 후 부하 테스트 실행

각 배포 후 부하 테스트를 수행하는 것은 과도한 것으로 보일 수 있습니다. 그러나 이 방법론을 따를 경우, 성능 감소를 야기하는 새롭게 도입된 기능에 대한 기회를 추적하고 완화할 수 있습니다.

새 코드에서 성능 저하를 감지하는 것 외에도, 사이트에서 주요 지표에 대한 기록 참조를 사용하면 새 도구 또는 변경 인프라가 활성화된 시점을 파악할 수 있습니다. 예를 들어 호스팅 회사에 환경 크기를 늘리기 위해 비용을 지불하고 기대하는 성능 향상을 얻기 전에 새 구성으로 스테이징 환경을 설정하고 부하 테스트를 실행하여 실제 결과가 무엇인지 확인할 수 있습니다.

이러한 테스트는 CI/CD 파이프라인의 일부로 자동화할 수 있습니다. 이로 인해 너무 많은 표준 편차가 발생하는 경우 결과를 가져와서 기능 병합을 잠재적으로 차단하는 규칙이 있을 수도 있습니다. 이 데이터에 대한 사용 사례의 수는 제한이 없지만, 이 프로세스를 시작하지 않으면 그 잠재력을 결코 파악할 수 없습니다.

Adobe Commerce에는 Experience League에서 발견된 이 주제에 대한 유용한 참고 자료가 있습니다. [성능 테스트 팁](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
