---
title: 단위 테스트 실행
description: Adobe Commerce 코드 베이스에 정의된 단위 테스트를 실행합니다.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# 단위 테스트 실행

{{file-system-owner}}

이 명령은 Commerce 2 코드 베이스에 정의된 테스트 세트를 실행합니다. 선택한 모든 테스트 또는 테스트를 실행할 수 있습니다. 지원되지 않는 유형을 지정할 때마다 프로그램이 종료되고 사용 가능한 모든 유형이 나열됩니다. 실행 후 테스트 실행 및 결과를 보여주는 자세한 보고서가 표시됩니다.

## 사전 요구 사항

이 명령을 실행하기 전에 다음 _은(는) true여야 합니다_.

- `Magento_Developer` 모듈을 사용하도록 설정해야 합니다. 다음과 같이 활성화할 수 있습니다.

  ```bash
  bin/magento module:enable [--force] Magento_Developer
  ```

  필요한 경우에만 `--force` 옵션을 사용하십시오.

- 원하는 테스트를 실행하도록 시스템을 설정해야 합니다.

예를 들어 통합 테스트를 실행하려면 `dev/tests/integration/etc/install-config-mysql.php.dist`을(를) `dev/tests/integration/etc/install-config-mysql.php`에 복사하고 환경에 맞게 수정해야 합니다.

## 테스트 실행

명령 사용:

```bash
bin/magento dev:tests:run <test>
```

사용 가능한 테스트 유형을 나열하려면 다음을 수행합니다.

```bash
bin/magento dev:tests:run --help
```

샘플 반환:

```
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

예를 들어 통합 테스트를 실행하려면 다음을 수행합니다.

```bash
bin/magento dev:tests:run integration
```
