---
title: 세션 저장소에 memcached 사용
description: 상거래 세션 저장소에 memcached 사용에 대해 알아봅니다.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# 세션 저장소에 memcached 사용

Memcached는 범용 분산 메모리 캐싱 시스템입니다. 종종 RAM에서 데이터와 개체를 캐싱하여 동적 데이터베이스 기반 웹 사이트의 속도를 높이는 데 사용되어 외부 데이터 소스(예: 데이터베이스 또는 API)를 읽어야 하는 횟수를 줄일 수 있습니다.

Memcached에서는 여러 시스템에 분산될 수 있는 큰 해시 테이블을 제공합니다. 테이블이 가득 차면 후속 삽입으로 인해 이전 데이터가 가장 최근에 사용한(LRU) 순서로 삭제됩니다. 이 해시 테이블의 크기는 종종 매우 큽니다. (소스: [memcached.org](https://www.memcached.org/))

Commerce에서는 세션 저장소에 memcached를 사용하지만 페이지 캐싱에는 사용하지 않습니다. 페이지 캐싱의 경우 다음을 수행하는 것이 좋습니다 [레디스](../cache/redis-pg-cache.md) 또는 [바니쉬](../cache/config-varnish.md).

**memcached를 사용하도록 상거래를 구성하려면**:

1. 열기 `<your install dir>/app/etc/env.php` 텍스트 편집기에서 을 참조하십시오.
1. 다음을 찾습니다.

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. 다음과 같이 변경하십시오.

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   memcached에는 이 안내서의 범위를 벗어나는 선택적 시작 매개 변수가 있습니다. URL에 대한 자세한 내용은 [memcached](https://www.php.net/manual/en/memcached.sessions.php) 설명서, 소스 코드 및 변경 내용

1. 다음 섹션을 계속 진행합니다.

**Commerce에서 memcached의 작업을 확인하려면**:

1. 전자 상거래 설치 디렉터리에서 다음 디렉토리의 콘텐츠를 삭제합니다.

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. 상점 앞쪽에 있는 페이지로 이동합니다.

1. 관리자에게 로그인하고 여러 페이지로 이동합니다.

   오류가 표시되지 않으면 축하합니다! memcached가 작동합니다! 선택적으로 다음 단계에서 설명한 대로 memcached 스토리지를 확인할 수 있습니다.

   오류가 표시되는 경우(예: HTTP 500(내부 서버 오류) 개발자 모드를 활성화하고 문제를 진단합니다. Memcached가 실행 중인지, 올바르게 구성되었는지 확인합니다. `env.php` 구문 오류가 없습니다.

1. (선택 사항입니다.) Telnet을 사용하여 메모리 캐시 스토리지를 확인합니다.

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   결과는 다음과 비슷합니다.

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
