---
title: 사용자 지정 로깅
description: 사용자 지정 로깅을 사용하여 오류를 조사하는 방법을 알아봅니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# 사용자 지정 로깅 개요

로그는 시스템 프로세스에 대한 가시성을 제공합니다. 예를 들어, 오류 발생 시기 또는 오류로 이어지는 사항을 이해하는 데 도움이 되는 디버깅 정보입니다.

이 항목에서는 Commerce에서 데이터베이스에 로그를 저장할 수 있는 유연성을 제공하지만 파일 기반 로깅에 중점을 둡니다.

Adobe은 다음과 같은 이유로 중앙 집중식 응용 프로그램 로깅을 사용하는 것이 좋습니다.

- 애플리케이션 서버 이외의 서버에 로그를 저장할 수 있고 디스크 I/O 작업을 줄일 수 있으므로 애플리케이션 서버의 지원이 간단해집니다.

- 따라서 다음과 같은 특별한 도구를 사용하여 로그 데이터를 보다 효과적으로 처리할 수 있습니다 [Logstash], [Logplex], 또는 [유체]—프로덕션 서버에 영향을 주지 않음

   >[!INFO]
   >
   >Adobe은 특정 로깅 솔루션을 추천하거나 승인하지 않습니다.

## PSR-3 규정 준수

다음 [PSR-3 표준][laminas] 는 라이브러리 로깅을 위한 일반적인 PHP 인터페이스를 정의합니다. PSR-3의 주요 목표는 라이브러리가 `Psr\Log\LoggerInterface` 간단하고 보편적으로 개체 및 로그 작성

이렇게 하면 애플리케이션 코드가 손상될 수 있으므로 걱정 없이 구현을 쉽게 교체할 수 있습니다. 또한 향후 버전의 시스템에서 로그 구현이 변경될 경우에도 사용자 지정 구성 요소가 작동되도록 보장합니다.

## 모노로그

Commerce 2는 PSR-3 표준을 준수합니다. 기본적으로 Commerce는 [모노로그]. 기본 설정으로 구현된 모노로그 `Psr\Log\LoggerInterface` 상거래 응용 프로그램에서 [`di.xml`][di].

Monolog는 고급 로깅 전략을 구축할 수 있는 다양한 핸들러가 포함된 널리 사용되는 PHP 로깅 솔루션입니다. 다음은 Monolog 작동 방식에 대한 요약입니다.

독록 _logger_ 는 자체 설정된 채널을 갖는 채널입니다 _핸들러_. Monolog에는 다음을 포함한 많은 핸들러가 있습니다.

- 파일 및 syslog 로그
- 경고 및 이메일 보내기
- 특정 서버 및 네트워크 로깅 로그
- 개발 로그인(FireBug 및 Chrome Logger와 통합)
- 데이터베이스에 로그인합니다.

각 처리기는 입력 메시지를 처리하고 전달을 중지하거나 체인의 다음 처리기에 컨트롤을 전달할 수 있습니다.

로그 메시지는 다양한 방법으로 처리할 수 있습니다. 예를 들어, 모든 디버그 정보를 디스크의 파일에 저장하고, 로그 수준이 높은 메시지를 데이터베이스에 넣은 다음, 마지막으로 e-메일을 통해 로그 수준이 &quot;중요&quot;인 메시지를 보낼 수 있습니다.

다른 채널에는 다른 핸들러 및 논리 세트가 있을 수 있습니다.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[유체]: http://www.fluentd.org
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[모노로그]: https://github.com/Seldaek/monolog
