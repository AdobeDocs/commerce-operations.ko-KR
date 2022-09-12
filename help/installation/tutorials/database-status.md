---
title: 데이터베이스 상태 확인
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source 데이터베이스 상태를 확인합니다.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 2%

---


# 데이터베이스 상태 확인

이 명령을 실행하기 전에 [배포 구성 만들기 또는 업데이트](deployment.md).

## 명령 사용

데이터베이스의 상태를 확인하려면

```bash
bin/magento setup:db:status
```

이 명령에는 인수나 옵션이 없습니다.

다음은 샘플 출력입니다.

```terminal
All modules are up to date.
```

이 명령은 다음 종료 코드 중 하나를 반환합니다.

| 종료 코드 | 설명 | 추천 작업 |
|--------------|--------------|---------------|
| 0 | 일반 | 없음 |
| 1 | 일부 모듈은 데이터베이스보다 최신 또는 이전 버전의 코드를 사용합니다 | 실행 [`magento setup:upgrade`](database-upgrade.md) 데이터베이스 스키마를 업데이트하고 를 실행하려면 `composer update` 구성 요소 종속성을 업데이트하려면 응용 프로그램 루트 디렉터리에서 |
| 2개 | `magento setup:upgrade` 필수 여부 | [`magento setup:upgrade`](database-upgrade.md) 를 업데이트하려면 [데이터베이스 스키마](https://glossary.magento.com/database-schema) |
