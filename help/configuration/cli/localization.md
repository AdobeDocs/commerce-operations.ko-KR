---
title: 번역 사전 및 언어 패키지
description: 번역 사전을 생성하고 언어 패키지를 빌드하는 방법에 대해 알아봅니다.
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 0%

---

# 로컬라이제이션

{{file-system-owner}}

상거래 번역을 통해 다음을 생성하여 여러 지역 및 시장에 대한 스토어를 사용자 정의하고 현지화할 수 있습니다.

- **번역 사전**, 맞춤화 또는 번역에 편리한 방법 _일부_ 사용자 지정 모듈 또는 테마에 대한 단어와 구.
- **언어 패키지** 번역할 수 있습니다. _모두 또는 일부_ commerce 애플리케이션의 단어 및 구문.

다음을 참조하십시오 [번역 개요].

## 번역 사전 생성

다음을 생성할 수 있습니다. [번역 사전] 기존 문자열을 사용자 지정하려면 사용자 지정 모듈에서 단어와 구를 번역하거나 테마를 현지화하거나 언어 패키지를 만듭니다.

번역을 시작하려면 명령을 사용하여 기존 구 및 단어의 수집된 목록이 있는 사전 CSV 파일을 생성합니다.

사전을 생성하고 번역을 시작하려면 다음을 수행하십시오.

1. 번역 수집 명령을 사용하여 활성화된 구성 요소에서 번역 가능한 단어 및 구를 추출합니다. 콘텐츠가 CSV 파일로 추출됩니다.
1. 기존 단어와 구를 번역합니다. 필요에 따라 사용자 정의 용어를 추가할 수 있습니다.

   번역된 사전을 사용할 수 있는 옵션이 있습니다.

1. 번역 사전을 언어 패키지로 패키징하고 이 패키지를 Commerce 스토어 관리자에게 제공할 수 있습니다.

1. 관리에서 저장소 관리자 [번역 구성].

명령 옵션:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

다음 표에서는 매개 변수와 값에 대해 설명합니다.

| 매개 변수 | 값 | 필수? |
|--- |--- |--- |
| `<path to directory to translate>` | 번역할 수 있는 코드가 있는 디렉터리의 경로입니다. 즉, 번역할 구문이 있는 PHP, PHTML 또는 XML 파일입니다.<br><br>이 도구는 사용자가 입력한 경로에서 검색을 시작하고 포함된 모든 파일과 하위 디렉토리를 검색합니다.<br><br>을 사용하는 경우 이 매개 변수를 사용하지 마십시오. `-m --magento`. | 예(사전), 아니요(패키지). |
| `-m --magento` | 이 번역 사전에서 언어 패키지를 만드는 데 필요합니다. 사용 중인 경우 bin/magento가 포함된 디렉터리를 검색합니다. 이 옵션은 사전의 각 줄에 테마나 모듈을 추가합니다.<br><br>샘플은 다음과 같습니다.<br><br>&quot;항목 없음&quot;,&quot;항목 없음&quot;,module,Magento 위시리스트 | 아니요 |
| `-o --output="<path>"` | 생성할 번역 사전 CSV 파일의 절대 파일 시스템 경로 및 파일 이름을 지정합니다. 입력한 값은 대/소문자를 구분합니다. CSV 파일의 이름은 문자의 대소문자를 포함하여 로케일 이름과 정확히 일치해야 합니다.<br><br>이 매개 변수를 생략하면 출력은 stdout으로 전달됩니다. | 아니요 |

>[!INFO]
>
>번역 사전에서 언어 팩을 만들려면 다음 작업을 수행하십시오 _필수_ 사용 `-m|--magento` 옵션을 선택합니다.

### 번역 지침

단어와 구를 번역할 때 다음 지침을 사용하십시오.

- 두 번째 열의 내용만 변경합니다. 영어 구 번역 (`US`)을 클릭하여 원하는 언어로 표시합니다.
- 로케일에 대한 사전을 만들 때 기본 상거래 문자열을 사용합니다.
- 번역할 때 자리 표시자에 주의하십시오. `%1`, `%2`

Commerce에서는 자리 표시자를 사용하여 컨텍스트 값을 삽입합니다. _아님_ 번역에 사용됩니다. For example:

```text
Product '%1' has been added to shopping cart.
```

값으로 채워집니다.

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

결과 구문에는 각 자리 표시자 중 하나 이상이 포함되어야 합니다. 예를 들어 다음 위치에 자리 표시자가 있다고 가정합니다. `%1` 끝 `%3` 원래 구문에서. 번역에는 이러한 자리 표시자를 순서에 관계없이 여러 개 포함할 수 있지만, 다음 중 하나 이상의 항목이 있어야 합니다. `%1`, `%2`, 및 `%3`. 번역에는 원래 값에 없는 자리 표시자 값이 포함될 수 없습니다(예: `%4`, `%5`등).

구문 번역의 예:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## 언어 패키지 만들기

번역 사전과 달리, 언어 패키지를 사용하여 Commerce 애플리케이션에서 모든 단어 및 구를 번역할 수 있습니다. 번역 사전을 사용하여 특정 구성 요소(예: 모듈 또는 테마)를 번역할 수 있습니다. [언어 패키지에 대해 자세히 알아보기].

이 섹션에서는 모듈 및 테마에 CSV 파일을 작성하는 언어 패키지를 만드는 방법에 대해 설명합니다. 언어 패키지를 생성하려면 다음 섹션에서 설명한 작업을 수행해야 합니다.

1. [단어와 구 수집 및 번역](#generate-a-translation-dictionary). (다음 `--magento` 매개 변수가 필요합니다.)
1. [언어 패키지 명령 실행](#run-the-language-package-command).
1. [디렉터리 및 파일 만들기](#create-directories-and-files).
1. (선택 사항입니다.) [한 언어에 대한 여러 패키지 구성](#configure-multiple-packages-for-a-language).

### 언어 패키지 명령 실행

명령 사용:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

다음 표에서는 언어 패키지 명령의 매개 변수와 값에 대해 설명합니다.

| 매개 변수 | 값 | 필수? |
|--- |--- |--- |
| `<source>` | 언어 패키지로 분류하는 데 필요한 메타 정보와 결합된 번역 사전이 포함된 CSV 파일의 절대 파일 시스템 경로 및 파일 이름입니다.<br><br>사용 [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) csv 파일을 만든 다음 의 설명에 따라 언어 패키지를 만듭니다. [디렉터리 및 파일 만들기](#m2devgde-xlate-files). | 예 |
| `<locale>` | [ISO 639-1] (언어) 및 [ISO 3166] (국가) 모든 결과 CSV 파일의 파일 이름으로 사용되는 언어의 식별자입니다. 예: `de_DE`, `pt_PT`, `pt_BR`. | 예 |
| `-m --mode` | 대상 파일이 있는 경우 기존 언어 패키지를 바꾸거나 새 언어 팩과 병합할지 여부를 지정합니다. 병합은 존재하는 모든 구문을 무시하고 새 구문을 추가합니다.<br><br>값: 병합 또는 바꾸기(기본값). | 아니요 |
| `-d --allow-duplicates` | 언어 팩에서 중복을 허용하려면 이 옵션을 포함합니다. 그렇지 않으면 다른 번역이 있는 여러 항목에서 동일한 구문을 발견하면 명령이 실패하고 오류가 발생합니다. | 아니요 |

### 디렉터리 및 파일 만들기

언어 패키지는 아래 디렉토리에 있습니다. `app/i18n/<VendorName>` Commerce 파일 시스템에서 다음 내용을 참조하십시오.

- 필수 라이선스 파일
- `composer.json`
- `registration.php` that [레지스터] 언어 패키지
- [`language.xml`](#language-package-languagexml) 메타 정보 파일

>[!INFO]
>
>전체 경로는 소문자로 입력해야 합니다. 예를 들어 다음을 참조하십시오. [`de_de`].

이러한 파일을 만들려면 다음 작업을 수행하십시오.

1. 아래에 디렉터리 만들기 `app/i18n`.

   예를 들어 상거래 언어 패키지는 `app/i18n/magento`

1. 필요한 라이선스 파일을 추가합니다.
1. 추가 [`composer.json`] 언어 패키지에 대한 종속성을 지정합니다.
1. 언어 패키지 등록 [`registration.php`]
1. 추가 `language.xml` 메타 정보 파일(다음 절에서 설명).

#### 언어 패키지 language.xml

에서 언어 패키지를 선언할 때 `language.xml` 구성 파일에서 이 패키지의 언어 상속 순서를 지정해야 합니다.

언어 상속을 사용하면 이라는 번역을 만들 수 있습니다. _하위_ 라는 기존 번역을 기반으로 함 _상위_. 하위 번역은 상위 번역을 재정의합니다. 그러나 하위 번역이 업로드 또는 표시에 실패하거나 구문 또는 단어가 누락된 경우 Commerce는 상위 로케일을 사용합니다. [언어 패키지 상속의 예](#example-of-language-inheritance).

패키지를 선언하려면 다음 정보를 지정합니다.

```xml
<?xml version="1.0"?>
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>en_gb</package>
    <sort_order>100</sort_order>
    <use vendor="oxford-university" package="en_us"/>
</language>
```

위치:

- `code`—언어 패키지 로케일(필수)
- `vendor`—모듈의 공급업체 이름(필수)
- `package`—언어 패키지 이름(필수)
- `sort_order`—저장소에 사용할 수 있는 언어 패키지가 여러 개인 경우 패키지 업로드의 우선 순위
- `use`- 사전을 상속할 상위 언어 패키지 로케일

필요한 경우 여러 상위 패키지를 지정할 수 있습니다. 상위 패키지는 처음 나열된 항목에서 처음 사용되는 항목에 적용됩니다.

#### 언어 상속의 예

언어 패키지가 다른 두 패키지에서 상속되고 해당 패키지에 상위 및 &quot;최상위&quot; 패키지도 있다고 가정해 봅시다.

언어 패키지가 두 패키지에서 상속되는 경우 `language.xml` 은 다음과 같이 표시될 수 있습니다.

```xml
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>language_pack</package>
    <sort_order>100</sort_order>
    <use vendor="parent-package-one" package="language_package_one"/>
    <use vendor= "parent-package-two" package="language_package_two"/>
</language>
```

앞의 예에서

- `language_package_one` 상속 위치 `en_au_package` 및 `en_au_package` 상속 위치 `en_ie_package`
- `language_package_two` 상속 위치 `en_ca_package` 및 `en_ca_package` 상속 위치 `en_us_package`

Commerce 응용 프로그램에서 단어 또는 구를 찾을 수 없는 경우 `en_GB` package를 검색하는 경우, 다음 순서로 다른 패키지를 검색합니다.

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

언어 패키지 간 상속을 모두 지정하면 순환 상속 체인이 생성될 수 있습니다. 사용 [Magento\Test\Integrity\App\Language\CircularDependencyTest] 이러한 체인을 찾아 고치기 위해 테스트합니다.

### 한 언어에 대한 여러 패키지 구성

스토어를 보다 유연하게 만들기 위해 스토어에서 동일한 언어에 대한 여러 언어 패키지를 업로드할 수 있습니다. 따라서 시스템에서 언어에 사용할 수 있는 모든 패키지에서 단일 패키지를 컴파일하므로 저장소의 각 부분에 대해 서로 다른 사용자 지정 패키지를 사용할 수 있습니다.

기존 언어에 대해 추가 패키지를 활성화하려면 기존 언어 코드 이름을 제외한 모든 이름을 새 패키지에 지정합니다(혼동을 피하기 위해). 언어 패키지의 패키지 구성 지정 `language.xml` 메타 정보 파일(다음 절에서 설명).

## 번역 명령 사용의 예

다음 섹션에서는 이 항목에서 설명한 명령을 사용하여 번역 사전 및 번역 패키지를 만드는 방법에 대한 전체적인 예제를 제공합니다.

### 예: 모듈 또는 테마의 번역 사전 만들기

다른 판매자에게 배포할 모듈 또는 테마에 독일어 번역을 추가하려면 다음을 수행합니다.

1. 모듈에서 구 수집:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >CSV 파일 이름은 _정확히 일치_ 문자의 대/소문자를 포함하는 로케일입니다.

1. 를 사용하여 단어와 구 번역 [이 지침](#translation-guidelines).
1. 필요한 경우 복사 `xx_YY.csv` 끝 `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` 번역 사전이 모듈용인지 아니면 테마용인지에 따라 모듈의 테마 디렉터리로 이동합니다.

### 예제: 언어 패키지 만들기

앞의 예제와 마찬가지로 CSV 파일을 생성하지만 모듈 또는 테마 디렉토리를 지정하는 대신 전체 Commerce 애플리케이션 루트 디렉토리를 지정합니다. 결과 CSV에는 명령이 코드에서 찾을 수 있는 모든 구문이 포함되어 있습니다.

1. 모듈에서 구 수집:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >CSV 파일 이름은 _정확히 일치_ 문자의 대/소문자를 포함하는 로케일입니다.

1. 를 사용하여 단어와 구 번역 [이 지침](#translation-guidelines).
1. 언어 패키지를 만듭니다.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. 언어 패키지의 디렉토리를 만듭니다.

   For example, `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. 해당 디렉터리에 다음 내용을 모두 추가합니다.

   - 필요한 경우 라이센스
   - `composer.json` (샘플 다음)
   - `registration.php` (샘플 다음)
   - `language.xml` (샘플 다음)

   **샘플`composer.json`**:

   ```json
   {
       "name": "examplecorp/language-xx_yy",
       "description": "Sample language",
       "version": "100.0.2",
       "license": [
           "OSL-3.0",
           "AFL-3.0"
       ],
       "require": {
           "magento/framework": "100.0.*"
       },
       "type": "magento2-language",
       "autoload": {
           "files": [
               "registration.php"
           ]
       }
   }
   ```

   **샘플`registration.php`**:

   ```php
   <?php
   /**
    * Copyright &copy; Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **샘플`language.xml`**:

   ```xml
   <?xml version="1.0"?>
   /**
   * Copyright &copy; Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[번역 개요]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[번역 사전]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[번역 구성]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[언어 패키지에 대해 자세히 알아보기]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[레지스터]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[&#39;de_de&#39;]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&#39;composer.json&#39;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&#39;registration.php&#39;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
