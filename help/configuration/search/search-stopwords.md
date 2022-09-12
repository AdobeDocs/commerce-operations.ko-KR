---
title: 검색 중지 구성
description: CSV 파일을 사용하여 Adobe Commerce에 대한 스토어를 관리하는 방법을 알아봅니다.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---


# 검색 중지 구성

일반적으로 _불용_ 검색 엔진이 텍스트를 처리한 후 필터링하는 일반적인 단어입니다. 원래 디스크 공간 및 메모리가 매우 제한적이었던 경우, 저장된 모든 킬로바이트는 성능이 크게 개선되었습니다. 따라서 검색 엔진은 특정 단어를 무시하고 인덱스를 작게 유지함으로써 성능 향상을 달성했습니다.

현재 스토리지 용량이 더 증가했지만 성능은 여전히 중요합니다. 다른 검색 엔진과 마찬가지로 Elasticsearch 및 OpenSearch도 여전히 스토어를 사용하여 성능을 향상시킵니다.

에 있는 CSV 파일을 사용하여 스토어를 관리해야 합니다 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 디렉토리 또는 `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` 디렉토리(Commerce 소프트웨어 설치 방법에 따라)

Elasticsearch 및 OpenSearch에서 단어를 사용하는 방법에 대한 자세한 내용은 다음 리소스를 참조하십시오.

- [중지 단어: 성능과 정밀도 비교](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [스탑워드의 장단점](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [스토워드 사용](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [중지 및 성능](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## stopwords 구성

스토워드는 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 디렉토리. Adobe Commerce 및 Magento Open Source은 기본 로케일에 대한 단어와 추가 파일이 포함된 하나의 CSV 파일과 함께 제공됩니다. `stopwords.csv`: 다른 CSV 파일로 표현되지 않는 모든 로케일에 대한 중지 단어를 포함합니다.

stopwords 파일의 기본 수명 [캐시](https://glossary.magento.com/cache) 은 15분입니다.

### 기존 로케일의 중지 단어 편집

**스토워드를 편집하려면**:

1. Commerce 서버에 로그인하거나 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 텍스트 편집기를 사용하여 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 디렉토리.

   CSV 파일은 이름 지정 규칙을 사용합니다 `stopwords_<locale_code>.csv`. 예를 들어, 독일어 스톱워드 파일의 이름은 다음과 같습니다 `stopwords_de_DE.csv`.

1. 단어를 추가하거나, 단어를 제거하거나, 파일에서 단어를 변경합니다.

   파일의 각 스토프는 새 줄에서 시작됩니다.

1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 구성 캐시를 지웁니다.

   - 관리자: **시스템** > 도구 > **캐시 관리**. 을(를) 선택합니다 **구성** 확인란을 선택하고 위의 목록에서 **새로 고침**. 클릭 **제출** 를 눌러 작업을 완료합니다.

   - 명령줄: 파일 시스템 소유자로서 다음 명령을 입력합니다.

      ```bash
      php <magento_root>/bin/magento cache:clean config
      ```

1. 다음 항목에서 용어를 검색하여 결과를 확인합니다. [상점](https://glossary.magento.com/storefront).

### 새 로케일에 대한 중지 단어 만들기

**로캘에 대한 스토어를 추가하려면**:

1. Commerce 서버에 로그인하거나 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).

1. 텍스트 편집기를 사용하여 이름이 인 스톱 워드 파일을 만듭니다. `stopwords_<locale_code>.csv` 에서 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 디렉토리.

   예를 들어, 이탈리아어 로캘에 대한 스톱워드를 만들려면 파일 이름을 지정합니다 `stopwords_it_IT.csv`.

1. 스톱 워드 파일에서 각 스톱워드가 별도의 줄에 있는지 확인하십시오.
1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 동일한 디렉터리에서 `esconfig.xml` 텍스트 편집기에서 을 참조하십시오.
1. 행 추가 `esconfig.xml` 아래와 같이 변경하는 것을 의미합니다.

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   예를 들어 이탈리아어 스톱워드 파일을 추가하려면 다음 줄을 추가합니다.

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 변경 내용을 `esconfig.xml` 텍스트 편집기를 종료합니다.
1. 구성 캐시를 지웁니다.

   - 관리자: **시스템** > 도구 > **캐시 관리**. 을(를) 선택합니다 **구성** 확인란을 선택하고 위의 목록에서 **새로 고침**. 클릭 **제출** 를 눌러 작업을 완료합니다.

   - 명령줄: 파일 시스템 소유자로서 다음 명령을 입력합니다.

      ```bash
      php <magento_root>/bin/magento magento cache:clean config
      ```

1. 상점에서 용어를 검색하여 결과를 확인합니다.

## 스토워드 디렉토리 변경

이 섹션에서는 다음 중 하나에서 선택적으로 기본 스토프 디렉토리를 변경하는 방법을 설명합니다.

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

위치는 상거래 소프트웨어를 설치하는 방법에 따라 다릅니다. Magento 2 GitHub 리포지토리를 복제한 경우 경로는 아래에 있습니다 `app/code`. 압축 아카이브 또는 메타패키지를 설치한 경우 경로는 아래에 있습니다 `vendor`.

**디렉토리를 변경하려면**:

1. 파일 시스템 소유자로서 Elasticsearch을 엽니다 `di.xml` 텍스트 편집기에서 을 참조하십시오.

   리포지토리를 복제한 경우, 리포지토리는 다음 위치에 있습니다. `app/code/Magento/Elasticsearch/etc/di.xml`

   보관 자료나 형이상지가 있다면, `vendor/magento/module-elasticsearch/etc/di.xml`

1. 값 변경 `stopwordsDirectory` 원하는 디렉토리에

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. 변경 내용을 `di.xml` 텍스트 편집기를 종료합니다.

## 모듈에서 디렉토리를 변경하려면

1. [모듈 만들기](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. 모듈에서 `etc/di.xml` 지침 추가:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. 모듈에서 디렉토리를 만듭니다 `etc/stopwords`를 사용하도록 선택할 수 있습니다.

1. 변경 내용을 `di.xml` 텍스트 편집기를 종료합니다.
