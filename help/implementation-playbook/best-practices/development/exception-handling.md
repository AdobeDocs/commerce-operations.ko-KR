---
title: 예외 처리 우수 사례
description: Adobe Commerce 프로젝트를 개발할 때 예외를 로깅하는 데 권장되는 방법에 대해 알아봅니다.
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# 예외 처리 우수 사례

예외 모델을 컨텍스트로 사용하여 `exception.log` 파일에 예외를 기록하지 않으면 New Relic 또는 다른 PSR-3 모노로그 호환 로그 저장소에서 예외를 올바르게 인식하고 분석하지 못합니다. 예외의 일부만 로깅(또는 잘못된 파일에 로깅)하면 예외가 무시될 때 프로덕션에서 버그가 발생합니다.

## 올바른 예외 처리

다음 체크리스트에서는 올바른 예외 처리를 보여 주는 예를 제공합니다.

### ![수정](../../../assets/yes.svg) 예외 로그에 쓰기

불가피한 사유가 있는 경우가 아니면 추가 작업에 관계없이 다음 패턴을 사용하여 예외 로그에 작성하십시오.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

이 방법은 `$e->getMessage`PSR-3 컨텍스트 표준`$e`에 따라 로그 메시지에 [을(를), 컨텍스트에 &#x200B;](https://www.php-fig.org/psr/psr-3/#13-context) 개체를 자동으로 저장합니다. 이 작업은 `\Magento\Framework\Logger\Monolog::addRecord`에서 수행됩니다.

### 음소거 신호 ![수정](../../../assets/yes.svg)개

의도한 작업 흐름의 일부인 예외를 기록하지 않아 신호를 음소거합니다. 예외가 발생했을 때 후속 작업이 필요하지 않으므로 예외가 발생했을 때 로그하여 분석할 필요가 없습니다. 신호를 무음하는 이유와 의도적임을 나타내는 주석을 추가합니다. `phpcs:ignore`과(와) 결합합니다.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![수정](../../../assets/yes.svg) 다운그레이드 예외

[PSR-3 컨텍스트 표준](https://www.php-fig.org/psr/psr-3/#13-context)에 따라 예외를 다운그레이드합니다.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![수정](../../../assets/yes.svg) 로깅이 항상 먼저 실행됨

로그에 기록하기 전에 다른 예외나 치명적인 오류가 발생하는 경우를 방지하기 위해 항상 코드의 맨 먼저 로깅하는 것이 모범 사례입니다.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![수정](../../../assets/yes.svg) 로그 메시지와 전체 예외 추적

[PSR-3 컨텍스트 표준](https://www.php-fig.org/psr/psr-3/#13-context)을(를) 따라 메시지 및 전체 예외 추적을 기록합니다.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## 잘못된 예외 처리

다음 예제에서는 잘못된 예외 처리를 보여 줍니다.

### 로깅 전 ![잘못된](../../../assets/no.svg) 논리

로깅하기 전 논리는 다른 예외나 치명적인 오류를 발생시킬 수 있으므로 예외가 기록되지 않으므로 [올바른 예제](#logging-always-comes-first)로 대체해야 합니다.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![잘못됨](../../../assets/no.svg) 비어 있음 `catch`

빈 `catch` 블록은 의도하지 않은 음소거의 징후일 수 있으므로 [올바른 예제](#mute-signals)로 대체해야 합니다.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![올바르지 않음](../../../assets/no.svg) 이중 로컬라이제이션

발견된 지역화된 예외가 아직 번역되지 않은 경우 예외를 처음으로 throw한 위치에서 문제를 해결합니다.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![잘못된](../../../assets/no.svg) 로그 메시지와 다른 로그 파일에 대한 추적

다음 코드는 예외에 대한 스택 추적을 로그 파일에 문자열로 잘못 기록합니다.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

이 접근 방법에서는 PSR-3과 호환되지 않는 라인 구분을 메시지에 도입합니다. 스택 추적을 포함한 예외는 New Relic 또는 다른 PSR-3 모노로그 호환 로그 저장소에서 메시지와 함께 올바르게 저장되도록 메시지 컨텍스트의 일부여야 합니다.

[예외 로그에 쓰기](#write-to-the-exception-log) 또는 [다운그레이드 예외](#downgrade-exceptions)에 표시된 올바른 예제의 다음 코드를 바꾸어 이 문제를 해결하십시오.

### ![올바르지 않음](../../../assets/no.svg) 컨텍스트가 없는 다운그레이드 예외

예외가 오류로 다운그레이드되어 개체 전달이 허용되지 않고 문자열만 허용되므로 `getMessage()`이(가) 됩니다. 이로 인해 추적이 손실되므로 [예외 로그에 쓰기](#write-to-the-exception-log) 또는 [다운그레이드 예외](#downgrade-exceptions)에 표시된 올바른 예제로 대체해야 합니다.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![잘못됨](../../../assets/no.svg) 메시지를 예외 로그에만 기록합니다.

개체 `$e`을(를) 전달하는 대신 `$e->getMessage()`만 전달됩니다. 이렇게 하면 추적이 손실되므로 [예외 로그에 쓰기](#write-to-the-exception-log) 또는 [다운그레이드 예외](#downgrade-exceptions)와 같은 올바른 예제로 대체해야 합니다.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![잘못됨](../../../assets/no.svg) 누락 `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

`phpcs:ignore` 줄을 생략하면 PHPCS에서 경고가 트리거되므로 CI를 전달하면 안 됩니다. 이 예제는 [음소거 신호](#mute-signals)에 표시된 올바른 예제로 대체해야 합니다.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
