---
title: 세션 스토리지에 memcached 사용
description: Commerce 세션 스토리지용 memcached 사용에 대해 알아봅니다.
feature: Configuration, Cache, Storage
exl-id: 24077929-e732-4579-8d7d-717a4902fc64
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# 세션 스토리지에 memcached 사용

Memcached는 범용 분산 메모리 캐싱 시스템입니다. RAM에 데이터와 개체를 캐싱하여 외부 데이터 소스(예: 데이터베이스 또는 API)를 읽어야 하는 횟수를 줄여 동적 데이터베이스 기반 웹 사이트의 속도를 높이는 데 종종 사용됩니다.

Memcached는 여러 시스템에 배포할 수 있는 큰 해시 테이블을 제공합니다. 테이블이 가득 차면 이후에 삽입하면 오래된 데이터가 LRU(가장 최근에 사용한 항목) 순서로 삭제됩니다. 이 해시 테이블의 크기는 종종 매우 큽니다. (소스: [memcached.org](https://www.memcached.org/))

Commerce는 세션 스토리지에 memcached를 사용하지만 페이지 캐싱에 대해서는 사용하지 않습니다. 페이지 캐싱의 경우 다음을 권장합니다 [레디스](../cache/redis-pg-cache.md) 또는 [니스](../cache/config-varnish.md).

**memcached를 사용하도록 Commerce를 구성하려면**:

1. 열기 `<your install dir>/app/etc/env.php` 텍스트 편집기에서.
1. 다음을 찾습니다.

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. 다음과 같이 변경합니다.

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   memcached에는 이 안내서의 범위를 벗어나는 선택적 시작 매개변수가 있습니다. 다음에서 해당 요소에 대한 자세한 내용을 찾을 수 있습니다. [memcached](https://www.php.net/manual/en/memcached.sessions.php) 설명서, 소스 코드 및 변경 내용.

1. 다음 섹션을 계속합니다.

**Commerce에서 memcached 작업을 확인하려면**:

1. Commerce 설치 디렉터리 아래에 있는 다음 디렉터리의 내용을 삭제합니다.

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. 상점 첫 화면의 아무 페이지나 이동하십시오.

1. 관리자에 로그인하고 여러 페이지를 찾아봅니다.

   오류가 표시되지 않으면 축하합니다! memcached가 작동 중입니다! 다음 단계에서 설명한 대로 선택적으로 Memcached 스토리지를 살펴볼 수 있습니다.

   HTTP 500(내부 서버 오류)과 같은 오류가 표시되면 개발자 모드를 활성화하고 문제를 진단합니다. memcached가 실행 중인지, 제대로 구성되어 있는지, `env.php` 에 구문 오류가 없습니다.

1. (선택 사항.) 텔넷을 사용하여 memcached 스토리지를 확인합니다.

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   결과는 다음과 유사하게 표시됩니다.

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
