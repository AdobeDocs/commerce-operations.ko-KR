---
title: 사용자 지정 로그 파일에 쓰기
description: Adobe Commerce에서 사용자 지정 로그 파일을 만들고 구성하는 방법에 대해 알아봅니다. 로거 처리기 및 사용자 지정 로깅 구현을 검색합니다.
feature: Configuration, Logs
badge: label="Atwix 제공" type="Informative" url="https://www.atwix.com/" tooltip="아트윅스"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# 사용자 지정 로그 파일에 쓰기

`Magento\Framework\Logger` 모듈에는 다음 처리기 클래스가 포함되어 있습니다.

| 클래스 | 로그 파일 |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php) | - |
| [Magento\Framework\Logger\Handler\Debug](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php) | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php) | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php) | - |
| [Magento\Framework\Logger\Handler\System](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php) | `/var/log/system.log` |

`lib/internal/Magento/Framework/Logger/Handler` 디렉터리에서 찾을 수 있습니다.

다음 방법 중 하나를 사용하여 사용자 정의 파일에 로그인할 수 있습니다.

- `di.xml`에서 사용자 지정 로그 파일 설정
- 사용자 지정 로거 처리기 클래스에서 사용자 지정 파일 설정

## `di.xml`에서 사용자 지정 로그 파일 설정

이 예제에서는 [가상 형식](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types)을(를) 사용하여 `debug`개의 메시지를 표준 `/var/log/debug.log` 대신 사용자 지정 로그 파일에 기록하는 방법을 보여 줍니다.

1. 모듈의 `di.xml` 파일에서 사용자 지정 로그 파일을 [가상 형식](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types)&#x200B;(으)로 정의합니다.

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   `name`의 `Magento\Payment\Model\Method\MyCustomDebug` 값은 고유해야 합니다.

1. 고유한 [을(를) 가진 다른 ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types)가상 형식`name`에서 처리기를 정의합니다.

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. `MyCustomLogger` 개체에 [ ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types)가상 형식`Magento\Payment\Model\Method\Logger`을(를) 삽입합니다.

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. 가상 클래스 `Magento\Payment\Model\Method\MyCustomDebug`이(가) `debug` 클래스의 `$logger` 속성의 `Magento\Payment\Model\Method\Logger` 처리기에 삽입되었습니다.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

예외 메시지가 `/var/log/payment.log` 파일에 기록됩니다.

## 로거 처리기 클래스에서 사용자 지정 로그 파일 설정

이 예제에서는 사용자 지정 로거 처리기 클래스를 사용하여 `error`개의 메시지를 특정 로그 파일에 기록하는 방법을 보여 줍니다.

1. 데이터를 기록하는 클래스를 만듭니다. 이 예제에서 클래스는 `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`에 정의되어 있습니다.

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

1. 이 클래스의 핸들러를 모듈의 [ 파일에서 ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types)가상 형식`di.xml`(으)로 정의합니다.

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger`은(는) 고유 식별자입니다.

1. `type` 정의에서 사용자 지정 로거 처리기를 삽입할 클래스 이름을 지정합니다. 이전 단계의 가상 형식 이름을 이 형식의 인수로 사용합니다.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   `Vendor\ModuleName\Observer\MyObserver` 클래스의 Source 코드:

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

1. 클래스 `Vendor\ModuleName\Logger\Handler\ErrorHandler`이(가) `error`에서 `$logger` 속성의 `Vendor\ModuleName\Observer\MyObserver` 처리기에 삽입되었습니다.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

예외 메시지가 `/var/log/my_custom_logger/error.log` 파일에 기록됩니다.

