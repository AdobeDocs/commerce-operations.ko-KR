---
title: 작성기 프로젝트 구조
description: 글로벌 참조 아키텍처 예제에 설명된 개별 패키지 옵션을 설정하고 유지 관리하는 방법에 대해 알아봅니다.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 8757d5b8-8309-452f-bfb3-1188a816d14f
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 작성기 프로젝트 구조

이 안내서에서는 GRA(전역 참조 아키텍처) 예제에 설명된 [개별 패키지 옵션](../examples.md#option-1-separate-packages)을 설정하고 유지 관리하는 방법을 설명합니다.

## 전제 조건

시작하기 전에 다음을 확인하십시오.

- Git 저장소가 있습니다.
- 작성기 저장소가 있습니다(이 항목에서는 개인 패키지 목록을 강조 표시함).
- `repo.magento.com` 및 `packagist.org` 저장소를 미러링하도록 작성기 저장소를 구성했습니다.

## 기본 Git 프로젝트 저장소

기본 Git 프로젝트 저장소에는 작성기 프로젝트만 포함되어야 합니다. Composer 패키지를 사용하여 그 외의 모든 것을 관리할 수 있습니다. Composer는 종속성을 통해 다른 모든 패키지를 설치하므로 기본 프로젝트에는 다음 파일 구조 이외의 다른 어떤 것도 포함해서는 안 됩니다.

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

`.gitignore` 파일에 다음 내용을 추가하십시오.

```tree
/*
!/composer.json
!/composer.lock
```

## 기본 프로젝트 초기화

1. Git 저장소 `project-<region/country/brand>`을(를) 만듭니다.

1. `composer.json` 및 `composer.lock` 파일 만들기:

   ```bash
   composer create-project --no-install --repository-url=https://repo.magento.com/ magento/project-enterprise-edition project-<region/country/brand>
   cd <install-directory-name>
   printf '/*\n!/composer.json\n!/composer.lock\n!/.gitignore' > .gitignore
   composer config --unset version
   composer config name '<client>/project-<region/country/brand>'
   composer config description '<client> <region/country/brand> main composer project'
   composer config repositories.private-packagist composer https://repo.packagist.com/<client>/
   composer config repositories.packagist.org false
   composer config --unset repositories.0
   composer install
   git init
   git add --all
   git commit -m 'initialize project'
   git remote add origin git@bitbucket.org:<client>/project-<region/country/brand>.git
   git push -u origin master
   ```

## 모듈이 아닌 파일 저장

1. Git 저장소에 `app/etc/config.xml` 파일을 추가합니다.

   만들려는 모듈을 사용하여 `.htaccess`, Google 또는 Bing 인증 텍스트 파일, 실행 파일 또는 Adobe Commerce 모듈에서 관리되지 않는 기타 정적 파일과 같은 다른 지역 또는 브랜드별 파일을 설치할 수 있습니다.

   `composer install` 및 `composer update` 작업 중에 기본 Git 저장소에 파일을 복사하기 위한 파일 매핑을 만들려면 `magento2-component` 형식 패키지를 사용하십시오.

1. 명명 규칙 `component-environment-<region/country/brand>`을(를) 따르는 Git 저장소를 만듭니다.

   ```bash
   bin/magento module:enable --all
   cd ../
   mkdir component-environment-<region/country/brand>
   cd component-environment-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/component-environment-<region/country/brand>' \
    --description='<client> <region/country/brand> environment files' \
    --type=magento2-component \
    --require="magento/magento-composer-installer:*"
   mkdir -p app/etc
   cp ../project-<region/country/brand>/app/etc/config.php app/etc/
   composer config -e
   ```

1. `app/etc/config.php` 파일을 `composer.json` 파일의 `extra.map` 특성에 매핑으로 추가합니다.

   ```json
   {
       "name": "example-client/component-environment-emea",
       "description": "Example client EMEA environment files",
       "type": "magento2-component",
       "require": {
           "magento/magento-composer-installer": "*"
       },
       "extra": {
           "map": [
               [
                   "app/etc/config.php",
                   "app/etc/config.php"
               ]
           ]
       }
   }
   ```

1. `composer.json` 파일의 유효성을 검사하고 Git 저장소에 커밋합니다.

   ```bash
   composer validate
   git init
   git add --all
   git commit -m 'initialize component'
   git remote add origin git@bitbucket.org:<client>/component-environment-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

## 메타패키지 설정

1. 다음 Git 저장소를 생성합니다.

   - `meta-gra`
   - `meta-<region/country/brand>`

1. 다음 종속성 트리를 설정합니다.

   ```tree
   client/project-<region/country/brand>
   └─ requires -> client/meta-<region/country/brand>
                  ├─ requires -> client/component-environment-<region/country/brand>
                  └─ requires -> client/meta-gra
                                 └─ requires -> magento/product-enterprise-edition
   ```

1. GRA 메타패키지를 만듭니다.

   ```bash
   cd ..
   mkdir meta-gra
   cd meta-gra
   composer init --no-interaction \
    --name='<client>/meta-gra' \
    --description='<client> GRA meta package' \
    --type=metapackage \
    --require="magento/product-enterprise-edition:<exact.required.version>"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-gra.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. 브랜드 메타패키지 만들기:

   ```bash
   cd ..
   mkdir meta-<region/country/brand>
   cd meta-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/meta-<region/country/brand>' \
    --description='<client> <region/country/brand> meta package' \
    --type=metapackage \
    --require="<client>/component-environment-<region/country/brand>:~0.1" \
    --require="<client>/meta-gra:~0.1"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. 기본 프로젝트에서 종속성 관리를 통해 컬렉션 필요:

   ```bash
   cd ../project-<region/country/brand>
   rm app/etc/config.php
   composer remove --no-update magento/product-enterprise-edition
   composer require --no-update "<client>/meta-<region/country/brand>:~0.1"
   composer config minimum-stability alpha
   composer config prefer-stable true
   composer update
   git add --all
   git commit -m 'set up GRA dependency tree'
   git push origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. 작성기가 `<client>/component-environment-<region/country/brand>`에서 `app/etc/config.php` 파일을 복사했는지 확인하십시오.

## 코드 배포

웹 서버에서는 Composer를 사용하여 코드를 배포할 수 있지만 기본 프로젝트를 업데이트할 수는 없습니다. 모든 새 배포에서 작성기를 사용하여 프로젝트를 다시 설치하면 프로덕션 및 테스트 서버가 Git에 액세스할 필요가 없어집니다.

## 다른 인스턴스 및 패키지 추가

각 인스턴스(지역, 브랜드 또는 기타 고유한 Adobe Commerce 설치)는 자체 **기본 프로젝트** 인스턴스, **특정 메타패키지** 및 **환경 구성 요소 패키지**&#x200B;를 받아야 합니다. **GRA 메타패키지**&#x200B;는 모든 인스턴스에서 **공유**&#x200B;되어야 합니다.

기능 패키지(예: Adobe Commerce 모듈, 테마, 언어 팩 및 라이브러리)와 서드파티 패키지는 다음 중 하나에 필요합니다.

- **GRA 메타패키지**—_모든_ 인스턴스에 설치
- **인스턴스별 메타패키지**—단일 브랜드 또는 지역에 설치용

>[!IMPORTANT]
>
>`main` 또는 `release` 분기에 있는 기본 프로젝트의 `composer.json` 파일에 패키지가 필요하지 않습니다.

## 개발 준비

개발을 위해 유지 관리하는 모든 모듈의 `develop` 버전을 설치하십시오.

분기 전략에 따라 `develop`, `qa`, `uat` 및 `main` 분기가 있을 수 있습니다. 각 분기가 `dev-` 접두사가 있는 Composer에 있습니다. 따라서 Composer를 통해 `dev-develop` 버전으로 `develop` 분기가 필요할 수 있습니다.

1. 모든 모듈 및 프로젝트 저장소에 `develop` 분기를 만듭니다.

   ```bash
   cd ../component-environment-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../meta-<region/country/brand>
   git checkout master
   git checkout -b develop
   
   git push -u origin develop
   
   
   cd ../meta-gra
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../project-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   composer require \
   "magento-services/meta-fantasy-corp:dev-develop as 0.999" \
   "magento-services/meta-gra:dev-develop as 0.999" \
   "magento-services/component-environment-fantasy-corp:dev-develop as 0.999"
   ```

   이전 단계에서는 `composer.json` 파일에 다음 줄을 생성합니다.

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >이 `composer.json`개 파일 변경 내용을 프로덕션 분기에 **병합하지 마십시오**. `release` 및 `main` 분기에 안정적인 버전의 패키지만 설치하십시오. `qa` 분기 및 다른 주 분기가 아닌 분기에 대해 이러한 종속성을 정의할 수 있습니다.
