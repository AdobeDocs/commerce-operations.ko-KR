---
title: 코어 및 타사 PHP 코드 수정 우수 사례
description: 핵심 Adobe Commerce 및 타사 PHP 코드를 수정하는 방법과 시기를 알아봅니다.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
exl-id: 32b3137d-fc00-4be8-ba02-5d8d48a51fe1
source-git-commit: d47567a8d69ccdae3db01e964f1db12e8ae26717
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# 핵심 및 타사 PHP 코드를 수정하거나 재정의하는 우수 사례

이 문서에서는 작성하지 않았거나 직접 제어하지 않은 코드의 기능, 결과 또는 입력을 수정해야 하는 경우의 모범 사례에 대해 설명합니다. 즉, 코어 코드와 타사 코드가 있습니다. 이 문서는 주로 백엔드 PHP 코드에 초점을 맞춥니다.

## 코드 수정 방법

코드를 수정할 때는 변경 사항의 범위를 고려하는 것이 중요합니다. 변경 사항의 &quot;범위&quot;는 코드 변경의 효과가 어디까지 미치는지를 나타냅니다. 가장 좋은 방법은 가장 작은 풋프린트와 가장 적은 리소스 사용량을 갖는 옵션을 기반으로 최종 구현 완료 방법을 결정하는 것입니다. 코드 재정의가 광범위할수록 개발 팀이 핵심 Adobe Commerce 기능에서 더 많이 이탈하여 버그가 발생할 가능성이 높아지고 향후 코드 베이스를 유지 관리하기 위한 노력이 증가합니다.

### 패치

패치는 개발 팀의 직접 제어 하에 있지 않은 파일 내에서 코드를 직접 변경하는 지침이 포함된 파일입니다. 다른 옵션이 존재하지 않을 때 일반적으로 최후의 수단으로 고려되어야 하는 옵션이다. 패치는 임시 해결책입니다. 일반적인 모범 사례로서 패치를 만들어야 하는 경우 2~4주 이내에 보다 영구적인 솔루션을 위해 패치를 제거합니다. 

반점은 쉽게 부러집니다. 패치를 대상으로 하는 파일이 업데이트되면 종종 패치의 작동이 중지됩니다. 패치 파일에는 패치가 변경할 내용을 구체적으로 나타내는 행 번호와 열 번호가 포함되어 있기 때문입니다. 패치가 예상한 내용과 일치하지 않는 사항이 있으면 적용이 중지되고 코드가 중단됩니다.

```bash
diff --git a/vendor/magento/module-quote/Model/QuoteManagement.php b/vendor/magento/module-quote/Model/QuoteManagement.php
index 51b68411d40..ac4a3468322 100644
--- a/vendor/magento/module-quote/Model/QuoteManagement.php
+++ b/vendor/magento/module-quote/Model/QuoteManagement.php
@@ -424,8 +424,9 @@ class QuoteManagement implements CartManagementInterface
                 }
             }
             $quote->setCustomerIsGuest(true);
-            $groupId = $customer ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID;
-            $quote->setCustomerGroupId($groupId);
+            $quote->setCustomerGroupId(
+                $quote->getCustomerId() ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID
+            );
         }
  
         $remoteAddress = $this->remoteAddress->getRemoteAddress();
```

#### 패치를 사용하여 변경할 수 있는 사항

아무거나 문자 그대로 타겟팅된 파일 내의 모든 문자를 변경할 수 있습니다. 패치는 특정 파일 형식이나 코드 언어로 제한되지 않습니다. 일반적으로 패치를 사용하여 `vendor` 디렉터리 내의 파일을 타겟팅합니다. 

#### 패치 사용 시기

다른 옵션이 없음을 알고 있는 경우 예를 들어 공급업체가 아직 코드에 대한 수정 사항을 게시하지 않은 경우 영구적인 솔루션을 기다리는 동안 패치를 사용하여 문제를 일시적으로 해결할 수 있습니다.

#### 단점

반점은 쉽게 부러집니다. 대상 코드가 변경되는 순간 패치가 작동하지 않습니다. 그것들은 단지 단기적인 해결책일 뿐입니다.

### 환경 설정

환경 설정은 Adobe Commerce 플랫폼으로 설계된 개념입니다. 그것은 본질적으로 &quot;PHP 클래스 대체&quot;입니다.

기존 PHP 응용 프로그램에서 수행되는 것처럼 새 키워드를 사용하여 PHP 클래스를 인스턴스화하지 않으므로 Adobe Commerce 플랫폼에서는 &quot;개체 관리자&quot;를 사용하여 PHP 클래스를 인스턴스화합니다. 대신 개체 관리자는 컴파일된 구성에 대해 인스턴스화할 PHP 클래스의 이름을 상호 참조하여 모듈이 원래 클래스에 대한 기본 설정을 선언했는지 확인합니다. PHP 클래스에 대한 기본 설정이 있으면 개체 관리자가 지정된 클래스를 대신 인스턴스화합니다.

(일반적으로) 원래 PHP 클래스를 대체하는 새로운 PHP 클래스는 원래 PHP 클래스에서 확장/상속됩니다. 이 작업은 다음 두 가지 이유로 수행됩니다.

- 종속성 삽입/유형 힌트를 준수하는지 확인하기 위해 그렇지 않으면 치명적인 오류가 발생하여 애플리케이션이 중단됩니다.
- 최소한의 코드 쓰기를 허용합니다. 원래 PHP 클래스에 10개의 메서드가 포함되어 있지만 한 메서드만 재정의하면 되는 경우에는 일반적으로 한 메서드를 변경하고 다른 9개의 메서드는 그대로 둘 수 있습니다. 플랫폼이 새 버전으로 업그레이드될 때 핵심 기능에 대한 업데이트가 차단되지 않도록 하는 것이 중요합니다.

#### 환경 설정 선언

환경 설정을 선언하는 것은 매우 간단한 프로세스입니다. 단일 코드 행을 모듈 내의 `di.xml` 파일에 추가해야 합니다. 이 작업은 전역적으로 수행하거나 `frontend`, `adminhtml`, `graphql`, `webapi_rest` 및 `crontab`과(와) 같은 모든 Adobe Commerce &quot;영역&quot; 내에서 수행할 수 있습니다.

```xml
<preference for="Magento\Elasticsearch7\SearchAdapter\Adapter" type="Vendor\Namespace\Adapter\AlgoliaElasticSearch7Adapter"/>
```

```php
<?php

declare(strict_types=1);

namespace Vendor\Namespace\Adapter;

class AlgoliaElasticSearchAdapter extends \Magento\Elasticsearch7\SearchAdapter\Adapter
{
}
```

#### 기본 설정으로 변경할 수 있는 사항

PHP 클래스만 기본 설정으로 재정의할 수 있습니다. PHP 클래스 내에서 공용 및 보호된 메서드와 속성을 수정할 수 있습니다. public 및 protected 메서드의 경우 메서드를 완전히 재정의하거나 원래 상위 메서드로 들어가는 인수(또는 그 결과물)를 수정할 수 있습니다.

비공개 메서드는 기술적으로 재정의할 수 없습니다. 그러나 원래 비공개 방법에 대한 대체 요소를 직접 만들 수 있습니다. 임의의 이름을 지정할 수도 있으며 원래 이름을 사용할 수도 있습니다. 비공개 메서드는 이 메서드가 포함된 실제 파일 내에만 있으므로 문제가 되지 않습니다. private 메서드를 재정의하려면 원래 private 메서드를 호출하는 public 또는 protected 메서드를 재정의하거나 수정해야 하며 그 대신 자체 기능을 대체해야 합니다.

#### 기본 설정을 사용해야 하는 경우

다른 옵션이 존재하지 않고 종속성 삽입, 플러그인 또는 관찰자로 목표를 달성할 수 없는 경우 환경 설정을 다시 한 번 사용해야 합니다. 개인 또는 보호된 메서드나 속성을 수정하거나 재정의해야 하는 경우 환경 설정이 필요할 수 있습니다. 환경 설정은 제한적으로 사용해야 합니다. 그들은 응용 프로그램을 변경하는 상당히 &quot;탐욕스러운&quot; 방법이며 효과적으로 PHP 클래스의 소유권을 가져옵니다. 이로 인해 타사 모듈과의 충돌이 발생할 수 있으며 핵심 클래스에 대한 업데이트가 차단되고 버그 진단이 어려울 수 있습니다. Adobe Commerce 플랫폼은 더 적은 풋프린트로 기본 코드를 변경할 수 있는 다른 방법을 포함하도록 설계되었습니다.

#### 단점

환경 설정은 코드를 수정하는 탐욕스러운 방법이며 다른 옵션이 없는 경우에만 사용해야 합니다. 환경 설정은 종종 코드 베이스 내에서 충돌을 야기할 수 있으며, 더 나아가 플랫폼 업그레이드와 함께 발생하는 핵심 업데이트를 차단할 수 있습니다. 

### 관찰자

관찰자는 많은 애플리케이션, 플랫폼, 라이브러리 및 코딩 언어에서 볼 수 있는 이벤트 리스너의 개념입니다. 이 개념은 Adobe Commerce 플랫폼에만 국한되지 않습니다. 관찰자는 Magento 1 이후 플랫폼에 통합되었으며 핵심 코드와 타사 코드를 수정하는 방법에 대한 주요 선택으로 간주됩니다. 

코어 코드 베이스 및 모든 서드파티 모듈은 코드에서 선택한 위치에 이벤트를 발송할 수 있습니다. `events.xml` 파일에서 선언되고 이름으로 발송된 이벤트를 수신 중인 관찰자는 전역 수준에서 작동하거나 `frontend`, `adminhtml`, `graphql`, `webapi_rest` 및 `crontab`과(와) 같은 Adobe Commerce &quot;영역&quot;으로 제한될 수 있습니다.

#### 관찰자를 선언하는 방법

전역 또는 영역별 `events.xml` 파일에서 관찰자를 구성할 수 있습니다.

```xml
    <event name="sales_model_service_quote_submit_before">
        <observer name="set_reward_flag_order" instance="Adobe\RewardAdjustments\Observer\SetOrderRewardFlag" />
    </event>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\RewardAdjustments\Observer;

use Magento\Framework\Event\ObserverInterface;
use Magento\Framework\Event\Observer;
use Magento\Quote\Model\Quote;
use Magento\Sales\Api\Data\OrderInterface;

class SetOrderRewardFlag implements ObserverInterface
{
    /**
     * @param Observer $observer
     * @return void
     */
    public function execute(Observer $observer)
    {
        $event = $observer->getEvent();
        /* @var $order OrderInterface */
        $order = $event->getOrder();
        /** @var $quote Quote $quote */
        $quote = $event->getQuote();

        // do something to the order and/or quote object here
    }
}
```

#### 관찰자가 변경할 수 있는 사항

관찰자는 Adobe Commerce 플랫폼 내의 PHP 코드에만 적용됩니다. 이벤트 발송과 함께 전달된 특정 데이터 및 개체만 수정할 수 있습니다.

#### 관찰자를 사용해야 하는 경우

언제든 가능합니다! 관찰자가 더 광범위하고 융통성 있다면, 관찰자는 이 목록에서 2위 자리를 차지할 것이다. 관찰자는 플러그인보다 처리 오버헤드가 적고, 가용성이 낮고 유연성이 떨어집니다.

#### 단점

관찰자는 코드를 가로채고 수정하는 훌륭한 방법이지만, 이벤트 발송은 코드가 수신할 수 있도록 핵심 또는 타사 코드에 추가해야 합니다. 이로 인해 관찰자 사용의 개념이 다소 제한적이다. 개발자가 선견지명을 가지고 코드에 포함하는 이벤트로 제한됩니다.

또한 관찰자의 또 다른 제한 요소는 발송된 이벤트가 개발자가 이벤트와 함께 전달하기로 한 특정 데이터 및 오브젝트에 대한 액세스만 제공한다는 것입니다.

### 플러그인

플러그인은 Adobe Commerce 플랫폼에 도입된 유연한 개념입니다. 이를 통해 모든 공개 PHP 메서드를 가로채고, 바꾸고, 수정할 수 있습니다. 플러그인을 사용하면 타깃팅된 메서드가 실행되기 전에 메서드로 이동하는 인수를 수정하거나, 타깃팅된 메서드가 실행된 후에 결과를 수정하거나, 타깃팅된 메서드를 완전히 대체할 수 있습니다. 단일 플러그인 파일 내에서 타깃팅된 PHP 클래스의 여러 메서드를 수정할 수 있습니다. 또한 `$subject` 인수를 사용하여 대상 PHP 클래스에 있는 모든 공용 메서드를 실행할 수 있습니다.

#### 플러그인을 선언하는 방법

전역 또는 영역별 `di.xml` 파일에서 플러그인을 구성할 수 있습니다.

```xml
    <type name="Magento\Catalog\Api\CategoryRepositoryInterface">
        <plugin name="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin" type="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin"/>
    </type>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\CatalogAdjustments\Plugin;

class CategoryRepositoryPlugin
{
    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param int $categoryId
     * @param int $storeId
     *
     * @return array
     */
    public function beforeGet($subject, $categoryId, $storeId = null): array
    {
        // modify the $categoryId or $storeId arguments or perform some other functionality prior to execution of the `get` method
        return [$categoryId, $storeId];
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Closure $origMethod
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function aroundGet($subject, $origMethod, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you can do something before calling the original method
        $result = $origMethod($categoryId, $storeId);
        // here you can do something after calling the original method
        // you can also NOT call the original method at all and instead, substitute our own functionality

        return $result;
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Magento\Catalog\Api\Data\CategoryInterface $result
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function afterGet($subject, $result, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you modify the result produced by the original `get` function or you can execute some other functionality
        // note that you also have access to the original function arguments. it's too late to modify them, but if needed, they are available for reading

        return $result;
    }
}
```

#### 플러그인으로 변경할 수 있는 사항

이 기능은 PHP 클래스를 대상으로 하는 경우에만 사용할 수 있습니다. 공개 메서드의 입력 또는 출력을 변경할 수 있으며 플러그인을 사용하여 다른 기능을 트리거할 수 있습니다. 여러 플러그인이 동일한 PHP 클래스를 대상으로 하는 경우 플러그인 실행에 대한 정렬 순서를 설정하여 플러그인이 다른 플러그인 전후에 실행되도록 할 수 있습니다.

#### 플러그인을 사용해야 하는 경우

종속성 대체를 사용할 수 없을 때마다 플러그인은 핵심 코드베이스, 타사 코드 전체에서 일반적으로 사용되며 사용자 지정 코드에서 일반적으로 사용할 수 있습니다. 일반적으로 사용자 지정 코드에서 소유하거나 제어하지 않는 기능을 수정해야 하는 경우 플러그인을 사용하는 것이 좋습니다.

#### 단점

보호된 메서드 또는 속성은 수정할 수 없습니다. 처리 오버헤드가 관찰자의 처리 오버헤드보다 높습니다. 플러그인을 사용하지 말라는 것은 중요한 논쟁이 아닙니다. 그 차이는 사소한 것입니다. 하지만, 이것은 기억해야 할 좋은 것이다.

### 종속성 대체

종속성 삽입은 생성자가 있는 클래스에 필요한 종속성을 전달하는 표준 개체 지향 코딩 개념입니다. 그러나 Adobe Commerce 플랫폼은 종속성을 XML로 대체할 수 있는 다양한 경로를 제공하여 이 작업을 한 단계 더 발전시킵니다. 기본적으로 종속성 대체입니다. 종속성 대체 기능은 모든 상황에 적합하지 않지만 최소한의 코드 작성과 낮은 오버헤드를 허용하며 정확한 코드 조각만 좁게 타깃팅할 수 있습니다. 종속성 대체 기능을 사용하여 개인 및 보호된 메서드를 수정할 수 있습니다.

#### 종속성 대체 사용 방법

의존성 교체는 전 세계적으로 또는 영역별로 수행할 수 있습니다.

```php
<?php

class SomeClass
{
    public function __construct(
        private readonly AllowedCountries $allowedCountriesReader
    ) {}

    /**
     * Check is address allowed for store
     *
     * @param AddressInterface $address
     * @param int|null $storeId
     * @return bool
     */
    private function isAddressAllowedForWebsite(AddressInterface $address, $storeId): bool
    {
        $allowedCountries = $this->allowedCountriesReader->getAllowedCountries(ScopeInterface::SCOPE_STORE, $storeId);

        return in_array($address->getCountryId(), $allowedCountries);
    }
}
```

```php
<?php

use Magento\Store\Model\ScopeInterface;

class OverrideAllowedCountries extends AllowedCountries
{
    /**
     * Retrieve all allowed countries for scope or scopes
     *
     * @param string $scope
     * @param string|null $scopeCode
     * @return array
     * @since 100.1.2
     */
    public function getAllowedCountries(
        $scope = ScopeInterface::SCOPE_WEBSITE,
        $scopeCode = null
    ) {
        // do some stuff here
        // you can call the original method or override it completely
        
        return $something;
    }
}
```

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Vendor\Namespace\SomeClass">
        <arguments>
            <argument name="allowedCountriesReader" xsi:type="object">OverrideAllowedCountries</argument>
        </arguments>
    </type>
</config>
```

이 단계를 수행하면 전용 메서드의 동작이 정상적으로 수정됩니다.

#### 종속성 대체 시 변경할 수 있는 사항

공개, 보호 및 비공개 방법은 종속성 대체와 함께 변경할 수 있습니다. 플러그인과 마찬가지로 들어오는 인수를 수정하거나, 함수를 완전히 대체하거나, 함수의 출력을 수정할 수 있습니다.

#### 종속성 대체 사용 시기

구현하기 위해 너무 복잡한 작업을 수행하지 않아도 된다고 가정하고 원하는 목표를 실제로 달성할 때 좋은 첫 번째 옵션입니다.

#### 단점

많지는 않아요. 모든 상황에서 사용할 수 있는 것은 아닙니다. 주요 단점은 수정할 기능이 포함된 원래 클래스를 확장해야 한다는 것입니다. 그것은 &quot;상속보다 구성&quot;의 원칙에 위배된다.
