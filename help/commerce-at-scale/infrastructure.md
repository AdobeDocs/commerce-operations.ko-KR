---
title: Adobe Commerce 및 Adobe Experience Manager 인프라 정렬
description: Adobe Commerce 및 Adobe Experience Manager 인프라를 조정하여 허용 가능한 시간 초과 및 연결 제한을 설정합니다.
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# 인프라 정렬(시간 초과 및 연결 제한)

AEM 및 Adobe Commerce의 설정과 로드 밸런서와 같이 맞춤이 필요한 주변 인프라가 있으며, 이는 연결 제한 및 시간 제한 설정과 관련이 있습니다.

이러한 제한 간의 오정렬은 AEM 측에서 연결이 조절될 수 있는 반면 Adobe Commerce에서는 더 많은 연결을 처리할 수 있음을 의미합니다. 마찬가지로 시간 초과 설정의 경우 잘못 정렬하면 Adobe Commerce에서 요청을 계속 처리하는 동안 AEM 측에서 시간 초과 오류가 발생할 수 있습니다.

시간 초과 설정의 경우 로드 중에 503 시간 초과 오류가 표시되지 않도록 설정을 검토하고 정렬해야 합니다. 검토할 몇 가지 인프라 및 애플리케이션 시간 초과 설정이 있습니다.

![AEM에 대한 시간 초과 및 연결 제한을 설명하는 번호 매기기 다이어그램](../assets/commerce-at-scale/timeout-settings.svg)

## AEM 로드 밸런서

인프라 및 여러 Dispatcher/게시자에 AWS 애플리케이션 로드 밸런서가 있다고 가정할 경우 로드 밸런서에 대해 다음 설정을 고려해야 합니다.

1. Dispatcher가 로드 급증에서 불필요하게 일찍 서비스를 중단하지 않도록 게시자 상태 검사를 검토해야 합니다. 로드 밸런서 상태 검사의 시간 제한 설정은 게시자 시간 제한 설정과 일치해야 합니다.

   ![AEM 부하 분산 장치 상태 검사를 보여 주는 스크린샷](../assets/commerce-at-scale/health-checks.png)

1. Dispatcher 대상 그룹 고착성을 비활성화하고 라운드 로빈 로드 밸런싱 알고리즘을 사용할 수 있습니다. 이는 세션 고착성을 설정해야 하는 AEM 특정 기능이나 AEM 사용자 세션이 사용되지 않는다고 가정합니다. 사용자 로그인 및 세션 관리가 GraphQL을 통해 Adobe Commerce에서만 이루어진다고 가정합니다.

   ![AEM 세션 연결 특성을 보여 주는 스크린샷](../assets/commerce-at-scale/session-stickiness.png)

1. 세션 연결을 활성화하면 Fastly에 대한 요청이 캐시되지 않을 수 있습니다. 기본적으로 Fastly는 Set-Cookies 헤더가 있는 페이지를 캐시하지 않습니다. Adobe Commerce은 캐시 가능한 페이지에서도 쿠키를 설정하지만(TTL > 0), 기본 Fastly VCL은 Fastly 캐싱이 작동하도록 캐시 가능한 페이지에서 해당 쿠키를 제거합니다. 페이지가 캐싱하지 않는 경우 사용 중인 사용자 지정 쿠키를 확인하고 Fastly VCL을 업로드한 다음 사이트를 다시 확인하십시오.

## Dispatcher 시간 초과 설정

dispatcher &quot;renders&quot; 옵션의 /timeout 은 AEM 게시 인스턴스에 액세스하는 연결 시간 제한(밀리초)을 지정합니다. 시간 초과 설정을 처리하기 위한 별도의 로드 밸런서가 있는 경우 이 설정을 검토해야 하며 기본 설정인 &quot;0&quot;(무제한 시간 초과)을 사용해야 합니다.

인프라에 로드 밸런서가 없는 경우 대신 게시자의 GraphQL 시간 제한 설정과 일치하는 값을 사용하여 시간 제한 설정을 Dispatcher/timeout 설정에 지정해야 합니다.

## 게시자

게시자 GraphQL 연결 제한 및 시간 초과: 처음에는 Adobe Commerce CIF GraphQL 클라이언트 구성 팩토리 OSGI 설정의 최대 HTTP 연결 수를 현재 200개로 설정된 기본 Fastly 최대 연결 수로 설정해야 합니다. AEM 팜에 여러 게시자가 있더라도 Fastly 설정과 일치하도록 각 게시자에서 제한을 동일하게 설정해야 합니다. 그 이유는 예를 들어 연결된 디스패처를 팜에서 가져올 경우 경우에 따라 한 게시자가 다른 게시자보다 더 많은 트래픽을 처리할 수 있기 때문입니다. 이는 모든 트래픽이 나머지 단일 Dispatcher 및 게시자를 통해 라우팅됨을 의미합니다. 이 경우 단일 게시자는 모든 HTTP 연결이 필요할 수 있습니다.

&quot;기본 HTTP 메서드&quot;는 POST에서 GET으로 설정해야 합니다. GET 요청만 Adobe Commerce GraphQL 캐시에 캐시되므로 기본 메서드는 항상 GET으로 설정해야 합니다.

http 연결 시간 제한 및 http 소켓 시간 제한을 Fastly 시간 제한과 일치하는 값으로 설정해야 합니다.

다음 이미지는 Magento CIF GraphQL 클라이언트 구성 팩토리를 보여 줍니다. 여기에 표시된 설정은 예제일 뿐이며 사례별로 조정해야 합니다.

![Commerce integration framework 구성 설정의 스크린샷](../assets/commerce-at-scale/cif-config.png)

다음 이미지는 Fastly 백엔드 구성을 보여 줍니다. 여기에 표시된 설정은 예제일 뿐이며 사례별로 조정해야 합니다.

Fastly에 대한 Commerce 관리자 구성 설정의 ![스크린샷](../assets/commerce-at-scale/cif-config-advanced.png)
