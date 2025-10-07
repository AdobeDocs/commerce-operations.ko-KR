---
title: 배포 플로우
description: Adobe Commerce 프로덕션 환경의 배포 흐름 프로세스에 대해 알아봅니다. 성능과 안정성을 극대화하는 단계를 살펴보십시오.
feature: Best Practices, Deploy
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# 배포 흐름

[!DNL Commerce] 프로덕션 배포 흐름은 스토어가 최대 성능에 도달하도록 도와줍니다.

## 종속성 설치

`composer.json` 및 `composer.lock` 파일은 [!DNL Commerce] 종속성을 관리하고 각 패키지에 적절한 버전을 설치합니다. [자동 로더](#preprocess-dependency-injection-instructions)를 업데이트하려면 [사전 처리 종속성 삽입 지침](#update-the-autoloader) 전에 종속성을 설치해야 합니다.

[!DNL Commerce] 종속성을 설치하려면:

```bash
composer install --no-dev
```

## 종속성 삽입 지침 전처리

종속성 삽입(DI) 지침을 전처리하고 컴파일하는 경우 Magento은

* 모든 현재 구성을 읽고 처리합니다.
* 클래스 간 종속성 분석
* 자동으로 생성된 파일(프록시, 팩토리 등 포함) 생성
* 컴파일된 데이터 및 구성을 캐시에 저장하여 요청 처리 시간을 최대 25% 절약

DI 지시사항을 미리 처리하고 컴파일하려면

```bash
bin/magento setup:di:compile
```

## 자동 로더 업데이트

컴파일이 완료된 후 [APCu가 활성화되었는지 확인](../performance/software.md#php-settings)하고 자동 로더를 업데이트하십시오.

자동로더를 갱신하려면

>[!INFO]
>
>`-o` 옵션은 PSR-0/4 자동 로드를 classmap으로 전환하여 더 빠른 자동 로더를 가져옵니다. `--apcu` 옵션은 APCu를 사용하여 찾은 클래스/찾을 수 없는 클래스를 캐시합니다.

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

정적 콘텐츠를 배포하면 [!DNL Commerce]에서 다음 작업을 수행합니다.

* 모든 정적 리소스 분석
* 콘텐츠 병합, 최소화 및 번들링 수행
* 테마 데이터 읽기 및 처리
* 테마 대체 분석
* 추가 사용을 위해 처리된 모든 콘텐츠 및 구체화된 콘텐츠를 특정 폴더에 저장

정적 콘텐츠가 배포되지 않으면 [!DNL Commerce]에서 나열된 모든 작업을 즉시 수행하여 응답 시간이 크게 늘어납니다.

다양한 옵션을 사용하여 저장소 크기 및 이행 요구 사항에 따라 배포 작업을 사용자 지정할 수 있습니다. 가장 일반적인 방법은 소규모 배포 전략입니다. [정적 파일 배포 전략](../configuration/cli/static-view-file-strategy.md)을 참조하세요.

정적 콘텐츠를 배포하려면

```bash
bin/magento setup:static-content:deploy
```

이 명령을 사용하면 작성기가 프로젝트 파일에 대한 매핑을 다시 빌드하여 보다 빠르게 로드할 수 있습니다.

## 프로덕션 모드 설정

>[!INFO]
>
>모드를 프로덕션으로 설정하면 `setup:di:compile` 및 `setup:static-content:deploy`이(가) 자동으로 실행됩니다.

마지막으로 스토어를 프로덕션 모드로 전환해야 합니다. 프로덕션 모드는 특히 스토어의 최대 성능에 최적화되었습니다. 또한 모든 개발자별 기능을 비활성화합니다. 이 작업은 `.htaccess` 또는 `nginx.conf` 파일에서 수행할 수 있습니다.

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
