---
title: 배포 플로우
description: 프로덕션 환경에 Adobe Commerce을 배포하는 데 필요한 단계에 대해 알아봅니다.
feature: Best Practices, Deploy
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# 배포 흐름

다음 [!DNL Commerce] 프로덕션 배포 흐름은 저장소가 최대 성능에 도달하도록 지원합니다.

## 종속성 설치

다음 `composer.json` 및 `composer.lock` 파일 관리 [!DNL Commerce] 종속성 을(를) 확인하고 각 패키지에 적절한 버전을 설치합니다. 먼저 종속성을 설치해야 합니다. [전처리 종속성 삽입 지침](#preprocess-dependency-injection-instructions) 을(를) 업데이트하려는 경우 [자동 로더](#update-the-autoloader).

설치하려면 [!DNL Commerce] 종속성:

```bash
composer install --no-dev
```

## 종속성 삽입 지침 전처리

종속성 삽입(DI) 지침을 전처리하고 컴파일하는 경우 Magento:

* 모든 현재 구성을 읽고 처리합니다.
* 클래스 간 종속성 분석
* 자동으로 생성된 파일(프록시, 팩토리 등 포함) 생성
* 컴파일된 데이터 및 구성을 캐시에 저장하여 요청 처리 시간을 최대 25% 절약

DI 지시사항을 미리 처리하고 컴파일하려면

```bash
bin/magento setup:di:compile
```

## 자동 로더 업데이트

컴파일이 완료된 후 다음을 확인합니다. [APCu가 활성화됨](../performance/software.md#php-settings) 및 자동로더를 업데이트합니다.

자동로더를 갱신하려면

>[!INFO]
>
>다음 `-o` 옵션은 PSR-0/4 자동 로드를 classmap으로 전환하여 더 빠른 자동 로더를 가져옵니다. 다음 `--apcu` option은 APCu를 사용하여 찾은 클래스/찾을 수 없는 클래스를 캐시합니다.

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

정적 콘텐츠 배포의 원인 [!DNL Commerce] 다음 작업을 수행하려면 다음과 같이 하십시오.

* 모든 정적 리소스 분석
* 콘텐츠 병합, 최소화 및 번들링 수행
* 테마 데이터 읽기 및 처리
* 테마 대체 분석
* 추가 사용을 위해 처리된 모든 콘텐츠 및 구체화된 콘텐츠를 특정 폴더에 저장

정적 콘텐츠가 배포되지 않은 경우 [!DNL Commerce] 나열된 모든 작업을 즉시 수행하여 응답 시간이 크게 증가합니다.

다양한 옵션을 사용하여 저장소 크기 및 이행 요구 사항에 따라 배포 작업을 사용자 지정할 수 있습니다. 가장 일반적인 방법은 소규모 배포 전략입니다. 다음을 참조하십시오 [정적 파일 배포 전략](../configuration/cli/static-view-file-strategy.md)

정적 콘텐츠를 배포하려면

```bash
bin/magento setup:static-content:deploy
```

이 명령을 사용하면 작성기가 프로젝트 파일에 대한 매핑을 다시 빌드하여 보다 빠르게 로드할 수 있습니다.

## 프로덕션 모드 설정

>[!INFO]
>
>모드를 프로덕션으로 설정하면 자동으로 실행됩니다 `setup:di:compile` 및 `setup:static-content:deploy`.

마지막으로 스토어를 프로덕션 모드로 전환해야 합니다. 프로덕션 모드는 특히 스토어의 최대 성능에 최적화되었습니다. 또한 모든 개발자별 기능을 비활성화합니다. 이 작업은 다음 위치에서 수행할 수 있습니다. `.htaccess` 또는 `nginx.conf` 파일:

`SetEnv MAGE_MODE production`

또한 하나의 CLI 명령에서 정적 콘텐츠를 배포하고, 콘텐츠를 컴파일하고, 모드를 설정할 수도 있습니다.

```bash
bin/magento deploy:mode:set production
```

이 명령은 백그라운드에서 실행되며 각 특정 단계에서 추가 옵션을 설정할 수 없습니다.

## 추가 실행 전 작업

이러한 단계가 권장되지만 필수는 아닙니다. 프로덕션 모드로 스토어를 시작하기 전에 바로 수행할 수 있습니다. 이 목록에는 다음이 포함됩니다.

* 인덱스에 일관되지 않은 데이터가 존재하지 않도록 데이터를 다시 색인화합니다.
* 캐시에 오래된 데이터나 잘못된 데이터가 남지 않도록 캐시를 플러시합니다.
* 가장 자주 사용되거나 중요한 저장소 페이지를 미리 호출하여 캐시에 대한 캐시가 생성 및 저장되도록 캐시를 준비합니다. 이 작업은 작은 스토어가 있는 경우 인터넷 크롤러를 사용하거나 수동으로 수행할 수 있습니다.
