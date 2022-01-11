---
title: 업그레이드 호환성 도구 설치
description: 다음 단계에 따라 Adobe Commerce 프로젝트용 업그레이드 호환성 도구를 설치합니다.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---


# 업그레이드 호환성 도구 설치

업그레이드 호환성 도구는 설치된 모든 모듈을 분석하여 Adobe Commerce 사용자 지정 인스턴스를 특정 버전과 비교하여 확인하는 명령줄 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 오류 및 경고 목록을 반환합니다.

## 워크플로우

다음 다이어그램은 업그레이드 호환성 도구를 실행할 때 예상되는 워크플로우를 보여줍니다.

![업그레이드 호환성 도구 다이어그램](../../assets/upgrade-guide/mvp-diagram-v3.png)

## 업그레이드 호환성 도구는 누구입니까?

다음 사용 사례에서는 Adobe Commerce 파트너가 클라이언트의 인스턴스를 업그레이드하는 일반적인 프로세스에 대해 설명합니다.

1. 파트너의 소프트웨어 엔지니어는 [Adobe Commerce 저장소](https://repo.magento.com/) 최신 Adobe Commerce 릴리스의 베타 단계 동안 및에서 실행합니다. See the [Download the Upgrade Compatibility Tool](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) topic for more information.
1. The Software Engineer generates a vanilla instance for the specific version of Adobe Commerce that is currently installed. See the [Contributor guide](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) for more information on using the `instance` command to generate a vanilla installation.
1. 소프트웨어 엔지니어는 재고 및 카탈로그 모듈에서 여러 사용자 지정 영역이 손상되어 복잡도 점수가 X인 것을 확인합니다. [개발자](../upgrade-compatibility-tool/developer.md) 복잡성 점수에 대한 자세한 내용은 안내서를 참조하십시오.
1. 이 정보를 통해 소프트웨어 엔지니어는 업그레이드의 복잡성을 이해하고 이 정보를 파트너의 계정 관리자에게 다시 전달할 수 있습니다.
1. 계정 관리자는 Adobe Commerce 업그레이드에 대한 타임라인 및 비용을 만들며, 이를 통해 관리자의 승인을 받을 수 있습니다.
1. 관리자의 승인을 받아 소프트웨어 엔지니어는 손상된 모듈을 해결하기 위해 필요한 코드 수정 작업을 수행합니다.
1. 소프트웨어 엔지니어는 Adobe Commerce 시험판과 함께 업그레이드 호환성 도구를 한 번 더 실행하여 새로운 문제가 없고 해당 코드가 베타 단계 동안 발견된 문제를 해결하도록 합니다.
1. 모든 것이 확인되고 소프트웨어 엔지니어가 코드를 스테이징 환경으로 푸시합니다. 여기서 회귀 테스트는 모든 테스트가 녹색으로 확인되므로 Adobe Commerce 사전 릴리스가 있는 당일 최신 Adobe Commerce 버전을 프로덕션에 릴리스할 수 있습니다.

   ![업그레이드 호환성 도구 대상](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>vanilla 인스턴스는 특정 릴리스 버전에 대해 지정된 버전 태그 또는 분기를 깔끔하게 설치하는 것입니다.

## 전제 조건

자세한 내용은 [전제 조건](../upgrade-compatibility-tool/prerequisites.md) 추가 정보.

>[!NOTE]
>
>모든 운영 체제에서 업그레이드 호환성 도구를 실행할 수 있습니다. Adobe Commerce 인스턴스가 있는 업그레이드 호환성 도구를 실행할 필요가 없습니다. Adobe Commerce 인스턴스의 소스 코드에 액세스하려면 업그레이드 호환성 도구가 필요합니다. 예를 들어, 한 서버에 도구를 설치하고 다른 서버에 Adobe Commerce 설치를 가리키면 됩니다.

큰 모듈 및 파일이 있는 Adobe Commerce 인스턴스에 대해 업그레이드 호환성 도구를 실행 중인 경우 도구에서 대용량 RAM, 최소 2GB RAM이 필요할 수 있습니다.

### 권장 작업

Adobe Commerce 우수 사례에 따라 이름이 같은 두 개의 모듈이 없도록 권장합니다. 이 경우 업그레이드 호환성 도구에서 세그멘테이션 오류 오류가 표시됩니다.

이 오류를 방지하려면 `bin` 옵션이 추가된 명령 `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>다음 `<dir>` 값은 Adobe Commerce 인스턴스가 있는 디렉토리입니다.

다음 `-m` 옵션을 사용하면 업그레이드 호환성 도구에서 Adobe Commerce 인스턴스에서 동일한 이름의 두 모듈이 발생하지 않도록 각 특정 모듈을 독립적으로 분석할 수 있습니다.

This command option also allows the Upgrade Compatibility Tool to analyze a folder containing several modules:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

This recommendation also helps with memory issues that can occur when executing the Upgrade Compatibility Tool.

## Download the Upgrade Compatibility Tool

To download the Upgrade Compatibility Tool, run the following command:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## 설치

업그레이드 호환성 도구를 설치하려면 필요한 사전 요구 사항을 설치해야 합니다.

* Adobe Commerce access keys
* 작성기
* Node.js

### Adobe Commerce 액세스 키

다음을 수행해야 합니다. [Adobe Commerce 액세스 키](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) 를 다운로드하여 사용하려면 업그레이드 호환성 도구를 사용하십시오. 에 Adobe Commerce 액세스 키 추가 `auth.json` 파일, 위치 `~/.composer` 기본적으로 제공됩니다.

>[!WARNING]
>
>다음 문서를 확인하십시오. **COMPOSER_HOME** 환경 변수를 사용하여 `auth.json` 파일이 있습니다.

다음 **공개 키** 은 _사용자 이름_ 반면에 **개인 키** 은 _암호_:

### Example of Adobe Commerce access keys

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### 작성기

업그레이드 호환성 도구 리포지토리 복제 및 실행 `composer install` 터미널 을 사용하여 종속성을 설치합니다.

>[!WARNING]
>
>If the **Adobe Commerce access keys** are not correctly configured, the Upgrade Compatibility Tool will not install and you will get errors when running the `composer install` command.

### Node.js

Node.js를 설치하려면 Node.js를 참조하십시오 [설명서](https://nodejs.dev/learn/how-to-install-nodejs).

## Third-party extensions

Adobe recommends that you contact your extension vendor to determine whether your extension is fully compatible with Adobe Commerce 2.4.x.

자세한 내용은 [도구 실행](../upgrade-compatibility-tool/run.md) 업그레이드 호환성 도구 실행에 대한 자세한 정보.
