---
title: 설치 [!DNL Upgrade Compatibility Tool]
description: 다음 단계에 따라 을(를) 설치합니다 [!DNL Upgrade Compatibility Tool] Adobe Commerce 프로젝트에 사용할 수 있습니다.
source-git-commit: 218b099caa883f66ddda48407fb789e51fedc203
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# 설치 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

다음 [!DNL Upgrade Compatibility Tool] 은 Adobe Commerce 사용자 지정된 인스턴스에 설치된 모든 모듈을 분석하여 특정 버전과 비교하여 확인하는 명령줄 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 오류 및 경고 목록을 반환합니다.

## 다운로드 [!DNL Upgrade Compatibility Tool]

를 다운로드하려면 [!DNL Upgrade Compatibility Tool]다음 명령을 실행합니다.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## 설치

를 설치하려면 [!DNL Upgrade Compatibility Tool], 필요한 사전 요구 사항을 설치해야 합니다.

* Adobe Commerce 액세스 키
* 작성기
* Node.js

## 전제 조건

자세한 내용은 [전제 조건](../upgrade-compatibility-tool/prerequisites.md) 추가 정보.

### Adobe Commerce 액세스 키

다음을 수행해야 합니다. [Adobe Commerce 액세스 키](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) 를 다운로드하여 사용하려면 [!DNL Upgrade Compatibility Tool]. 에 Adobe Commerce 액세스 키 추가 `auth.json` 파일, 위치 `~/.composer` 기본적으로 제공됩니다.

>[!WARNING]
>
>다음 문서를 확인하십시오. **COMPOSER_HOME** 환경 변수를 사용하여 `auth.json` 파일이 있습니다.

다음 **공개 키** 은 _사용자 이름_ 반면에 **개인 키** 은 _암호_:

### Adobe Commerce 액세스 키의 예

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### 작성기

복제 [!DNL Upgrade Compatibility Tool] 저장소 및 실행 `composer install` 터미널 을 사용하여 종속성을 설치합니다.

>[!WARNING]
>
>만약 **Adobe Commerce 액세스 키** 올바르게 구성되지 않은 경우 [!DNL Upgrade Compatibility Tool] 설치 안 되고 실행 시 오류가 발생합니다 `composer install` 명령.

### Node.js

Node.js를 설치하려면 Node.js를 참조하십시오 [설명서](https://nodejs.dev/learn/how-to-install-nodejs).

## 타사 확장

Adobe은 확장 공급업체에 문의하여 확장이 Adobe Commerce 최신 릴리스 버전과 완전히 호환되는지 확인할 것을 권장합니다.

자세한 내용은 [도구 실행](../upgrade-compatibility-tool/run.md) 를 참조하십시오 [!DNL Upgrade Compatibility Tool].
