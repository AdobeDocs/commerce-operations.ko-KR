---
title: 데이터베이스 상태 확인
description: 다음 단계에 따라 Adobe Commerce 데이터베이스 상태를 확인하십시오.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%

---

# 데이터베이스 상태 확인

이 명령을 실행하기 전에 다음을 수행해야 합니다 [배포 구성 만들기 또는 업데이트](deployment.md).

## 명령 사용

데이터베이스의 상태를 확인합니다.

```bash
bin/magento setup:db:status
```

이 명령에는 인수 또는 옵션이 없습니다.

샘플 출력은 다음과 같습니다.

```terminal
All modules are up to date.
```

이 명령은 다음 종료 코드 중 하나를 반환합니다.

| 종료 코드 | 설명 | 제안된 작업 |
|--------------|--------------|---------------|
| 0 | 기본 | 없음 |
| 1 | 일부 모듈은 데이터베이스보다 최신 또는 오래된 코드 버전을 사용합니다. | 실행 [`magento setup:upgrade`](database-upgrade.md) 데이터베이스 스키마를 업데이트하고 실행하려면 `composer update` 애플리케이션 루트 디렉토리에서 구성 요소 종속성 업데이트 |
| 2 | `magento setup:upgrade` 필수 | [`magento setup:upgrade`](database-upgrade.md) 데이터베이스 스키마를 업데이트하려면 |
