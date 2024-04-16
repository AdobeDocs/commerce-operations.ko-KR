---
title: 컨텐츠 보안 정책 개요
description: 컨텐츠 보안 정책을 사용하여 Adobe Commerce 또는 Magento Open Source 저장소의 보안 자세를 개선하는 방법을 알아봅니다.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# 컨텐츠 보안 정책 개요

CSP(콘텐츠 보안 정책)는 XSS(교차 사이트 스크립팅) 및 관련 데이터 삽입 공격을 감지하고 완화하는 데 도움을 주어 Adobe Commerce 설치에 대한 추가 방어 계층을 제공할 수 있습니다. 이 일반적인 공격 벡터는 웹 사이트에서 비롯되었다고 허위 주장을 하는 악성 콘텐츠를 삽입하여 작동합니다. 악성 콘텐츠가 로드되고 실행된 후 데이터의 무단 전송을 시작할 수 있습니다.

CSP는 신뢰할 수 있는 콘텐츠 리소스와 차단해야 하는 콘텐츠를 브라우저에 알려 주는 표준화된 지침 세트를 제공합니다. 신중하게 정의된 정책을 사용하면 CSP는 화이트리스트에 있는 리소스만 표시되도록 브라우저 콘텐츠를 제한할 수 있습니다.

## 구성

사이트 작업에 방해가 되지 않도록 CSP를 단계적으로 구현할 수 있습니다. CSP에는 두 가지 기본 작업 모드가 있습니다. `report-only mode` 및 `restrict mode`.

**보고서 전용 모드**: 브라우저는 정책 위반을 보고하라는 지시를 받지만 이를 집행하지는 않습니다. 요청된 리소스가 CSP를 위반할 때마다 브라우저는 결과 오류를 콘솔에 기록합니다. 그런 다음 콘솔 로그를 사용하여 각 위반의 원인을 조사할 수 있습니다.

모든 CSP 오류가 발생하면 이를 검토하고 필요한 모든 리소스를 화이트리스트에 추가할 때까지 정책을 구체화하는 것이 중요합니다. (으)로 전환해도 안전합니다. `restrict mode` 더 이상 오류가 발생하지 않는 경우입니다. 그렇지 않으면 잘못 구성된 CSP로 인해 브라우저에 콘솔 오류가 많은 빈 페이지가 표시될 수 있습니다. 올바르게 구성된 CSP를 사용하면 화이트리스트에 추가된 콘텐츠를 성능에 영향을 주지 않고 전달할 수 있습니다.

**제한 모드**: 모든 컨텐츠 정책을 적용하고 화이트리스트에 추가한 리소스로 게시를 제한하도록 브라우저에 지시합니다.

Adobe Commerce CSP 구현의 첫 번째 단계는 Adobe Commerce 2.3.5에서 도입되었으며 CSP를 사용할 수 있게 되었습니다. `report-only mode` 기본적으로.  Adobe Commerce 2.4.7 이상에서는 CSP가 `restrict-mode` 기본적으로 상점 및 관리 영역, 의 결제 페이지에 사용됩니다. `report-only` 다른 모든 페이지의 모드. 해당 CSP 헤더에 `unsafe-inline` 키워드 내부 `script-src` 지급 페이지에 대한 지시문입니다. 또한 화이트리스트에 추가한 인라인 스크립트만 허용됩니다.

CSP는 관리자가 아닌 서버에서 구성되므로 대부분의 판매자는 이를 제대로 구성하려면 시스템 통합자나 개발자의 도움이 필요합니다. 다음을 참조하십시오 [컨텐츠 보안 정책](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) 다음에서 _Commerce PHP 개발자 안내서_.


## 보고

기본적으로 CSP는 브라우저 콘솔에 오류를 보내지만 HTTP 요청으로 오류 로그를 수집하도록 구성할 수 있습니다. 또한 CSP 위반을 모니터링, 수집 및 보고하는 데 사용할 수 있는 여러 서드파티 서비스가 있습니다. CSP 위반은 관리자 또는 `config.xml` 사용자 지정 모듈에 대한 파일입니다.  다음을 참조하십시오 [보고서 URI 구성](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration) 다음에서 _Commerce PHP 확장 프로그램 개발자 안내서_.

[보고서 URI](https://report-uri.io/) 는 CSP 위반을 모니터링하고 결과를 대시보드에 표시하는 서비스입니다. 가맹점과 개발자 모두 CSP 위반이 발생할 때마다 이 서비스를 사용해 보고서를 받을 수 있다.
