---
title: 글로벌 참조 아키텍처 예
description: 대규모 Adobe Commerce 프로젝트에 대한 코드 관리 예를 참조하십시오.
role: Developer, Architect
level: Experienced
source-git-commit: 64f330919abab9644de1163c9a6d6501a9c50cc1
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---


# 글로벌 참조 아키텍처 예

이 항목에서는 를 구성하는 일반적인 방법을 설명합니다. [글로벌 참조 아키텍처(GRA)](overview.md) 코드 베이스입니다. 하지만 [개별 패키지](#option-1-separate-packages) 옵션이 선호되며, 일부 상황에서는 아래에 설명된 다른 옵션 중 하나를 필요로 합니다.

## 정의

{{$include /help/_includes/gra-definitions.md}}

## 옵션 1: 패키지 구분

다음을 참조하십시오 [작성기 프로젝트 구조](composer/project-structure.md) 이 메서드를 설정하는 모범 사례입니다.

![글로벌 참조 아키텍처에 대한 개별 패키지 옵션을 보여 주는 다이어그램](../../../assets/playbooks/gra-separate-packages.png)

GRA Composer 패키지를 관리하는 가장 유연한 방법은 메타패키지입니다. 메타패키지에는 다음이 포함됩니다. `composer.json` 다른 패키지 종속성을 정의하는 파일만. 다음을 사용하여 메타패키지 만들기 [비공개 패키지 사용자](https://packagist.com/) 리포지토리.

### 기본 프로젝트 `composer.json`

```json
{
    "name": "example-client/region-1",
    "description": "Example Client Region 1",
    "type": "project",
    "require": {
        "magento/product-enterprise-edition": "2.3.5",
        "example-client/meta-region-1": "~1.0"
    },
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": [
        {"type": "composer", "url": "https://repo.packagist.com/example-client/"},
        {"packagist.org": false}
    ]
}
```

### `example-client/meta-region-1 composer.json`

```json
{
    "name": "example-client/meta-region-1",
    "description": "Region 1 meta package",
    "type": "metapackage",
    "require": {
        "example-client/meta-gra": "~1.0",
        "example-client/theme-frontend-region1",
        "example-client/language-es-es",
        "ingenico/ogone-client"
    }
}
```

### `example-client/meta-gra composer.json`

```json
{
    "name": "example-client/meta-gra",
    "description": "GRA meta package",
    "type": "metapackage",
    "require": {
        "geoip2/geoip2": "~2.0",
        "magento-services/module-stackify-logger": "~1.1",
        "example-client/sap-connector",
        "example-client/service-chat",
        "example-client/store-locator"
    }
}
```

각 모듈, 언어 팩, 테마 및 라이브러리에는 자체 Git 저장소가 있습니다. 각 Git 저장소는 개인 패키지 목록 저장소에 자동으로 동기화되며, 가 있는 한 여기에서 패키지를 생성합니다. `composer.json` 파일은 Git 저장소의 루트에 있습니다.

## 옵션 2: 벌크 패키지

다음은 단일 Composer 패키지 내의 여러 모듈에 대한 예입니다.

벌크 패키지는 동일한 유형의 패키지만 포함할 수 있습니다. 예를 들어 Adobe Commerce 모듈, 테마, 언어 팩 및 라이브러리에 대한 패키지가 여러 개 있는 경우 각 유형에 대해 별도의 벌크 패키지를 만들어야 합니다.

공급업체 디렉토리 내의 파일 구조는 다음 예제와 같아야 합니다. 그러나 프로젝트를 확인하여 Git 저장소에 포함해야 하는 항목을 확인하십시오.)

```tree
.
└── example-client/
    └── gra/
        └── src/
            ├── SapConnector/
            │   ├── etc/
            │   └── registration.php
            ├── ServiceChat/
            │   ├── etc/
            │   └── registration.php
            ├── StoreLocator/
            │   ├── etc/
            │   └── registration.php
            └── composer.json
```

다음 `composer.json` 파일은 다음과 같아야 합니다.

```json
{
    "name": "example-client/gra",
    "description": "GRA Modules",
    "require": {
        "magento/magento-composer-installer": "*"
    },
    "type": "magento2-module",
    "autoload": {
        "files": [
            "src/SapConnector/registration.php",
            "src/ServiceChat/registration.php",
            "src/StoreLocator/registration.php"
        ],
        "psr-4": {
            "ExampleClient\\SapConnector\\": "src/SapConnector",
            "ExampleClient\\ServiceChat\\": "src/ServiceChat",
            "ExampleClient\\StoreLocator\\": "src/StoreLocator"
        }
    }
}
```

## 옵션 3: Git 분할

이 아키텍처는 4개의 Git 저장소를 사용하여 코드를 저장합니다.

- `core`: Adobe Commerce 핵심 설치가 포함되어 있습니다. Adobe Commerce 버전을 업그레이드하는 데 사용됩니다.
- `GRA`: GRA 코드를 포함합니다. 모든 GRA 모듈, 언어 팩, 화이트 라벨 테마 및 라이브러리.
- `brand/region`: 각 브랜드 또는 지역에는 브랜드 또는 지역별 코드만 있는 자체 저장소가 있습니다.
- `release`: 위의 모든 항목이 이 Git 저장소에 병합됩니다. 여기에서는 병합 커밋만 허용됩니다.

![글로벌 참조 아키텍처를 위한 분할 Git 옵션을 보여 주는 다이어그램](../../../assets/playbooks/gra-split-git.png)

이 옵션을 설정하려면 다음을 수행하십시오.

1. Git에서 네 가지 저장소 유형을 만듭니다. 만들기 `core` 및 `GRA` 저장소는 한 번만 사용합니다. 1개 만들기 `brand/region` 및 1 `release` 각 브랜드의 저장소입니다.

   제안된 저장소 이름:

   - `m2-core`
   - `m2-gra`
   - `m2-region-x`/`m2-brand-x` (예: `m2-emea`/`m2-adobe`)
   - `m2-release-region-x`/`m2-release-brand-x` (예: `m2-release-emea`/`m2-release-adobe`)

1. 만들기 `release/` 모든 저장소에 대한 공유 Git 기록을 만들려면 디렉토리를 지정하고 다음을 실행합니다.

   ```bash
   git init
   git remote add origin git@github.com:example-client/m2-release-brand-x.git
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   touch .gitkeep
   git add .gitkeep
   git commit -m 'initialize repository'
   git push -u origin master
   git push core master
   git push gra master
   git push region-x master
   ```

1. 다음을 제외하고 각 저장소 복제 `core`를 입력합니다.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   git clone git@github.com:example-client/m2-region-x.git
   git clone git@github.com:example-client/m2-gra.git
   ```

1. [Composer로 Adobe Commerce 설치](../../../installation/composer.md). 제거 `.gitignore` 파일, 추가 `core` 원격, 코드 추가 및 커밋, 푸시

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition m2-core
   cd m2-core
   git init
   rm .gitignore
   git remote add origin git@github.com:example-client/m2-core.git
   git fetch
   git checkout .gitkeep
   git add --all
   git commit -m 'install Adobe Commerce'
   git push
   ```

1. 다음에서 `GRA` 리포지토리에서 다음 디렉터리를 만듭니다.

   - `app/code/`
   - `app/design/`
   - `app/i18n/`
   - `lib/`

1. 코드를 추가합니다. 제거 `.gitignore` 파일, 코드 추가 및 커밋, 원격 추가 및 푸시

1. 다음에서 `brand/region` 리포지토리. 에서와 동일하게 수행 `GRA` 저장소는 파일이 고유해야 한다는 점을 기억하십시오. 이 저장소와 의 두 저장소에 동일한 파일을 포함할 수 없습니다. `GRA` 리포지토리.

1. 다음에서 `release` 리포지토리, 병합을 적용합니다.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   cd m2-release-brand-x
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

1. 제거 `.gitkeep` 파일.

1. 배포 `release` 프로덕션, 테스트, QA 및 개발 서버에 대한 저장소입니다. 업그레이드 중 `core`, `GRA`, 및 `brand` 코드는 다음 명령을 쉽게 실행할 수 있습니다.

   ```bash
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

## 옵션 4: Monorepo(권장)

이 전략은 Magento Open Source Git 저장소의 작동 방식을 거의 모방합니다.

모든 코드는 단일 저장소에서 개발 및 테스트됩니다. 자동화는 Composer를 사용하여 UAT 및 프로덕션 환경에 설치할 수 있는 이 단일 저장소에서 패키지를 분할합니다.

![글로벌 참조 아키텍처에 대한 Monorepo 옵션을 보여 주는 다이어그램](../../../assets/playbooks/gra-monorepo1.png)

모노레포 옵션을 사용하면 단일 저장소에서 쉽게 작업할 수 있을 뿐만 아니라 패키지를 사용하여 인스턴스를 유연하게 구성할 수 있습니다.

버전 관리 및 패키지 증류는 GitHub 작업 또는 GitLab 작업을 사용하여 자동화를 통해 수행됩니다.

![글로벌 참조 아키텍처에 대한 Monorepo 옵션을 보여 주는 다이어그램](../../../assets/playbooks/gra-monorepo2.png)

이 자동화에 대한 자세한 내용은 다음 리소스를 참조하십시오.

- [https://github.com/symplify/monorepo-builder](https://github.com/symplify/monorepo-builder)
- [https://github.com/danharrin/monorepo-split-github-action](https://github.com/danharrin/monorepo-split-github-action)

>[!TIP]
>
>모노리포를 설정하는 것은 진전되지만 가장 낮은 간접비로 가장 많은 유연성을 제공합니다.

## 전략을 혼합하지 마십시오.

GRA 패키지용 Composer와 를 사용하여 결합된 접근 방식을 사용하는 것은 권장되지 않습니다. `app/` 브랜드 또는 지역 패키지의 디렉터리입니다.

모든 항목을 가져올 수 있습니다. _장점_ 그러나 모두 _단점_ 두 가지 방법 중 하나를 선택할 수 있습니다. 둘 중 하나(Git 또는 Composer)를 선택하여 최적의 상태로 작업해야 합니다.

## 피해야 할 솔루션

- **GRA 또는 브랜드를 나타내는 모듈 이름 지정 규칙**

  GRA나 브랜드를 나타내는 명명 모듈은 유연성의 결여로 이어진다. 대신 작성기 메타패키지를 사용하여 모듈이 속한 그룹을 확인합니다. 예를 들어 고객 VF의 경우 패키지 `vf/meta-gra` 에는 모든 GRA 패키지에 대한 참조가 포함되어 있으며 `composer require vf/meta-gra` 명령입니다. 패키지 `vf/meta-kipling` 모든 Kipling 특정 패키지 및 `vf/meta-gra` 패키지. 모듈 이름은 로 지정됩니다. `vf/module-sales` 및 `vf/module-sap` 예. 이 명명 규칙을 사용하면 영향은 작지만 브랜드와 GRA 상태 간에 패키지를 이동할 수 있습니다.

- **인스턴스당 Adobe Commerce 코어 업그레이드**

  다양한 브랜드 또는 지역이 가능한 한 가깝게 실행되도록 패치 업그레이드를 포함한 Adobe Commerce 코어 업그레이드를 예약합니다. 공유 모듈에 대해 여러 Adobe Commerce 버전을 지원하면 호환성 제한으로 인해 모듈이 중단되고 유지 관리 작업이 두 배 이상 증가합니다. 정기적인 개발을 계속하기 전에 모든 인스턴스가 동일한 Adobe Commerce 버전에서 실행되고 있는지 확인하여 이러한 증가된 노력을 방지하십시오.
