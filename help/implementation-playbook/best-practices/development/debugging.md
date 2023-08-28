---
title: 디버깅 모범 사례
description: 일반적인 Adobe Commerce 개발 문제를 해결하기 위한 기술에 대해 알아봅니다.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---


# Adobe Commerce에 대한 디버깅 모범 사례

이 항목에서는 Adobe Commerce 프레임워크를 체계적이고 효과적으로 디버깅하는 방법을 설명합니다. 문제의 뿌리를 빨리 찾아내고 조사 시간을 최소화하도록 돕는 게 목표다.

## 문제 해결: 일반적인 문제 해결

이 섹션에서는 개발 중에 발생할 수 있는 가장 일반적인 문제에 대해 설명합니다.

### 캐시

- 추가 조사 전에 캐시 초기화
- APC 캐시, CDN, Vannish, 생성된 코드 및 `var/view_preprocessed` 및 `pub/static/` 디렉터리
- 캐시를 플러시하거나 코드를 수정한 후 큐 핸들러를 중지했다가 다시 시작합니다.

다음 코드 샘플은 캐시 관리와 관련된 유용한 명령을 제공합니다(프로덕션 환경에서는 실행하지 마십시오).

```bash
# restart php-fpm to flush APC
sudo service php-fpm restart
 
# restart varnish to force full flush
sudo service varnish restart
 
# clear generated files
rm -rf generated/*
 
# clear static file cache
rm -rf var/view_preprocessed/*
rm -rf pub/static/*
 
# flush redis cache
redis-cli -n <db_number> FLUSHDB
 
# flush redis cache and sessions
redis-cli FLUSHALL
 
# flush redis cache with telnet
telnet <ip_or_host> 6379
SELECT <db_number>
FLUSHDB
Ctrl + ]
quit
 
# flush redis cache and sessions with telnet
telnet <ip_or_host> 6379
FLUSHALL
Ctrl + ]
quit
 
# find consumers
pgrep -af queue:consumers:start
 
# kill all queue consumers (they will restart by cron job)
sudo pkill -f queue:consumers:start
 
# kill a specific queue consumer (it will restart by cron job)
sudo kill <process_id>
```

### 인덱싱된 데이터

문제가 색인과 관련될 수 있는 경우 모든 항목을 다시 색인화합니다. 인덱싱된 데이터 디버깅은 일반적으로 비프로덕션 환경에서 수행됩니다. 프로덕션 환경에서는 다시 인덱싱하기 전에 인덱스 오정렬의 원점을 조사할 수 있습니다. 고장 상태의 특징이 문제의 원인을 말해 줄 수 있다.

### 작성기

분기 변경 또는 이전 디버깅 작업에서 편집된 코어 파일로 인해 오래된 코드가 있을 수 있습니다. 잠재적인 문제를 해결하려면 다음 명령을 실행합니다.

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### 생성된 콘텐츠

JS, CSS, 이미지, 번역 및 기타 파일에서 생성된 콘텐츠를 디버깅하기 전에 프론트엔드 파일을 다시 빌드합니다.

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### 개발자 모드

로컬 설치가에 있는지 확인합니다. `developer` 모드.

### 새 모듈

모듈을 만든 경우 다음 문제를 확인하십시오.

- 모듈이 활성화되었습니까?

  ```bash
  bin/magento module --enable Your_Module
  ```

  다음 확인: `app/etc/config.php` 새 모듈에 대한 파일입니다.

- 파일 및 디렉터리 구조 중첩을 확인합니다. 예를 들어 은 `view/layout/` 디렉토리 대신 `view/frontend/layout` 디렉토리? 다음에 템플릿이 있음 `view/frontend/template` 디렉토리 대신 `view/frontend/templates` 디렉토리?

## 문제 해결: 절반 분할

일반적인 의심자가 문제에 대한 해결책을 제시하지 않는 경우, 가장 빨리 진행할 수 있는 방법은 문제를 반으로 쪼개거나(또는 이중으로 쪼개어) 진행하는 것입니다. 이 방법을 사용하면 선형 방식으로 코드를 거치는 대신 큰 청크를 제거하고 남은 내용을 분할하여 근본 원인을 찾을 수 있습니다.

다음 다이어그램을 참조하십시오.

![이등분 다이어그램](../../../assets/playbooks/bisect.png)

![이등분 다이어그램](../../../assets/playbooks/bisect2.png)

몇 가지 방법으로 양분할 수 있지만 Adobe은 다음 순서를 따를 것을 권장합니다.

- 주제별 이등분
- 커밋별 이등분
- 파일별 이등분

### 1단계: 주제별 이등분

코드와 관련이 없는 문제인 경우 먼저 큰 청크를 제거하십시오. 생각해 볼 수 있는 큰 덩어리 중 일부는 다음과 같습니다.

- **Adobe Commerce 프레임워크**—Adobe Commerce과 관련된 문제입니까? 아니면 연결된 다른 시스템과 관련된 문제입니까?
- **서버 및 클라이언트**- 브라우저 캐시와 저장소를 지웁니다. 문제가 해결되었습니까? 이로 인해 서버 관련 문제가 발생할 수 있습니다. 문제가 여전히 존재합니까? 브라우저 디버깅에 더 이상 시간을 낭비할 필요가 없습니다.
- **세션**—모든 사용자에 대해 문제가 발생합니까? 그렇지 않으면 세션 또는 브라우저 관련 주제로 문제를 제한할 수 있습니다.
- **캐시**—모든 캐시를 비활성화하면 변경 사항이 있습니까? 이 경우 캐시 관련 항목에 중점을 둘 수 있습니다.
- **데이터베이스**—동일한 코드를 실행하는 모든 환경에서 문제가 발생합니까? 그렇지 않은 경우 구성 및 기타 데이터베이스 관련 항목에서 문제를 찾습니다.
- **코드**—위의 방법 중 어느 방법으로도 문제가 해결되지 않은 경우 코드 문제를 찾습니다.

### 2단계: 커밋별 이등분

지금부터 2개월 전 사이에 문제가 시작된 경우 코드를 2개월 전으로 되돌립니다. 문제가 여전히 존재하는지 확인합니다. 앞으로 한 달. 거기서 문제가 발생합니까? 그렇지 않다면 2주 앞으로 나아가세요. 지금 발생합니까? 1주일 전으로 돌아가세요. 아직 있어? 4일 전으로 돌아가십시오. 어느 시점에서 문제와 관련된 코드가 포함되어 있을 수 있는 커밋이 하나만 남습니다. 이제 근본 원인은 해당 커밋에서 편집된 파일로 제한될 수 있습니다.

주 및 일을 커밋으로 대체할 수 있습니다. 예를 들어, 롤백 100개, 포워드 50개, 포워드 25개, 백 12개의 커밋이 있습니다.

### 3단계: 파일별 이등분

- Adobe Commerce을 파일 형식(코어 및 비코어)으로 나눕니다. 먼저 모든 고객 및 마켓 플레이스 모듈을 비활성화합니다. 문제가 여전히 존재합니까? 이는 핵심 문제가 아닌 문제일 가능성이 높습니다.
- 에서 모듈의 절반(대략)을 다시 활성화합니다. `app/etc/config.php` 파일. 종속성에 유의하십시오. 한 번에 동일한 주제의 모듈 클러스터를 활성화하는 것이 가장 좋습니다. 문제가 여전히 존재합니까?
- 나머지 모듈의 1/4을 활성화합니다. 문제가 여전히 존재합니까? 활성화한 항목의 절반을 비활성화합니다. 이 방법을 사용하면 근본 원인을 단일 모듈로 분리할 수 있습니다.

## 시간 절약

문제 해결 기법 외에도 이 섹션에서는 디버깅 중에 시간을 절약하는 데 도움이 되는 몇 가지 일반 규칙을 제공합니다.

### 데이터 제한

문제를 복제하기 위해 전체 카탈로그 보기가 필요한지 아니면 모든 스토어 보기가 필요한지 여부를 고려합니다. 디버깅을 시작하기 전에 카탈로그의 95%를 제거한 데이터베이스 클론에서 인덱싱 문제를 디버깅할 수 있습니다. 이 방법을 사용하면 색인화 프로세스 중에 시간이 많이 절약됩니다. 저장소 수와 카탈로그가 줄어든 클라이언트 데이터베이스의 복제본을 만듭니다. 이는 디버깅 중인 영역에 따라 다른 엔티티(예: 고객)에도 적용될 수 있습니다.

### 추가 정보 요청

때로는 모든 코드와 기술 작업 중에 잊기 쉬운 단계입니다. 자세한 정보를 요청하십시오. 전체 화면 캡처, 비디오, 문제를 식별한 사람과의 화상 회의 채팅, 복제 단계, 문제 이벤트 주변에서 다른 겉보기에 중요하지 않은 일이 발생했는지 여부에 대한 질문. 어떤 사람이 일어날 것으로 예상했는지 물어보십시오. 이것이 정말 버그입니까 아니면 코드가 작동하는 방식에 대한 오해에 불과한 것입니까?

### 언어 및 통역

문제에 대한 설명이 명확합니까? 어떤 용어나 설명도 여러 가지 방법으로 해석될 수 없는 것이 확실합니까? 만약 그렇다면, 여러분이 같은 것에 대해 말하고 있는지 확인하십시오.

### 인터넷 검색

문제와 관련된 용어를 사용하여 인터넷 검색을 수행합니다. 다른 사용자가 이미 동일한 문제를 겪었을 가능성이 있습니다. 다음을 통해 검색 [Adobe Commerce GitHub 문제](https://github.com/magento/magento2/issues).

### 휴식을 취하세요

너무 오랫동안 문제를 바라보고 있다면, 해결책을 찾는 것이 어려울 수 있다. 일을 접고 다른 일을 하거나 산책을 하세요. 그 문제에 대해 잠시 잊었다가 답이 나올 수도 있다.

## 도구

n98 magerun CLI 도구([https://github.com/netz98/n98-magerun2](https://github.com/netz98/n98-magerun2))는 명령줄에서 Adobe Commerce을 사용하는 데 유용한 기능을 제공합니다. 특히 다음 명령을 사용합니다.

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## 코드 조각

다음 항목에서는 Commerce 프로젝트에서 문제를 기록하거나 식별하는 데 사용할 수 있는 코드 조각을 제공합니다.

### Commerce에서 XML 파일을 사용하고 있는지 확인

XML 파일에 명백한 구문 오류를 추가하여 사용 여부를 확인합니다. 태그를 열고 예를 들어 닫지 마십시오.

```xml
<?xml version="1.0"?>
<test
```

이 파일을 사용하면 오류가 발생합니다. 그렇지 않으면 모듈이 사용되지 않거나 활성화되어 있지 않거나 XML 파일이 잘못된 위치에 있을 수 있습니다.

### 로깅

>[!BEGINTABS]

>[!TAB Adobe Commerce]

```php
\Magento\Framework\App\ObjectManager::getInstance()
    ->get(\Psr\Log\LoggerInterface::class)->debug('message');
```

>[!TAB 독백]

```php
$log = new \Monolog\Logger('custom', [new \Monolog\Handler\StreamHandler(BP.'/var/log/test.log')]);
$log->info('Your Logging Message', ['context' => ['email' => 'john@example.com']]);
```

>[!TAB 젠드]

```php
$writer = new \Zend\Log\Writer\Stream(BP . '/var/log/test.log');
$logger = new \Zend\Log\Logger();
$logger->addWriter($writer);
$logger->info('Your text message');
$logger->info(print_r($yourArray, true));
```

>[!ENDTABS]

### 낮은 수준의 로깅

PHP 파일에서 항상 작동하는 두 가지 예입니다.

```php
file_put_contents('/var/www/html/var/log/example.log', "example line\n", FILE_APPEND);
file_put_contents('/var/www/html/var/log/example.log', print_r($yourArray, true) . "\n", FILE_APPEND);
```

스택 추적의 경우:

```php
try {
    throw new \Exception('example');
} catch (\Exception $e) {
    file_put_contents('/var/www/html/var/log/example.log', $e->getTraceAsString() . "\n", FILE_APPEND);
}
```
