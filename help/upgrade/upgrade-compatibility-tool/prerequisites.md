---
title: '"[!DNL Upgrade Compatibility Tool] 요구 사항'
description: 시스템이 를 실행하는 데 필요한 요구 사항을 충족하는지 확인합니다. [!DNL Upgrade Compatibility Tool] ( Adobe Commerce 프로젝트에 대한 명령줄 인터페이스 사용)을 참조하십시오.
source-git-commit: 653d755023f96c0a6acc312f74fd4a0292f13a73
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Adobe Commerce 액세스 키

{{commerce-only}}

다음을 수행해야 합니다. [Adobe Commerce 액세스 키](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) 를 다운로드하여 사용하려면 [!DNL Upgrade Compatibility Tool]. 에 Adobe Commerce 액세스 키 추가 `auth.json` 파일, 위치 `~/.composer` 기본적으로 제공됩니다.

>[!NOTE]
>
>다음 문서를 확인하십시오. **COMPOSER_HOME** 환경 변수를 사용하여 `auth.json` 파일이 있습니다.

다음 **공개 키** 은 _사용자 이름_ 반면에 **개인 키** 은 _암호_:

## Adobe Commerce 액세스 키의 예

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

>[!NOTE]
>
> 를 올바르게 구성하지 않으면 **Adobe Commerce 액세스 키**&#x200B;를 다운로드할 수 없습니다 [!DNL Upgrade Compatibility Tool] 그리고 `composer create-project` 명령이 실패합니다.

실행 `composer install` 터미널 을 사용하여 종속성을 설치합니다.

## 시스템 요구 사항

를 사용하기 위한 최소 요구 사항 [!DNL Upgrade Compatibility Tool] 명령줄 인터페이스에서 는 다음과 같습니다.

| **요구 사항** | **제한** |
|----------------|-----------------|
| PHP 버전 | >= 7.3 |
| 작성기 | 알려진 요구 사항이 없습니다. |
| Node.js | Node.js 버전 `^12.22.0`, `^14.17.0`, 또는 `>=16.0.0` 자세한 내용은 [Node.js 설치](https://nodejs.dev/en/learn/how-to-install-nodejs/)) |
| 메모리 제한 | 최소 2GB RAM |

[!DNL Upgrade Compatibility Tool] 필요 [PCNTL](https://www.php.net/manual/en/book.pcntl.php) 및 기타 PHP 확장 기능을 실행할 수 있습니다. 를 사용하여 필요한 PHP 확장 확인 `composer check-platform-reqs` 명령:

```bash
# Example output of `composer check-platform-reqs` command for UCT 2.2.6 and PHP 7.4:

$ composer check-platform-reqs
Checking platform requirements for packages in the vendor dir
ext-ctype     *         success provided by symfony/polyfill-ctype
ext-dom       20031129  success
ext-filter    7.4.30    success
ext-json      7.4.30    success
ext-libxml    7.4.30    success
ext-mbstring  *         success provided by symfony/polyfill-mbstring
ext-openssl   7.4.30    success
ext-pcntl     7.4.30    success
ext-pcre      7.4.30    success
ext-phar      7.4.30    success
ext-simplexml 7.4.30    success
ext-tokenizer 7.4.30    success
ext-xml       7.4.30    success
ext-xmlwriter 7.4.30    success
ext-zip       1.15.6    success
php           7.4.30    success
```

Adobe Commerce은 Linux 운영 체제에서만 지원됩니다. 를 실행할 수 있습니다 [!DNL Upgrade Compatibility Tool] ( Linux OS) 를 실행할 필요가 없습니다 [!DNL Upgrade Compatibility Tool] Adobe Commerce 인스턴스가 있는 위치.

이것은 [!DNL Upgrade Compatibility Tool] Adobe Commerce 인스턴스의 소스 코드에 액세스할 수 있습니다. 예를 들어 한 서버에 설치하고 다른 서버에 Adobe Commerce 설치 시 가리킬 수 있습니다.

를 실행하는 경우 [!DNL Upgrade Compatibility Tool] 큰 모듈 및 파일이 있는 Adobe Commerce 인스턴스에 대해 도구에 높은 양의 RAM(최소 2GB)이 필요할 수 있습니다.

를 실행합니다. [!DNL Upgrade Compatibility Tool] 에서 [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) 대상 [Adobe Commerce on cloud 인프라](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} 프로젝트를 참조하십시오.
