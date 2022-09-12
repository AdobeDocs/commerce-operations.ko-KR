---
title: 사용자 정의 로그 파일에 쓰기
description: 사용자 지정 로그 파일을 설정하는 방법을 알아봅니다.
contributor_name: Atwix
contributor_link: https://www.atwix.com/
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# 사용자 정의 로그 파일에 쓰기

다음 `Magento\Framework\Logger` 모듈에는 다음 처리기 클래스가 포함되어 있습니다.

| 클래스 | 로그 파일 |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

여기에서 찾을 수 있습니다. `lib/internal/Magento/Framework/Logger/Handler` 디렉토리.

다음 방법 중 하나를 사용하여 사용자 지정 파일에 로그인할 수 있습니다.

- 에서 사용자 지정 로그 파일을 설정합니다. `di.xml`
- 사용자 지정 로거 처리기 클래스에서 사용자 지정 파일 설정

## 에서 사용자 지정 로그 파일을 설정합니다. `di.xml`

이 예는 를 사용하는 방법을 보여줍니다. [가상 유형](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 기록하다 `debug` 표준 대신 사용자 지정 로그 파일에 메시지 보내기 `/var/log/debug.log`.

1. 에서 `di.xml` 모듈의 파일에서 사용자 정의 로그 파일을 [가상 유형](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   다음 `name` 값 `Magento\Payment\Model\Method\MyCustomDebug` 고유해야 합니다.

1. 다른 처리기를 정의합니다. [가상 유형](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 고유한 `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. 를 주입합니다. `MyCustomLogger` [가상 유형](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 에서 `Magento\Payment\Model\Method\Logger` 개체:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. 가상 클래스 `Magento\Payment\Model\Method\MyCustomDebug` 에 삽입됨 `debug` 의 처리기 `$logger` 속성( `Magento\Payment\Model\Method\Logger` 클래스 이름을 지정합니다.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

예외 메시지는 `/var/log/payment.log` 파일.

## 로거 처리기 클래스에서 사용자 지정 로그 파일 설정

이 예에서는 사용자 정의 로거 처리기 클래스를 사용하여 기록하는 방법을 보여 줍니다 `error` 메시지를 특정 로그 파일에 추가합니다.

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

1. 이 클래스의 처리기를 [가상 유형](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 모듈 `di.xml` 파일.

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

1. 에서 `type` 정의를 사용하여 사용자 지정 로거 핸들러가 삽입되는 클래스 이름을 지정합니다. 이전 단계의 가상 유형 이름을 이 유형의 인수로 사용합니다.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   의 소스 코드 `Vendor\ModuleName\Observer\MyObserver` 클래스:

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

1. 클래스 `Vendor\ModuleName\Logger\Handler\ErrorHandler` 에 삽입됨 `error` 의 처리기 `$logger` 속성( `Vendor\ModuleName\Observer\MyObserver`.

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
