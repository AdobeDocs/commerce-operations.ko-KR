---
title: 배포 흐름
description: '프로덕션 환경에서 Adobe Commerce 또는 Magento Open Source을 배포하는 데 필요한 단계에 대해 알아봅니다. '
source-git-commit: 9ab52374e031bd2b0a846dd5f47c89ff788dcafa
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# 배포 흐름

다음 [!DNL Commerce] 프로덕션 배포 플로우는 스토어가 최대 성능에 도달하도록 도와줍니다.

## 종속성 설치

다음 `composer.json` 및 `composer.lock` 파일 관리 [!DNL Commerce] 종속성을 설정하고 각 패키지에 적절한 버전을 설치합니다. 먼저 종속성을 설치해야 합니다 [종속성 주입 지침 처리](#preprocess-dependency-injection-instructions) 업데이트하려는 경우 [자동 로더](#update-the-autoloader).

설치하려면 [!DNL Commerce] 종속성:

```bash
composer install --no-dev
```

## 종속성 삽입 지침 사전 처리

ID(종속성 주입) 지침을 미리 처리하고 컴파일할 때 Magento:

* 현재 구성을 모두 읽고 처리합니다
* 클래스 간 종속성 분석
* 자동으로 생성된 파일(프록시, 공장 등 포함)을 생성합니다.
* 컴파일된 데이터 및 구성을 요청 처리 시 최대 25%의 시간을 저장하는 캐시에 저장

ID 지침을 미리 처리하고 컴파일하려면 다음을 수행하십시오.

```bash
bin/magento setup:di:compile
```

## 자동 로더 업데이트

컴파일이 완료되면 다음을 확인합니다. [APCu가 활성화됨](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html#php-settings) 자동 로더를 업데이트합니다.

자동 로더를 업데이트하려면:

>[!INFO]
>
>다음 `-o` 옵션은 PSR-0/4 자동 로드를 classmap으로 변환하여 더 빠른 자동 로더를 가져옵니다. 다음 `--apcu` 이 옵션은 APCu를 사용하여 발견되었거나 찾을 수 없는 클래스를 캐시합니다.

```bash
composer dump-autoload -o --apcu
```

자동 로더를 업데이트할 계획이라면 다음 명령을 순서대로 실행해야 합니다.

```bash
composer install --no-dev
```

```bash
bin/magento setup:di:compile
```

```bash
composer dump-autoload -o
```

```bash
bin/magento setup:static-content:deploy
```

## 정적 콘텐츠 배포

정적 콘텐츠 배포의 원인 [!DNL Commerce] 다음 작업을 수행하려면 다음을 수행하십시오.

* 모든 정적 리소스 분석
* 컨텐츠 병합, 최소화 및 번들링을 수행합니다
* 테마 데이터 읽기 및 처리
* 테마 대체 분석
* 추가 사용을 위해 처리된 모든 및 구체화된 컨텐츠를 특정 폴더에 저장

정적 콘텐츠가 배포되지 않으면, [!DNL Commerce] 나열된 모든 작업을 즉시 수행하므로 응답 시간이 크게 늘어납니다.

다양한 옵션을 사용하여 저장소 크기 및 이행 요구에 따라 배포 작업을 사용자 정의할 수 있습니다. 가장 일반적인 것은 컴팩트한 배포 전략입니다. 자세한 내용은 [정적 파일 배포 전략](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-static-deploy-strategies.html)

정적 콘텐츠를 배포하려면:

```bash
bin/magento setup:static-content:deploy
```

이 명령을 사용하면 Composer에서 프로젝트 파일에 대한 매핑을 다시 빌드하여 더 빠르게 로드할 수 있습니다.

## 프로덕션 모드 설정

>[!INFO]
>
>모드를 프로덕션으로 설정하면 자동으로 실행됩니다 `setup:di:compile` 및 `setup:static-content:deploy`.

마지막으로 스토어를 프로덕션 모드에 배치해야 합니다. 프로덕션 모드는 저장소의 최대 성능에 맞게 특별히 최적화되어 있습니다. 또한 모든 개발자별 기능을 비활성화합니다. 이 작업은 `.htaccess` 또는 `nginx.conf` 파일:

`SetEnv MAGE_MODE production`

정적 컨텐츠를 배포하고 컨텐츠를 컴파일한 다음 하나의 CLI 명령으로 모드를 설정할 수도 있습니다.

```bash
bin/magento deploy:mode:set production
```

명령은 백그라운드에서 실행되며 특정 단계마다 추가 옵션을 설정할 수 없습니다.

## 추가적인 사전 실행 작업

이러한 단계는 권장되지만 필수는 아닙니다. 프로덕션 모드에서 스토어를 시작하기 전에 즉시 수행할 수 있습니다. 이 목록에는 다음 사항이 포함됩니다.

* 인덱스에 일관되지 않은 데이터가 없도록 데이터를 다시 색인화합니다.
* 캐시에 오래된 데이터나 잘못된 데이터가 남아 있지 않도록 캐시를 플러시합니다.
* 가장 방문 빈도가 높거나 중요한 저장소 페이지를 미리 호출하는 캐시를 준비하여 캐시에 대한 캐시가 생성되어 저장됩니다. 이 작업은 임의의 인터넷 Crawler를 사용하여 수행하거나 작은 저장소가 있는 경우 수동으로 수행할 수 있습니다.
