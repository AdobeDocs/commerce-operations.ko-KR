---
title: 검색 중지 단어 구성
description: CSV 파일을 사용하여 Adobe Commerce에 대한 중지 단어를 관리하는 방법을 알아봅니다.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# 검색 중지 단어 구성

일반적으로 _중지 단어_&#x200B;은(는) 검색 엔진이 텍스트를 처리한 후 필터링하는 일반적인 단어입니다. 원래 디스크 공간과 메모리가 매우 제한적이었던 경우에는 1KB를 절약할 때마다 성능이 크게 향상되었습니다. 따라서 검색 엔진은 특정 단어를 무시하고 지수를 작게 유지함으로써 성능 향상을 달성했다.

현재 스토리지가 더 많지만 성능은 여전히 중요합니다. Elasticsearch 및 OpenSearch는 다른 검색 엔진과 마찬가지로 여전히 성능을 향상시키기 위해 중지 단어를 사용합니다.

Commerce 소프트웨어를 설치한 방식에 따라 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 디렉터리 또는 `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` 디렉터리에 있는 CSV 파일을 사용하여 중지 단어를 관리해야 합니다.

Elasticsearch 및 OpenSearch에서 중지 단어를 사용하는 방법에 대한 자세한 내용은 다음 리소스를 참조하십시오.

- [중지 단어: 성능 대 전체 자릿수](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [중지 단어의 장단점](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [중지 단어 사용](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [중지 단어 및 성능](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## 정지어 구성

중지 단어가 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 디렉터리에 있습니다. Adobe Commerce은 기본 로케일에 대한 중지 단어가 포함된 하나의 CSV 파일과 다른 CSV 파일로 표시되지 않는 모든 로케일에 대한 중지 단어가 포함된 추가 파일 `stopwords.csv`과(와) 함께 제공됩니다.

중지 단어 파일 캐시의 기본 수명은 15분입니다.

### 기존 로케일에 대한 정지어 편집

**중지 단어를 편집하려면**:

1. Commerce 서버에 로그인하거나 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 전환합니다.
1. 텍스트 편집기를 사용하여 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 디렉터리에서 중지 파일을 엽니다.

   CSV 파일은 명명 규칙 `stopwords_<locale_code>.csv`을(를) 사용합니다. 예를 들어 독일어 중지 단어 파일의 이름은 `stopwords_de_DE.csv`입니다.

1. 파일에서 단어를 추가하거나, 단어를 제거하거나, 단어를 변경합니다.

   (파일의 각 중지문은 새 행에서 시작됩니다.)

1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 구성 캐시를 정리합니다.

   - 관리자: **시스템** > 도구 > **캐시 관리**. **구성** 확인란을 선택하고 위 목록에서 **새로 고침**&#x200B;을 클릭합니다. 작업을 완료하려면 **제출**&#x200B;을 클릭하세요.

   - 명령줄: 파일 시스템 소유자로서 다음 명령을 입력합니다.

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. 상점에서 용어를 검색하여 결과를 확인합니다.

### 새 로케일에 대한 정지어 만들기

**로케일에 대한 중지 단어를 추가하려면**:

1. Commerce 서버에 로그인하거나 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 전환합니다.

1. 텍스트 편집기를 사용하여 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 디렉터리에 이름이 `stopwords_<locale_code>.csv`인 중지 단어 파일을 만듭니다.

   예를 들어 이탈리아어 로케일에 대한 중지 단어를 만들려면 파일 이름을 `stopwords_it_IT.csv`로 지정합니다.

1. 중지 단어 파일에서 각 중지 단어가 별도의 줄에 있는지 확인합니다.
1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 동일한 디렉터리에서 텍스트 편집기에서 `esconfig.xml`을(를) 엽니다.
1. `esconfig.xml`에 다음과 같이 줄을 추가합니다.

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   예를 들어 이탈리아어 중지 단어 파일을 추가하려면 다음 줄을 추가합니다.

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 변경 내용을 `esconfig.xml`에 저장하고 텍스트 편집기를 종료합니다.
1. 구성 캐시를 정리합니다.

   - 관리자: **시스템** > 도구 > **캐시 관리**. **구성** 확인란을 선택하고 위 목록에서 **새로 고침**&#x200B;을 클릭합니다. 작업을 완료하려면 **제출**&#x200B;을 클릭하세요.

   - 명령줄: 파일 시스템 소유자로서 다음 명령을 입력합니다.

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. 상점에서 용어를 검색하여 결과를 확인합니다.

## 중지 디렉터리 변경

이 섹션에서는 다음 중 하나에서 기본 중지 디렉토리를 선택적으로 변경하는 방법에 대해 설명합니다.

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

위치는 Commerce 소프트웨어를 설치한 방식에 따라 다릅니다. Magento 2 GitHub 리포지토리를 복제한 경우 경로는 `app/code` 아래에 있습니다. 압축 보관 또는 메타패키지를 설치한 경우 경로는 `vendor` 아래에 있습니다.

**디렉터리를 변경하려면**:

1. 파일 시스템 소유자로서 텍스트 편집기에서 Elasticsearch `di.xml`을(를) 엽니다.

   리포지토리를 복제한 경우 `app/code/Magento/Elasticsearch/etc/di.xml`에 있습니다.

   보관 또는 메타패키지가 있는 경우 `vendor/magento/module-elasticsearch/etc/di.xml`에 있습니다.

1. `stopwordsDirectory`의 값을 원하는 디렉터리로 변경합니다.

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. 변경 내용을 `di.xml`에 저장하고 텍스트 편집기를 종료합니다.

## 모듈에서 디렉토리를 변경하려면

1. [모듈 만들기](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. `etc/di.xml` 모듈에서 지침을 추가합니다.

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. 모듈에서 해당 CSV 파일을 사용하여 `etc/stopwords` 디렉터리를 만듭니다.

1. 변경 내용을 `di.xml`에 저장하고 텍스트 편집기를 종료합니다.
