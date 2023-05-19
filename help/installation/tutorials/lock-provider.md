---
title: 잠금 공급자 구성
description: Adobe Commerce 또는 Magento Open Source 배포에서 중복 cron 작업 및 cron 그룹이 실행되지 않도록 하려면 다음 단계를 따르십시오.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# 잠금 공급자 구성

이 명령을 실행하기 전에 다음을 수행해야 합니다 *또는* 다음을 수행해야 합니다. [응용 프로그램 설치](../advanced.md):

* [배포 구성 만들기 또는 업데이트](deployment.md)
* [데이터베이스 스키마 만들기](database.md)

## 보안 설치

{{$include /help/_includes/secure-install.md}}

## 잠금 구성

중복 cron 작업 및 cron 그룹이 시작되지 않도록 잠금 공급자를 구성하십시오. (Adobe Commerce 또는 Magento Open Source 2.2.x, 2.2.5 이상 및 2.3.3 이상 필요)

Adobe Commerce 및 Magento Open Source은 데이터베이스를 사용하여 기본적으로 잠금을 저장합니다. 서버에 여러 노드가 있는 경우 Zookeeper를 잠금 공급자로 사용하는 것이 좋습니다.

클라우드 인프라에서 Adobe Commerce을 실행하는 경우 잠금 공급자 설정을 구성할 필요가 없습니다. 프로비전 프로세스 중에 Pro 프로젝트에 대한 파일 잠금 공급자를 구성합니다. 다음을 참조하십시오 [클라우드 변수](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### 명령 사용

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 매개 변수 설명

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--lock-provider` | 공급자 이름 잠금: `db`, `zookeeper`, 또는 `file`.<br><br>기본 잠금 공급자: `db` | 아니요 |
| `--lock-db-prefix` | 를 사용할 때 잠금 충돌을 방지하기 위한 특정 DB 접두사 `db` 공급자 잠금.<br><br>기본값: `NULL` | 아니요 |
| `--lock-zookeeper-host` | 를 사용할 때 Zookeeper 클러스터에 연결할 호스트 및 포트 `zookeeper` 공급자 잠금.<br><br>예: `127.0.0.1:2181` | 예, 다음을 설정하면 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper가 잠금을 저장하는 경로입니다.<br><br>기본 경로는 다음과 같습니다. `/magento/locks` | 아니요 |
| `--lock-file-path` | 파일 잠금이 저장되는 경로입니다. | 예, 다음을 설정하면 `--lock-provider=file` |
