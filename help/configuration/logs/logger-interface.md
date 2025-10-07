---
title: 로거 인터페이스
description: 사용자 정의 로깅을 위해 Adobe Commerce의 로거 인터페이스를 사용하는 방법을 알아봅니다. PSR-3 구현 및 로그 기능을 살펴봅니다.
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# 로거 인터페이스

로거로 작업하려면 `\Psr\Log\LoggerInterface`의 인스턴스를 만들어야 합니다. 이 인터페이스를 사용하면 다음 함수를 호출하여 로그 파일에 데이터를 쓸 수 있습니다.

- [경고()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [중요()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [긴급()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [오류()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [경고()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

이를 수행하는 한 가지 방법은 [데이터베이스 작업 기록](../logs/database-activity.md) 예제에 설명되어 있습니다.

다른 방법은 다음과 같습니다.

```php
class SomeModel
 {
     private $logger;

     public function __construct(\Psr\Log\LoggerInterface $logger)
     {
         $this->logger = $logger;
     }

     public function doSomething()
     {
         try {
             //do something
         } catch (\Exception $e) {
             $this->logger->critical('Error message', ['exception' => $e]);
         }
     }
 }
```

앞의 예제에서는 `SomeModel`이(가) 생성자 삽입을 사용하여 `\Psr\Log\LoggerInterface` 개체를 받는 것을 보여 줍니다. `doSomething` 메서드에서 오류가 발생하면 메서드 `critical`(`$this->logger->critical($e);`)에 기록됩니다.

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424)은(는) 8개의 로그 수준(디버그, 정보, 알림, 경고, 오류, 중요, 경고 및 긴급)을 정의합니다.
