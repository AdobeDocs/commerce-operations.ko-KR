---
title: 로거 인터페이스
description: 로거 인터페이스를 시작합니다.
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# 로거 인터페이스

로거로 작업하려면 다음 인스턴스를 생성해야 합니다. `\Psr\Log\LoggerInterface`. 이 인터페이스를 사용하면 다음 함수를 호출하여 로그 파일에 데이터를 쓸 수 있습니다.

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [emergency()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

이를 수행하는 한 가지 방법은 다음에서 설명합니다. [데이터베이스 작업 기록](../logs/database-activity.md) 예.

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

앞의 예제에서는 를 `SomeModel` 수신: `\Psr\Log\LoggerInterface` 생성자 삽입을 사용하는 개체입니다. 메서드에서 `doSomething`, 오류가 발생하면 메서드에 기록됩니다 `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) 는 8개의 로그 수준(디버그, 정보, 알림, 경고, 오류, 중요, 경고 및 긴급)을 정의합니다.
