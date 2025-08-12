---
title: Valkey 구성
description: Valkey 기능에 대한 개요를 확인하고 Valkey 구성을 시작하십시오.
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
source-git-commit: b2cf71bfda3e5db8e27eb28d764cf99216454e33
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Valkey 구성

주요 기능은 다음과 같습니다.

- PHP 세션 저장소
- `foreach` 루프 없이 태그 기반 캐시 정리
- 디스크 상의 저장 및 마스터/슬레이브 복제

## Valkey 설치

Valkey 소프트웨어를 설치하고 구성하려면 다음 리소스를 참조하십시오.

- [Valkey 페이지 다운로드](https://valkey.io/download/)
- [Valkey 빠른 시작](https://valkey.io/topics/quickstart/)
- [Valkey 설명서 페이지](https://valkey.io/docs)

## Valkey 구성 설정

설치에 따라 일반적으로 `/etc/valkey/valkey.conf` 파일 또는 `/etc/valkey/<port>.conf` 파일에서 Valkey 구성을 찾을 수 있습니다.

요구 사항에 맞게 Valkey 인스턴스를 최적화하려면 각 세션, Commerce 캐시 및 FPC에 대한 전용 인스턴스를 사용하여 최상의 결과를 얻을 수 있습니다.

Adobe은 세션에 대해 지속성을 설정하여 Valkey 데이터를 디스크에 복사할 것을 권장합니다. RDB(Valkey Database Backup) 스냅샷 또는 AOF(Append Only File) 지속성 로그를 사용할 수 있습니다.

- **RDB**(Valkey 데이터베이스) 스냅샷은 마지막 저장 이후 최소 키 수가 변경된 경우 지정된 시간 후에 전체 데이터베이스를 덤프 파일에 저장합니다. `save` 파일 내의 `valkey.conf` 설정을 사용하여 이 설정을 구성하십시오.

- **파일만 추가**(AOF)는 Valkey로 전송된 각 쓰기 작업을 저널 파일에 저장합니다. Valkey는 재시작 시에만 이 파일을 읽고 원본 데이터 세트를 복원하는 데 사용합니다.

RDB 및 AOF 옵션을 동시에 활성화할 수도 있습니다. 지속성 옵션의 장점과 단점을 포함한 자세한 내용은 [Valkey 지속성 설명서](https://valkey.io/topics/persistence/)를 참조하십시오.

캐시 인스턴스의 경우 전체 Commerce 캐시를 저장할 수 있을 만큼 크도록 인스턴스를 설정합니다. 크기 요구 사항은 제품 수 및 스토어 조회수와 같은 다양한 요인에 따라 다릅니다. 시작점으로 파일 시스템의 캐시 폴더 크기를 사용할 수 있습니다. 예를 들어, 파일 시스템의 `var/cache` 폴더가 5GB인 경우 시작하려면 최소 5GB로 Valkey 인스턴스를 설정하십시오. Commerce 캐시를 복원할 수 있으므로 캐시 인스턴스에 지속성이 필요하지 않습니다.

성능 조정을 위해 비동기 삭제에 대해 다음 설정을 활성화할 수 있습니다. 이러한 설정은 Valkey의 동작을 변경하지 않습니다.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```
