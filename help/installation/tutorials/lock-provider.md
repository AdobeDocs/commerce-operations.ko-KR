---
title: 잠금 공급자 구성
description: Adobe Commerce 배포에서 중복 cron 작업 및 cron 그룹이 실행되지 않도록 하려면 다음 단계를 따르십시오.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# 잠금 공급자 구성

이 명령을 실행하기 전에 다음 *또는*&#x200B;을(를) 수행해야 합니다. [응용 프로그램을 설치](../advanced.md)해야 합니다.

* [배포 구성 만들기 또는 업데이트](deployment.md)
* [데이터베이스 스키마 만들기](database.md)

## 보안 설치

{{$include /help/_includes/secure-install.md}}

## 잠금 구성

중복 cron 작업 및 cron 그룹이 시작되지 않도록 잠금 공급자를 구성하십시오. (Adobe Commerce 2.2.x, 2.2.5 이상 및 2.3.3 이상 필요)

Adobe Commerce은 데이터베이스를 사용하여 기본적으로 잠금을 저장합니다. 서버에 여러 노드가 있는 경우 Zookeeper를 잠금 공급자로 사용하는 것이 좋습니다.

클라우드 인프라에서 Adobe Commerce을 실행하는 경우 잠금 공급자 설정을 구성할 필요가 없습니다. 프로비전 프로세스 중에 Pro 프로젝트에 대한 파일 잠금 공급자를 구성합니다. [클라우드 변수](https://devdocs.magento.com/cloud/env/variables-cloud.html)를 참조하십시오.

### 명령 사용

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 매개 변수 설명

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--lock-provider` | 공급자 이름 잠금: `db`, `zookeeper` 또는 `file`.<br><br>기본 잠금 공급자: `db` | 아니요 |
| `--lock-db-prefix` | `db` 잠금 공급자를 사용할 때 잠금 충돌을 방지하기 위한 특정 DB 접두사입니다.<br><br>기본값: `NULL` | 아니요 |
| `--lock-zookeeper-host` | `zookeeper` 잠금 공급자를 사용할 때 Zookeeper 클러스터에 연결할 호스트 및 포트입니다.<br><br>예: `127.0.0.1:2181` | 예, `--lock-provider=zookeeper`을(를) 설정하는 경우 |
| `--lock-zookeeper-path` | Zookeeper가 잠금을 저장하는 경로입니다.<br><br>기본 경로는 `/magento/locks`입니다. | 아니요 |
| `--lock-file-path` | 파일 잠금이 저장되는 경로입니다. | 예, `--lock-provider=file`을(를) 설정하는 경우 |
