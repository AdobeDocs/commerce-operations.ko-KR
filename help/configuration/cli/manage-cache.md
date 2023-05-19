---
title: 캐시 관리
description: 캐시 유형을 관리하고 캐시 상태를 확인합니다.
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---

# 캐시 관리

{{file-system-owner}}

## 캐시 유형

Commerce 2에는 다음과 같은 캐시 유형이 있습니다.

| 캐시 유형 &quot;친숙한&quot; 이름 | 캐시 유형 코드 이름 | 설명 |
|--- |--- |--- |
| 구성 | config | Commerce는 모든 모듈에서 구성을 수집하고 병합한 다음 병합된 결과를 캐시에 저장합니다. 또한 이 캐시에는 파일 시스템 및 데이터베이스에 저장된 저장소 관련 설정이 포함되어 있습니다. 구성 파일을 수정한 후 이 캐시 유형을 정리하거나 플러시합니다. |
| 레이아웃 | 레이아웃 | 컴파일된 페이지 레이아웃(즉, 모든 구성 요소의 레이아웃 구성 요소). 레이아웃 파일을 수정한 후 이 캐시 유형을 정리하거나 플러시합니다. |
| HTML 출력 차단 | block_html | 블록당 HTML 페이지 조각. 보기 레이어를 수정한 후 이 캐시 유형을 정리하거나 플러시합니다. |
| 컬렉션 데이터 | 컬렉션 | 데이터베이스 쿼리 결과. 필요한 경우 Commerce가 이 캐시를 자동으로 정리하지만 서드파티 개발자는 캐시의 모든 세그먼트에 데이터를 배치할 수 있습니다. 사용자 지정 모듈에서 Commerce에서 정리할 수 없는 캐시 항목을 생성하는 논리를 사용하는 경우 이 캐시 유형을 정리하거나 플러시합니다. |
| DDL | db_ddl | 데이터베이스 스키마. 필요한 경우 Commerce가 이 캐시를 자동으로 정리하지만 서드파티 개발자는 캐시의 모든 세그먼트에 데이터를 배치할 수 있습니다. 데이터베이스 스키마를 사용자 지정 변경한 후 이 캐시 유형을 정리하거나 플러시합니다. 즉, Commerce가 자체적으로 만들지 않는 업데이트입니다. 데이터베이스 스키마를 자동으로 업데이트하는 한 가지 방법은 `magento setup:db-schema:upgrade` 명령입니다. |
| 컴파일된 구성 | compiled_config | 컴파일 구성 |
| 엔티티 속성 값(EAV) | eav | EAV 속성과 관련된 메타데이터(예: 스토어 레이블, 관련 PHP 코드에 대한 링크, 속성 렌더링, 검색 설정 등). 일반적으로 이 캐시 유형을 정리하거나 플러시할 필요가 없습니다. |
| 페이지 캐시 | full_page | 생성된 HTML 페이지. 필요한 경우 Commerce가 이 캐시를 자동으로 정리하지만 서드파티 개발자는 캐시의 모든 세그먼트에 데이터를 배치할 수 있습니다. HTML 출력에 영향을 주는 코드 수준을 수정한 후 이 캐시 유형을 정리하거나 플러시합니다. 캐싱 HTML이 성능을 크게 향상시키므로 이 캐시를 활성 상태로 유지하는 것이 좋습니다. |
| 반사 | 반사 | Webapi 모듈과 고객 모듈 간의 종속성을 제거합니다. |
| 번역 | 번역 | 모든 모듈에서 번역을 병합한 후 병합 캐시가 정리됩니다. |
| 통합 구성 | config_integration | 컴파일된 통합. 통합을 변경하거나 추가한 후 이 캐시를 지우거나 플러시합니다. |
| 통합 API 구성 | config_integration_api | 스토어 통합의 컴파일된 통합 API 구성입니다. |
| 웹 서비스 구성 | config_webservice | 웹 API 구조 캐싱. |
| 고객 알림 | customer_notification | 사용자 인터페이스에 표시되는 임시 알림입니다. |

## 캐시 상태 보기

캐시의 상태를 보려면

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

샘플은 다음과 같습니다.

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
                           eav: 1
         customer_notification: 1
                     full_page: 1
            config_integration: 1
        config_integration_api: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

## 캐시 유형 활성화 또는 비활성화

이 명령을 사용하면 모든 캐시 유형 또는 지정한 캐시 유형만 활성화하거나 비활성화할 수 있습니다. 캐시 유형을 비활성화하면 캐시를 플러시하지 않고도 변경 결과가 표시되므로 개발 중에 유용합니다. 그러나 캐시 유형을 비활성화하면 성능에 부정적인 영향을 줍니다.

>[!INFO]
>
>버전 2.2부터 프로덕션 모드에서 Commerce를 실행하는 동안에는 명령줄을 사용해서만 캐시 유형을 활성화하거나 비활성화할 수 있습니다. 개발자 모드에서 Commerce를 실행하는 경우 명령줄을 사용하거나 수동으로 캐시 유형을 활성화하거나 비활성화할 수 있습니다. 이렇게 하기 전에 수동으로 다음을 수행해야 합니다. `<magento_root>/app/etc/env.php` 에서 쓰기 가능 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).

청소할 수 있습니다(청소라고도 함) _플러시_ 또는 _새로 고침_) 명령줄 또는 관리자를 사용하는 캐시 유형입니다.

명령 옵션:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

생략된 위치 `[type]` 모든 캐시 유형을 동시에 활성화하거나 비활성화합니다. 다음 `type` 옵션은 공백으로 구분된 캐시 유형 목록입니다.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

캐시 유형 및 해당 상태를 나열하려면

```bash
bin/magento cache:status
```

예를 들어 전체 페이지 캐시와 DDL 캐시를 비활성화하려면 다음을 수행합니다.

```bash
bin/magento cache:disable db_ddl full_page
```

샘플 결과:

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>캐시 유형을 활성화하면 해당 캐시 유형이 자동으로 지워집니다.

>[!INFO]
>
>버전 2.3.4부터 Commerce는 검색될 때 모든 시스템 EAV 속성을 캐시합니다. 이 방식으로 EAV 속성을 캐시하면 DB에 대한 삽입/선택 요청의 양이 줄어들기 때문에 성능이 향상됩니다. 그러나 캐시 네트워크 크기도 증가합니다. 개발자는 다음을 실행하여 사용자 지정 EAV 속성을 캐시할 수 있습니다. `bin/magento config:set dev/caching/cache_user_defined_attributes 1` 명령입니다. 에 있는 동안 관리자로부터 수행할 수도 있습니다. [개발자 모드](../bootstrap/application-modes.md) 설정별 **스토어** > 설정 **구성** > **고급** > **개발자** > **캐싱 설정** > **캐시 사용자 정의 속성** 끝 **예**.

## 캐시 유형 정리 및 플러시

캐시에서 오래된 항목을 제거하려면 _clean_ 또는 _플러시_ 캐시 유형:

- 캐시 유형을 정리하면 활성화된 Commerce 캐시 유형에서만 모든 항목이 삭제됩니다. 즉, 이 옵션은 Commerce에서 사용하는 캐시만 정리하므로 다른 프로세스나 애플리케이션에는 영향을 주지 않습니다.

   비활성화된 캐시 유형은 정리되지 않습니다.

   >[!TIP]
   >
   >Magento Open Source 또는 Adobe Commerce 버전을 업그레이드하거나, Magento Open Source에서 Adobe Commerce으로 업그레이드하거나, Adobe Commerce용 B2B 또는 임의의 모듈을 설치한 후 항상 캐시를 정리하십시오.

- 캐시 유형을 플러시하면 캐시 저장소가 지워지므로 동일한 저장소를 사용하는 다른 프로세스 애플리케이션에 영향을 줄 수 있습니다.

캐시를 지우려고 했지만 여전히 격리할 수 없는 문제가 있는 경우 캐시 유형을 플러시합니다.

명령 사용:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

위치 `[type]` 는 공백으로 구분된 캐시 유형 목록입니다. 생략 `[type]` 모든 캐시 유형을 동시에 정리하거나 플러시합니다. 예를 들어 모든 캐시 유형을 플러시하려면 다음을 입력합니다.

```bash
   bin/magento cache:flush
```

샘플 결과:

```terminal
   Flushed cache types:
   config
   layout
   block_html
   collections
   reflection
   db_ddl
   compiled_config
   eav
   customer_notification
   config_integration
   config_integration_api
   full_page
   config_webservice
   translate
```

>[!TIP]
>
>관리자에서 캐시 유형을 정리하고 플러시할 수도 있습니다. 다음으로 이동 **시스템** > **도구** > **캐시 관리**. **캐시 저장소 초기화** 은(는) 와 동일합니다. `bin/magento cache:flush`. **Magento 캐시 초기화** 은(는) 와 동일합니다. `bin/magento cache:clean`.
