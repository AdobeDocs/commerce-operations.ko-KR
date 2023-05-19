---
title: 사용자 정의 로깅
description: 사용자 정의 로깅을 사용하여 오류를 조사하는 방법에 대해 알아봅니다.
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# 사용자 정의 로깅 개요

로그는 시스템 프로세스에 대한 가시성을 제공합니다. 예를 들어, 오류 발생 시점 또는 오류의 원인이 무엇인지 이해하는 데 도움이 되는 디버깅 정보를 제공합니다.

이 항목에서는 파일 기반 로깅에 중점을 두고 있지만 Commerce에서는 데이터베이스에 로그를 저장할 수 있는 유연성도 제공합니다.

Adobe은 다음과 같은 이유로 중앙 집중식 애플리케이션 로깅을 사용할 것을 권장합니다.

- 애플리케이션 서버 이외의 서버에 로그를 저장할 수 있고 디스크 I/O 작업을 줄여 애플리케이션 서버 지원을 간소화합니다.

- 다음과 같은 특수 도구를 사용하여 로그 데이터를 보다 효과적으로 처리할 수 있습니다. [Logstash], [Logplex], 또는 [플루엔트]—운영 서버에 영향을 주지 않습니다.

   >[!INFO]
   >
   >Adobe은 특정 로깅 솔루션을 추천하거나 보증하지 않습니다.

## PSR-3 준수

다음 [PSR-3 표준][laminas] 는 로깅 라이브러리에 대한 일반적인 PHP 인터페이스를 정의합니다. PSR-3의 주요 목표는 라이브러리가 `Psr\Log\LoggerInterface` 간단하고 범용적인 방법으로 개체를 만들고 로그에 기록합니다.

이렇게 대체하면 애플리케이션 코드가 손상될 수 있으므로 걱정하지 않고 구현을 쉽게 교체할 수 있습니다. 또한 시스템의 향후 버전에서 로그 구현이 변경되는 경우에도 사용자 지정 구성 요소가 작동하도록 보장합니다.

## 독백

상거래 2는 PSR-3 표준을 준수합니다. 기본적으로 Commerce는 [독백]. 의 환경 설정으로 구현된 독백 `Psr\Log\LoggerInterface` Commerce 애플리케이션에서 [`di.xml`][di].

Monolog는 고급 로깅 전략을 구축 할 수있는 광범위한 핸들러를 가진 인기있는 PHP 로깅 솔루션입니다. 다음은 Monolog의 작동 방식에 대한 요약입니다.

독백 _로거_ 는 자체 세트가 있는 채널입니다. _핸들러_. Monolog에는 다음을 포함한 많은 처리기가 있습니다.

- 파일 및 syslog에 로그인
- 경고 및 이메일 보내기
- 로그 특정 서버 및 네트워크 로깅
- 개발 로그인(특히 FireBug 및 Chrome Logger와 통합)
- 데이터베이스에 로그인

각 처리기는 입력 메시지를 처리하고 전파를 중지하거나 체인의 다음 처리기로 컨트롤을 전달할 수 있습니다.

로그 메시지는 다양한 방법으로 처리할 수 있습니다. 예를 들어 모든 디버그 정보를 디스크의 파일에 저장하고, 로그 수준이 높은 메시지를 데이터베이스에 저장한 다음, 마지막으로 로그 수준이 &quot;위험&quot;인 메시지를 이메일로 보낼 수 있습니다.

다른 채널에는 다른 처리기 및 논리 세트가 있을 수 있습니다.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[플루엔트]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[독백]: https://github.com/Seldaek/monolog
