---
title: 검색 중지 단어 구성
description: CSV 파일을 사용하여 Adobe Commerce에 대한 중지 단어를 관리하는 방법을 알아봅니다.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 789b7d9dc400b1f669de0067a59e2036c2977a19
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# 검색 중지 단어 구성

일반적으로, _정지어_ 는 텍스트를 처리한 후 검색 엔진이 필터링하는 일반적인 단어입니다. 원래 디스크 공간과 메모리가 매우 제한적이었던 경우에는 1KB를 절약할 때마다 성능이 크게 향상되었습니다. 따라서 검색 엔진은 특정 단어를 무시하고 지수를 작게 유지함으로써 성능 향상을 달성했다.

현재 스토리지가 더 많지만 성능은 여전히 중요합니다. Elasticsearch 및 OpenSearch는 다른 검색 엔진과 마찬가지로 여전히 성능을 향상시키기 위해 중지 단어를 사용합니다.

에 있는 CSV 파일을 사용하여 중지 단어를 관리해야 합니다. `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 디렉토리 또는 `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` directory(Commerce 소프트웨어를 설치한 방식에 따라 다름)

Elasticsearch 및 OpenSearch에서 중지 단어를 사용하는 방법에 대한 자세한 내용은 다음 리소스를 참조하십시오.

- [Stopwords: 성능 대 정밀도](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [정지어의 장단점](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [정지어 사용](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [정지어 및 성능](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## 정지어 구성

정지어는 다음에 위치합니다. `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 디렉토리. Adobe Commerce 및 Magento Open Source은 기본 로케일에 대한 정지어가 포함된 하나의 CSV 파일과 추가 파일, `stopwords.csv`다른 CSV 파일로 표시되지 않는 모든 로케일에 대한 중지 단어가 있습니다.

중지 단어 파일 캐시의 기본 수명은 15분입니다.

### 기존 로케일에 대한 정지어 편집

**정지어를 편집하려면**:

1. Commerce 서버에 로그인하거나 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 텍스트 편집기를 사용하여 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 디렉토리.

   CSV 파일은 명명 규칙을 사용합니다 `stopwords_<locale_code>.csv`. 예를 들어 독일어 stopword 파일의 이름은 입니다 `stopwords_de_DE.csv`.

1. 파일에서 단어를 추가하거나, 단어를 제거하거나, 단어를 변경합니다.

   (파일의 각 중지문은 새 행에서 시작됩니다.)

1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 구성 캐시를 정리합니다.

   - 관리자: **시스템** > 도구 > **캐시 관리**. 다음 항목 선택 **구성** 확인란을 선택하고 그 위에 있는 목록에서 **새로 고침**. 클릭 **제출** 을 클릭하여 작업을 완료합니다.

   - 명령줄: 파일 시스템 소유자로서 다음 명령을 입력합니다.

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. 상점에서 용어를 검색하여 결과를 확인합니다.

### 새 로케일에 대한 정지어 만들기

**로케일에 대한 정지어를 추가하려면**:

1. Commerce 서버에 로그인하거나 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).

1. 텍스트 편집기를 사용하여 라는 중지 단어 파일 만들기 `stopwords_<locale_code>.csv` 다음에서 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 디렉토리.

   예를 들어 이탈리아어 로케일에 대한 정지어를 만들려면 파일 이름을 지정합니다 `stopwords_it_IT.csv`.

1. 중지 단어 파일에서 각 중지 단어가 별도의 줄에 있는지 확인합니다.
1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 동일한 디렉터리에서 을 엽니다. `esconfig.xml` 텍스트 편집기에서.
1. 줄 추가 `esconfig.xml` 다음과 같이:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   예를 들어 이탈리아어 중지 단어 파일을 추가하려면 다음 줄을 추가합니다.

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 변경 내용 저장 `esconfig.xml` 텍스트 편집기를 종료합니다.
1. 구성 캐시를 정리합니다.

   - 관리자: **시스템** > 도구 > **캐시 관리**. 다음 항목 선택 **구성** 확인란을 선택하고 그 위에 있는 목록에서 **새로 고침**. 클릭 **제출** 을 클릭하여 작업을 완료합니다.

   - 명령줄: 파일 시스템 소유자로서 다음 명령을 입력합니다.

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. 상점에서 용어를 검색하여 결과를 확인합니다.

## 중지 디렉터리 변경

이 섹션에서는 다음 중 하나에서 기본 중지 디렉토리를 선택적으로 변경하는 방법에 대해 설명합니다.

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

위치는 Commerce 소프트웨어를 설치한 방식에 따라 다릅니다. Magento 2 GitHub 저장소를 복제한 경우 경로는 아래에 있습니다 `app/code`. 압축된 아카이브 또는 메타패키지를 설치한 경우 경로는 다음과 같습니다 `vendor`.

**디렉토리를 변경하려면**:

1. 파일 시스템 소유자로서 Elasticsearch을 엽니다. `di.xml` 텍스트 편집기에서.

   저장소를 복제한 경우 다음 위치에 있습니다. `app/code/Magento/Elasticsearch/etc/di.xml`

   아카이브 또는 메타패키지가 있는 경우 `vendor/magento/module-elasticsearch/etc/di.xml`

1. 값 변경 `stopwordsDirectory` 원하는 디렉토리로 이동합니다.

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. 변경 내용 저장 `di.xml` 텍스트 편집기를 종료합니다.

## 모듈에서 디렉토리를 변경하려면

1. [모듈 만들기](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. 모듈 내 `etc/di.xml` 지침 추가:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. 모듈에서 디렉토리를 만듭니다 `etc/stopwords`를 추가합니다.

1. 변경 내용 저장 `di.xml` 텍스트 편집기를 종료합니다.
