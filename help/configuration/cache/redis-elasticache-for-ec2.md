---
title: AWS ElastiCache를 사용하여 Redis 구성
description: EC2에서 호스팅되는 Commerce 인스턴스의 경우 로컬 Redis 인스턴스 대신 AWS ElastiCache를 사용하는 방법에 대해 알아봅니다. 명령줄 설정, 구성 옵션 및 유효성 검사 기술을 살펴봅니다.
feature: Configuration, Cache
source-git-commit: 908796587e78b80d699354c0506ca948d0f37518
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# AWS ElastiCache를 사용하여 Redis 구성

Commerce 2.4.3부터 Amazon EC2에서 호스팅되는 인스턴스는 로컬 Redis 인스턴스 대신 AWS ElastiCache를 사용할 수 있습니다.

>[!WARNING]
>
>이 섹션은 Amazon EC2 VPC에서 실행되는 Commerce 인스턴스에만 적용됩니다. 온-프레미스 설치에서는 작동하지 않습니다.

## 사전 요구 사항

- **Redis OSS 서버리스 캐시 만들기**—AWS 관리 콘솔에서 EC2 인스턴스의 동일한 지역 및 VPC에 Redis 캐시를 만듭니다. 지침은 [AWS Elasticache 설명서]&#x200B;(https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html)를 참조하십시오.

- **EC2 Commerce 인스턴스에 대한 연결 확인**

   - EC2 인스턴스에 대한 SSH 연결 열기
   - EC2 인스턴스에서 Redis 클라이언트를 설치합니다.

     ```bash
     sudo apt-get install redis
     ```

   - EC2 보안 그룹에 인바운드 규칙 추가: 유형 `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - ElastiCache 클러스터 보안 그룹에 인바운드 규칙을 추가합니다. 유형 `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Redis CLI에 연결:

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### 클러스터를 사용하도록 Commerce 구성

Commerce은 여러 유형의 캐싱 구성을 지원합니다. 일반적으로 캐싱 구성은 프론트엔드와 백엔드 간에 분할됩니다. 프론트엔드 캐싱은 `default`(으)로 분류되며 모든 캐시 유형에 사용됩니다. 성능을 개선하기 위해 하위 수준 캐시를 사용자 정의하거나 하위 수준 캐시로 분할할 수 있습니다. 일반적인 Redis 구성은 기본 캐시와 페이지 캐시를 고유한 Redis 데이터베이스(RDB)로 구분합니다.

`setup` 명령을 실행하여 Redis 끝점을 지정합니다.

Redis용 Commerce을 기본 캐싱으로 구성하려면 다음을 수행하십시오.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Redis용 Commerce 페이지 캐싱을 구성하려면:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

세션 스토리지에 Redis를 사용하도록 Commerce을 구성하려면 다음을 수행하십시오.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## 연결 확인

**Commerce이 ElastiCache에 연결되어 있는지 확인하려면**:

1. Commerce EC2 인스턴스에 대한 SSH 연결을 엽니다.
1. Redis 모니터를 시작합니다.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Commerce UI에서 페이지를 엽니다.
1. 터미널에서 [캐시 출력](#verify-the-redis-connection)을 확인하세요.
