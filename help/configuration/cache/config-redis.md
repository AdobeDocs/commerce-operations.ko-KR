---
title: Redis 구성
description: Redis 기능에 대한 개요를 보고 Redis 구성을 시작하십시오.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Redis 구성

Redis 기능은 다음과 같습니다.

- PHP 세션 저장소
- 태그 기반 캐시 정리 `foreach` 루프
- On-Disk 저장 및 마스터/슬레이브 복제

## Redis 설치

Redis 소프트웨어 설치 및 구성은 이 안내서의 범위를 벗어납니다. 다음과 같은 리소스를 참조하십시오.

- [Redis 다운로드 페이지](https://redis.io/download)
- [Redis 빠른 시작](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Redis 설명서 페이지](https://redis.io/docs)

## Redis 구성 설정

설치에 따라 일반적으로 다음 파일 중 하나에서 Redis 구성을 찾을 수 있습니다. `/etc/redis/redis.conf` 또는 `/etc/redis/<port>.conf`

요구 사항에 대해 Redis 인스턴스를 최적화하려면 각 세션, 상거래 캐시 및 FPC에 대한 전용 인스턴스를 사용하여 최상의 결과를 얻습니다.

세션의 경우 Adobe은 다음 지속성 옵션 중 하나를 사용하여 지속성이 Redis 데이터를 디스크에 복사하도록 설정하는 것을 권장합니다. 일반 RDB(Redis Database Backup) 스냅샷 또는 AOF(Append Only File) 지속성 로그를 참조하십시오.

- **Redis 데이터베이스 백업** (RDB) 스냅샷은 마지막 저장 이후 최소 개수의 키가 변경된 경우 지정된 시간 후 덤프 파일에 전체 데이터베이스를 저장합니다. 를 사용하십시오 `save` 내부 설정 `redis.conf` 이 설정을 구성할 파일입니다.

- **파일만 추가** (AOF) Redis로 보낸 각 쓰기 작업을 저널 파일에 저장합니다. Redis는 다시 시작 시에만 이 파일을 읽고 원래 데이터 세트를 복원하는 데 사용합니다.

RDB 옵션과 AOF 옵션을 동시에 활성화할 수도 있습니다. 지속성 옵션의 장점과 단점을 포함한 추가 세부 사항은 다음을 참조하십시오. [Redis Persistence 설명서](https://redis.io/topics/persistence).

캐시 인스턴스에 대해 전체 상거래 캐시를 저장하기에 충분하도록 인스턴스를 설정합니다. 크기 요구 사항은 제품 수 및 스토어 보기 수와 같은 다양한 요소에 따라 다릅니다. 시작 지점으로 파일 시스템에서 캐시 폴더의 크기를 사용할 수 있습니다. 예를 들어 `var/cache` 파일 시스템의 폴더는 5GB이며, 시작할 최소 5GB의 Redis 인스턴스를 설정합니다. 상거래 캐시를 복원할 수 있으므로 캐시 인스턴스에 지속성이 필요하지 않습니다. 자세한 내용은 [Redis 캐시 안내서](https://redis.io/docs/manual/eviction/).

성능 조정을 위해 비동기 삭제에 대해 다음 설정을 활성화할 수도 있습니다. 이러한 설정은 레디스의 동작을 변경하지 않습니다. 참조 - [레드뉴스](http://antirez.com/news/93) 비동기 삭제에 대한 자세한 내용을 참조하십시오.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

Redis 6.x 이상에서는 다음 값을 추가할 수도 있습니다.

```ini
lazyfree-lazy-user-del yes
```
