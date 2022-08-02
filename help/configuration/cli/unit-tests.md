---
title: 단위 테스트 실행
description: Adobe Commerce 코드 베이스에 정의된 단위 테스트를 실행합니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# 단위 테스트 실행

{{file-system-owner}}

이 명령은 상거래 2 코드 베이스에 정의된 테스트 집합을 실행합니다. 선택한 모든 테스트나 테스트를 실행할 수 있습니다. 지원되지 않는 형식을 지정할 때마다 프로그램이 종료되고 사용 가능한 모든 유형이 나열됩니다. 실행 후 테스트 실행 및 결과를 보여주는 세부 보고서가 표시됩니다.

## 전제 조건

이 명령을 실행하기 전에 _반드시_ true입니다.

- 다음 `Magento_Developer` 모듈을 활성화해야 합니다. 다음과 같이 활성화할 수 있습니다.

   ```bash
   bin/magento module:enable [--force] Magento_Developer
   ```

   를 사용하십시오 `--force` 필요한 경우에만 선택합니다.

- 원하는 테스트를 실행하려면 시스템을 설정해야 합니다.

예를 들어 통합 테스트를 실행하려면 를 복사해야 합니다 `dev/tests/integration/etc/install-config-mysql.php.dist` to `dev/tests/integration/etc/install-config-mysql.php` 환경에 맞게 수정합니다.

## 테스트 실행

명령 사용:

```bash
bin/magento dev:tests:run <test>
```

사용 가능한 테스트 유형을 나열하려면 다음을 수행하십시오.

```bash
bin/magento dev:tests:run --help
```

샘플 반환:

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

예를 들어 통합 테스트를 실행하려면

```bash
bin/magento dev:tests:run integration
```
