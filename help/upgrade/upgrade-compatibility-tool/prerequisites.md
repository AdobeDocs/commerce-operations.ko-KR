---
title: '"[!DNL Upgrade Compatibility Tool] 요구 사항'
description: '시스템이 를 실행하는 데 필요한 요구 사항을 충족하는지 확인합니다. [!DNL Upgrade Compatibility Tool] Adobe Commerce 프로젝트에 사용할 수 있습니다. '
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# 시스템 요구 사항

{{commerce-only}}

를 사용하기 위한 최소 요구 사항 [!DNL Upgrade Compatibility Tool] 입니다.

| **요구 사항** | **제한** |
|----------------|-----------------|
| PHP 버전 | >= 7.3 |
| 작성기 | 알려진 요구 사항 없음 |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`, 또는 `>=16.0.0`) |
| 메모리 제한 | 최소 2GB RAM |

를 실행할 수 있습니다 [!DNL Upgrade Compatibility Tool] 일부 운영 체제(Windows는 지원되지 않음)에서 사용할 수 있습니다. 를 실행할 필요가 없습니다 [!DNL Upgrade Compatibility Tool] Adobe Commerce 인스턴스가 있는 위치.

이것은 [!DNL Upgrade Compatibility Tool] Adobe Commerce 인스턴스의 소스 코드에 액세스할 수 있습니다. 예를 들어 한 서버에 설치하고 다른 서버에 Adobe Commerce 설치 시 가리킬 수 있습니다.

를 실행하는 경우 [!DNL Upgrade Compatibility Tool] 큰 모듈 및 파일이 있는 Adobe Commerce 인스턴스에 대해 도구에 높은 양의 RAM(최소 2GB)이 필요할 수 있습니다.

## Adobe Commerce 액세스 키

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

## 작성기

다운로드 [!DNL Upgrade Compatibility Tool] 저장소 및 실행 `composer install` 터미널 을 사용하여 종속성을 설치합니다.

>[!NOTE]
>
> 를 올바르게 구성하지 않으면 **Adobe Commerce 액세스 키**&#x200B;를 다운로드할 수 없습니다 [!DNL Upgrade Compatibility Tool]. 실행 `composer create-project` 명령이 실패합니다.

## Node.js

Node.js를 설치하려면 Node.js를 참조하십시오 [설명서](https://nodejs.dev/learn/how-to-install-nodejs).

## 타사 확장

Adobe은 확장 공급업체에 문의하여 확장이 최신 Adobe Commerce 버전과 완전히 호환되는지 확인할 것을 권장합니다.
