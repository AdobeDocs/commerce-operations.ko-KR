---
title: 사용자 지정 로그 파일에 쓰기
description: 사용자 지정 로그 파일을 설정하는 방법에 대해 알아봅니다.
feature: Configuration, Logs
badge: label="기여자 Atwix" type="정보" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# 사용자 지정 로그 파일에 쓰기

다음 `Magento\Framework\Logger` 모듈에는 다음 핸들러 클래스가 포함되어 있습니다.

| 클래스 | 로그 파일 |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

다음 위치에서 찾을 수 있습니다. `lib/internal/Magento/Framework/Logger/Handler` 디렉토리.

다음 방법 중 하나를 사용하여 사용자 정의 파일에 로그인할 수 있습니다.

- 에서 사용자 지정 로그 파일 설정 `di.xml`
- 사용자 지정 로거 처리기 클래스에서 사용자 지정 파일 설정

## 에서 사용자 지정 로그 파일 설정 `di.xml`

이 예는 를 사용하는 방법을 보여 줍니다 [가상 유형](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 기록하기 `debug` 표준 대신 사용자 지정 로그 파일에 메시지 `/var/log/debug.log`.

1. 다음에서 `di.xml` 모듈의 파일인 경우 사용자 지정 로그 파일을 [가상 유형](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   다음 `name` 값 `Magento\Payment\Model\Method\MyCustomDebug` 은(는) 고유해야 합니다.

1. 다른 작업 영역에서 핸들러 정의 [가상 유형](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 고유 포함 `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. 삽입 `MyCustomLogger` [가상 유형](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 다음에서 `Magento\Payment\Model\Method\Logger` 개체:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. 가상 클래스 `Magento\Payment\Model\Method\MyCustomDebug` 이(가)에 주입됩니다. `debug` 의 핸들러 `$logger` 의 속성 `Magento\Payment\Model\Method\Logger` 클래스.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

예외 메시지는 `/var/log/payment.log` 파일.

## 로거 처리기 클래스에서 사용자 지정 로그 파일 설정

이 예제에서는 사용자 지정 로거 처리기 클래스를 사용하여 기록하는 방법을 보여 줍니다 `error` 특정 로그 파일에 메시지를 남깁니다.

1. 데이터를 기록하는 클래스를 만듭니다. 이 예제에서 클래스는 `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   namespace Vendor\ModuleName\Logger\Handler;
   
   use Magento\Framework\Logger\Handler\Base as BaseHandler;
   use Monolog\Logger as MonologLogger;
   
   /**
    * Class ErrorHandler
    */
   class ErrorHandler extends BaseHandler
   {
       /**
        * Logging level
        *
        * @var int
        */
       protected $loggerType = MonologLogger::ERROR;
   
       /**
        * File name
        *
        * @var string
        */
       protected $fileName = '/var/log/my_custom_logger/error.log';
   }
   ```

1. 이 클래스의 핸들러를 다음으로 정의 [가상 유형](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 의 모듈에서 `di.xml` 파일.

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` 는 고유 식별자입니다.

1. 다음에서 `type` 사용자 지정 로거 처리기를 삽입할 클래스 이름을 지정합니다. 이전 단계의 가상 형식 이름을 이 형식의 인수로 사용합니다.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   소스 코드 `Vendor\ModuleName\Observer\MyObserver` 클래스:

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   declare(strict_types=1);
   
   namespace Vendor\ModuleName\Observer;
   
   use Psr\Log\LoggerInterface as PsrLoggerInterface;
   use Exception;
   use Magento\Framework\Event\ObserverInterface;
   use Magento\Framework\Event\Observer;
   
   /**
    * Class MyObserver
    */
   class MyObserver implements ObserverInterface
   {
       /**
        * @var PsrLoggerInterface
        */
       private $logger;
   
       /**
        * MyObserver constructor.
        *
        * @param PsrLoggerInterface $logger
        */
       public function __construct(
           PsrLoggerInterface $logger
       ) {
           $this->logger = $logger;
       }
   
       /**
        * @param Observer $observer
        */
       public function execute(Observer $observer)
       {
           try {
               // some code goes here
           } catch (Exception $e) {
               $this->logger->error($e->getMessage());
           }
       }
   }
   ```

1. 클래스 `Vendor\ModuleName\Logger\Handler\ErrorHandler` 이(가)에 주입됩니다. `error` 의 핸들러 `$logger` 의 속성 `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

예외 메시지는 `/var/log/my_custom_logger/error.log` 파일.

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
