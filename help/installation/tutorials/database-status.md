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

이 명령을 실행하기 전에 [배포 구성을 만들거나 업데이트](deployment.md)해야 합니다.

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
| 1 | 일부 모듈은 데이터베이스보다 최신 또는 오래된 코드 버전을 사용합니다. | [`magento setup:upgrade`](database-upgrade.md)을(를) 실행하여 데이터베이스 스키마를 업데이트하고 응용 프로그램 루트 디렉터리에서 `composer update`을(를) 실행하여 구성 요소 종속성을 업데이트합니다. |
| 2 | `magento setup:upgrade`은(는) 필수입니다. | 데이터베이스 스키마를 업데이트하는 [`magento setup:upgrade`](database-upgrade.md) |
