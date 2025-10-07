---
title: 캐시 관리
description: Adobe Commerce CLI 명령을 사용하여 캐시 유형을 관리하고 캐시 상태를 보는 방법에 대해 알아봅니다. 캐시 관리 및 최적화 기술을 살펴보십시오.
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# 캐시 관리

{{file-system-owner}}

## 캐시 유형

Adobe Commerce 캐시 관리 시스템을 사용하여 사이트의 성능을 향상시킬 수 있습니다. 이 항목에서는 Commerce 애플리케이션 서버에 대한 액세스 권한이 있는 시스템 관리자 또는 개발자가 명령줄에서 캐시를 관리하는 방법을 설명합니다.

>[!NOTE]
>
>
>Commerce 사이트 관리자는 캐시 관리 시스템 도구를 사용하여 관리자로부터 캐시를 관리할 수 있습니다. [관리 시스템 안내서](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/tools/cache-management)에서 _캐시 관리_&#x200B;를 참조하십시오.


## 캐시 상태 보기

Commerce Application Server의 명령줄에서 `cache:status` Commerce CLI 명령을 사용하여 캐시의 상태를 확인합니다.

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

샘플은 다음과 같습니다.

```
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
             webhooks_response: 1
                           eav: 1
         customer_notification: 1
 graphql_query_resolver_result: 1
            config_integration: 1
        config_integration_api: 1
                  admin_ui_sdk: 1
                     full_page: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

>[!TIP]
>
>Adobe Commerce에서 지원하는 기본 캐시 유형에 대한 자세한 설명은 [관리 시스템 안내서](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/tools/cache-management#caches)의 _캐시_&#x200B;를 참조하십시오.


## 캐시 유형 활성화 또는 비활성화

이 명령을 사용하면 모든 캐시 유형 또는 지정한 캐시 유형만 활성화하거나 비활성화할 수 있습니다. 캐시 유형을 비활성화하면 캐시를 플러시하지 않고도 변경 결과가 표시되므로 개발 중에 유용합니다. 그러나 캐시 유형을 비활성화하면 성능에 부정적인 영향을 줍니다.

>[!INFO]
>
>버전 2.2부터 프로덕션 모드에서 Commerce을 실행하는 동안 명령줄을 사용해서만 캐시 유형을 활성화하거나 비활성화할 수 있습니다. 개발자 모드에서 Commerce을 실행하는 경우 명령줄을 사용하거나 수동으로 캐시 유형을 활성화하거나 비활성화할 수 있습니다. 이렇게 하려면 먼저 `<magento_root>/app/etc/env.php`파일 시스템 소유자[가 &#x200B;](../../installation/prerequisites/file-system/overview.md)을(를) 수동으로 쓸 수 있게 해야 합니다.

명령줄 또는 관리자를 사용하여 캐시 유형을 정리(_플러시_ 또는 _새로 고침_&#x200B;이라고도 함)할 수 있습니다.

명령 옵션:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

`[type]`을(를) 생략하면 모든 캐시 유형이 동시에 활성화되거나 비활성화됩니다. `type` 옵션은 공백으로 구분된 캐시 형식 목록입니다.

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

```
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>캐시 유형을 활성화하면 해당 캐시 유형이 자동으로 지워집니다.

>[!INFO]
>
>버전 2.3.4부터 Commerce은 모든 시스템 EAV 속성을 검색할 때 캐시합니다. 이 방식으로 EAV 속성을 캐시하면 DB에 대한 삽입/선택 요청의 양이 줄어들기 때문에 성능이 향상됩니다. 그러나 캐시 네트워크 크기도 증가합니다. 개발자는 `bin/magento config:set dev/caching/cache_user_defined_attributes 1` 명령을 실행하여 사용자 지정 EAV 특성을 캐시할 수 있습니다. [개발자 모드](../bootstrap/application-modes.md)에 있는 동안 관리자도 **스토어** > 설정 **구성** > **고급** > **개발자** > **설정 캐싱** > **사용자 정의 특성 캐싱**&#x200B;을 **예**(으)로 설정하여 이 작업을 수행할 수 있습니다.

## 캐시 유형 정리 및 플러시

>[!NOTE]
>
>여러 페이지 캐시는 이러한 엔터티를 편집하지 않고 **_동시에 자동으로_**&#x200B;무효화할 수 있습니다. 예를 들어 카탈로그의 제품이 범주에 할당되거나 [!UICONTROL related product rule]이(가) 수정되는 경우입니다.

캐시에서 오래된 항목을 제거하려면 _clean_ 또는 _flush_ 캐시 형식을 삭제할 수 있습니다.

- 캐시 유형을 정리하면 활성화된 Commerce 캐시 유형에서만 모든 항목이 삭제됩니다. 즉, 이 옵션은 Commerce에서 사용하는 캐시만 정리하므로 다른 프로세스나 애플리케이션에는 영향을 주지 않습니다.

  비활성화된 캐시 유형은 정리되지 않습니다.

  >[!TIP]
  >
  >Adobe Commerce의 버전을 업그레이드하거나, Magento Open Source에서 Adobe Commerce으로 업그레이드하거나, Adobe Commerce용 B2B 또는 임의의 모듈을 설치한 후에는 항상 캐시를 정리하십시오.

- 캐시 유형을 플러시하면 캐시 저장소가 지워지므로 동일한 저장소를 사용하는 다른 프로세스 애플리케이션에 영향을 줄 수 있습니다.

캐시를 지우려고 했지만 여전히 격리할 수 없는 문제가 있는 경우 캐시 유형을 플러시합니다.

명령 사용:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

여기서 `[type]`은(는) 공백으로 구분된 캐시 형식 목록입니다. `[type]`을(를) 생략하면 모든 캐시 유형이 동시에 정리되거나 플러시됩니다. 예를 들어 모든 캐시 유형을 플러시하려면 다음을 입력합니다.

```bash
   bin/magento cache:flush
```

샘플 결과:

```
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
   graphql_query_resolver_results
   config_webservice
   translate
```

>[!TIP]
>
>관리자에서 캐시 유형을 정리하고 플러시할 수도 있습니다. **시스템** > **도구** > **캐시 관리**(으)로 이동합니다. **플러시 캐시 저장소**&#x200B;은(는) `bin/magento cache:flush`과(와) 같습니다. **Magento 캐시 플러시**&#x200B;는 `bin/magento cache:clean`와(과) 같습니다.
