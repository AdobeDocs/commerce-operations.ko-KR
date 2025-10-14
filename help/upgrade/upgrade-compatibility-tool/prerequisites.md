---
title: '[!DNL Upgrade Compatibility Tool] 요구 사항'
description: 시스템이 Adobe Commerce 프로젝트에 대한 명령줄 인터페이스에서  [!DNL Upgrade Compatibility Tool] 을(를) 실행하는 데 필요한 요구 사항을 충족하는지 확인하십시오.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Adobe Commerce 액세스 키

{{commerce-only}}

[을(를) 다운로드하여 사용하려면 &#x200B;](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys)Adobe Commerce 액세스 키[!DNL Upgrade Compatibility Tool]가 있어야 합니다. 기본적으로 `auth.json`에 있는 `~/.composer` 파일에 Adobe Commerce 액세스 키를 추가하십시오.

>[!NOTE]
>
>**COMPOSER_HOME** 환경 변수를 확인하여 `auth.json` 파일의 위치를 확인하십시오.

**공개 키**&#x200B;은(는) _사용자 이름_&#x200B;에 해당하는 반면 **개인 키**&#x200B;은(는) _암호_&#x200B;입니다.

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
> **Adobe Commerce 액세스 키**&#x200B;를 올바르게 구성하지 않으면 [!DNL Upgrade Compatibility Tool]을(를) 다운로드할 수 없으며 `composer create-project` 명령이 실패합니다.

터미널에서 `composer install`을(를) 실행하여 종속성을 설치하십시오.

## 시스템 요구 사항

명령줄 인터페이스에서 [!DNL Upgrade Compatibility Tool]을(를) 사용하기 위한 최소 요구 사항은 다음과 같습니다.

| **요구 사항** | **제약 조건** |
|----------------|-----------------|
| PHP 버전 | >= 7.3 |
| 작성기 | 알려진 요구 사항 없음. |
| Node.js | Node.js 버전 `^12.22.0`, `^14.17.0` 또는 `>=16.0.0`([Node.js 설치](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs) 참조) |
| 메모리 제한 사항 | 최소 2GB RAM. |

[!DNL Upgrade Compatibility Tool]을(를) 실행하려면 [PCNTL](https://www.php.net/manual/en/book.pcntl.php) 및 기타 PHP 확장이 필요합니다. `composer check-platform-reqs` 명령을 사용하여 필요한 PHP 확장을 확인합니다.

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

Adobe Commerce은 Linux 운영 체제에서만 지원됩니다. Linux OS에서 [!DNL Upgrade Compatibility Tool]을(를) 실행할 수 있습니다. Adobe Commerce 인스턴스가 있는 [!DNL Upgrade Compatibility Tool]을(를) 실행하지 않아도 됩니다.

[!DNL Upgrade Compatibility Tool]이(가) Adobe Commerce 인스턴스의 소스 코드에 액세스해야 합니다. 예를 들어 한 서버에 설치하고 다른 서버의 Adobe Commerce 설치를 가리킬 수 있습니다.

큰 모듈과 파일이 있는 Adobe Commerce 인스턴스에 대해 [!DNL Upgrade Compatibility Tool]을(를) 실행하는 경우 도구에는 많은 양의 RAM(최소 2GB)이 필요할 수 있습니다.

[!DNL Upgrade Compatibility Tool][[!DNL Site-Wide Analysis Tool]에서 &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html?lang=ko)클라우드 인프라의 Adobe Commerce[&#x200B; 프로젝트에 대해 &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=ko){target=_blank}을(를) 실행합니다.
