---
title: 를 실행합니다. [!DNL Upgrade Compatibility Tool]
description: 다음 단계에 따라 을(를) 실행합니다 [!DNL Upgrade Compatibility Tool] Adobe Commerce 프로젝트에서 확인하십시오.
source-git-commit: fbe47245623469a93cce5cc5a83baf467a007bc4
workflow-type: tm+mt
source-wordcount: '1883'
ht-degree: 0%

---


# 를 실행합니다. [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

다음 [!DNL Upgrade Compatibility Tool] 은 Adobe Commerce 사용자 지정된 인스턴스에 설치된 모든 모듈을 분석하여 특정 버전과 비교하여 확인하는 명령줄 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 중요한 문제, 오류 및 경고 목록을 반환합니다.

다음 [!DNL Upgrade Compatibility Tool] 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 코드에서 해결해야 하는 잠재적인 문제를 식별합니다.

## 를 사용하십시오 `upgrade:check` 명령

다음 `upgrade:check` 명령은 도구를 실행하는 기본 명령입니다.

```bash
bin/uct upgrade:check <dir>
```

>[!TIP]
>
>다음 `<dir>` 값은 Adobe Commerce 인스턴스가 있는 디렉토리입니다.

다음 `upgrade:check` 명령 실행 [!DNL Upgrade Compatibility Tool] 및 은(는) Adobe Commerce에 설치된 모든 모듈을 분석하여 특정 버전에 대해 사용자 지정 인스턴스를 확인합니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 중요한 문제, 오류 및 경고 목록을 반환합니다.

>[!WARNING]
>
>프로젝트 루트(또는 기본) 디렉토리가 제공된 경우에만 실행합니다.

이 명령은 해당 특정 Adobe Commerce 인스턴스에 대한 코어 코드 변경 사항과 이 인스턴스에 설치된 모든 사용자 지정 코드 변경 사항을 확인합니다.

를 실행할 수 있습니다 `core:code:changes` 특정 Adobe Commerce 인스턴스에 대한 코어 코드 변경 사항만 분석하는 명령입니다. 자세한 내용은 [코어 코드 변경 사항](../upgrade-compatibility-tool/run.md#use-the-core:code:changes-command) 섹션을 참조하십시오.

를 사용할 수 있는 동안 `graphql:compare` 두 GraphQL 스키마를 비교하여 변경 사항이 있는지 확인하는 명령 자세한 내용은 [GraphQL 스키마 호환성 확인](../upgrade-compatibility-tool/run.md#graphql-schema-compatibility-verification) 섹션을 참조하십시오.

### Recommendations 를 사용하여 `upgrade:check` 명령

- 다음 [!DNL Upgrade Compatibility Tool] 실행하려면 2GB 이상의 RAM이 필요합니다. 이 설정은 메모리 부족 때문에 문제가 발생하지 않도록 하는 것이 좋습니다. 다음 [!DNL Upgrade Compatibility Tool] 질문을 실행하면 `upgrade:check` 낮은 명령 `memory_limit` 설정
- 을(를) 지정합니다. `-m` 특정 모듈에 대해 도구를 실행하는 옵션:

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

여기서 인수는 다음과 같습니다.

- `<dir>`: Adobe Commerce 설치 디렉토리.
- `[=MODULE-PATH]`: 특정 모듈 경로 디렉터리입니다.

### 를 사용하십시오 `--help` 옵션

를 보려면 [!DNL Upgrade Compatibility Tool] 명령 일반 옵션 및 도움말:

```bash
bin/uct --help
```

그러나 실행할 수 있습니다 `--help` 과 같은 특정 명령을 실행할 때 옵션으로 `bin/uct upgrade:check`. 특정 값 반환 `--help` 해당 명령의 옵션:

```bash
bin/uct upgrade:check --help
```

사용 가능 `--help` 옵션 `upgrade:check` 명령:

- `-m, --module-path[=MODULE-PATH]`: 분석할 모듈의 경로입니다
- `-a, --current-version[=CURRENT-VERSION]`: 현재 Adobe Commerce 버전인 경우 Adobe Commerce 설치 버전이 사용됩니다.
- `-c, --coming-version[=COMING-VERSION]`: Target Adobe Commerce 버전인 경우 최신 릴리스된 Adobe Commerce 버전이 사용됩니다. 사용 가능한 모든 Adobe Commerce 버전 목록을 제공합니다.
- `--json-output-path[=JSON-OUTPUT-PATH]`: 출력을 json 형식으로 내보낼 파일의 경로입니다.
- `--html-output-path[=HTML-OUTPUT-PATH]`: 출력을 HTML 형식으로 내보낼 파일의 경로입니다.
- `--min-issue-level`: 보고서에 표시할 최소 문제 수준. 기본 수준은 입니다. [경고].
- `-i, --ignore-current-version-compatibility-issues`: 알려진 중요한 문제, 오류 및 경고를 사용자 [!DNL Upgrade Compatibility Tool] 보고서 세트에 대해 설명합니다.
- `--context=CONTEXT`: 실행 컨텍스트. 이 옵션은 통합 목적이며 실행 결과에 영향을 주지 않습니다.
- `-h, --help`: 해당 특정 명령에 대한 도움말을 표시합니다. 명령을 제공하지 않으면 `list` 명령은 기본 결과입니다.
- `-q, --quiet`: 명령을 실행하는 동안 메시지를 출력하지 마십시오.
- `-v, --version`: 애플리케이션 버전을 표시합니다.
- `--ansi, --no-ansi`: ANSI 출력을 사용하도록 설정합니다.
- `-n, --no-interaction`: 명령을 실행하는 동안 대화형 질문을 하지 마십시오.
- `-v, --vv, --vvv, --verbose`: 출력 통신의 세부 정보를 증가시킵니다. 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버그 출력의 경우 3입니다.

### 출력

수행된 분석의 결과로, [!DNL Upgrade Compatibility Tool] 심각도, 오류 코드 및 오류 설명을 지정하는 각 파일에 대한 문제 목록이 포함된 보고서를 내보냅니다.

아래 예를 참조하십시오.

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

을(를) 확인합니다. [오류 메시지 참조](error-messages.md) 주제 를 참조하십시오.

이 보고서에는 다음과 같은 세부 요약이 포함되어 있습니다.

- *현재 버전*: 현재 설치된 버전입니다.
- *Target 버전*: 업그레이드할 버전입니다.
- *실행 시간*: 분석을 통해 보고서를 작성하는 데 걸린 시간(mm:ss)입니다.
- *업데이트가 필요한 모듈*: 호환성 문제가 있고 업데이트가 필요한 모듈의 비율입니다.
- *업데이트가 필요한 파일*: 호환성 문제가 있고 업데이트가 필요한 파일의 비율입니다.
- *총 위험 오류*: 발견된 중요한 오류 수입니다.
- *총 오류*: 발견된 오류 수입니다.
- *총 경고 수*: 찾은 경고 수

아래 예를 참조하십시오.

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>기본적으로 [!DNL Upgrade Compatibility Tool] 보고서를 다음 두 가지 형식으로 내보냅니다. `json` 및 `html`.

#### JSON

JSON 파일에는 출력에 표시된 것과 동일한 정보가 포함되어 있습니다.

- 식별된 문제 목록입니다.
- 분석 요약.

발생한 각 문제에 대해 보고서는 문제의 심각도와 설명과 같은 자세한 정보를 제공합니다.

>[!NOTE]
>
>출력 폴더의 기본 경로는 다음과 같습니다. `var/output/[TIME]-results.json`.

이 보고서를 다른 출력 폴더로 내보내려면 다음을 실행하십시오.

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

여기서 인수는 다음과 같습니다.

- `<dir>`: Adobe Commerce 설치 디렉토리.
- `[=JSON-OUTPUT-PATH]`: 내보낼 경로 디렉토리 `.json` 출력 파일입니다.

>[!NOTE]
>
>출력 폴더의 기본 경로는 다음과 같습니다. `var/output/[TIME]-results.json`.

#### HTML

HTML 파일에는 식별된 문제 목록 및 분석 요약이 포함되어 있습니다. 4가지 차트도 포함되어 있습니다.

- **문제 심각도별 모듈**: 모듈별 심각도 분포를 표시합니다.
- **문제 심각도별 파일**: 파일별 심각도 배포를 표시합니다.
- **총 문제 횟수로 정렬된 모듈입니다**: 경고, 오류 및 위험 오류를 고려하여 가장 손상된 10개의 모듈을 표시합니다.
- **관련 크기 및 문제가 있는 모듈**: 모듈에 있는 파일이 많을수록 원이 커집니다. 모듈에 문제가 많을수록 원형이 더 나타납니다.

이러한 차트를 사용하면 가장 손상된 부품과 업그레이드를 수행하는 데 더 많은 작업이 필요한 부품을 한눈에 파악할 수 있습니다.

![HTML 보고서 - 요약](../../assets/upgrade-guide/uct-html-summary.png)

![HTML 보고서 - 세부 정보](../../assets/upgrade-guide/uct-html-details.png)

이 보고서를 다른 출력 폴더로 내보내려면 다음을 수행하십시오.

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

여기서 인수는 다음과 같습니다.

- `<dir>`: {{site.data.var.ee}} 설치 디렉터리입니다.
- `[=HTML-OUTPUT-PATH]`: 내보낼 경로 디렉토리 `.html` 출력 파일입니다.

>[!NOTE]
>
>출력 폴더의 기본 경로는 다음과 같습니다. `var/output/[TIME]-results.html`.

### 를 사용하십시오 `--ignore-current-version-compatibility-issues` 옵션

다음 [!DNL Upgrade Compatibility Tool] 다음을 실행할 수 있습니다. `upgrade:check` 명령을 사용하여 명령 `--ignore-current-version-compatibility-issues` 옵션을 선택하면 새 문제 또는 알 수 없는 중요 문제, 오류 및 경고만 표시됩니다. 알려진 중요한 문제, 오류 및 경고를 사용자 [!DNL Upgrade Compatibility Tool] 보고서 세트에 대해 설명합니다.

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
>이는 PHP API 유효성 검사에만 적용됩니다.

### 바닐라 설치

A _바닐라_ 설치는 특정 릴리스 버전에 대해 지정된 버전 태그 또는 분기를 새로 설치하는 것입니다.

다음 `bin/uct core:code:changes` 시스템에서 vanilla 인스턴스가 있는지 확인합니다. vanilla 설치를 처음 사용하는 경우 대화형 명령줄 질문이 Adobe Commerce 리포지토리에서 vanilla 프로젝트를 다운로드하라는 메시지를 표시합니다(`https://repo.magento.com/`).

를 실행할 수 있습니다 [!DNL Upgrade Compatibility Tool] 명령을 사용하여 `--vanilla-dir` Adobe Commerce vanilla 설치 디렉토리를 지정하는 옵션.

자세한 내용은 [바닐라 인스턴스 배포](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) 주제 를 참조하십시오.

## 를 사용하십시오 `list` 명령

목록 반환 [!DNL Upgrade Compatibility Tool] 사용 가능한 명령, 실행:

```bash
bin/uct list
```

다음 `list` 명령은 다음을 반환합니다.

- `-h, --help`: 해당 특정 명령에 대한 도움말을 표시합니다. 명령을 제공하지 않으면 `list` 명령은 기본 결과입니다.
- `-q, --quiet`: 명령을 실행하는 동안 메시지를 출력하지 마십시오.
- `-v, --version`: 앱 버전을 표시합니다.
- `--ansi, --no-ansi`: ANSI 출력을 사용하도록 설정합니다.
- `-n, --no-interaction`: 명령을 실행하는 동안 대화형 질문을 하지 마십시오.
- `-v, --vv, --vvv, --verbose`: 출력 통신의 세부 정보를 증가시킵니다. 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버그 출력의 경우 3입니다.

## 를 사용하십시오 `core:code:changes` 명령

현재 Adobe Commerce 설치를 깨끗한 vanilla 설치와 비교하여 핵심 코드에 새로운 기능 또는 사용자 지정을 구현하기 위한 수정 사항이 있는지 확인할 수 있습니다. 이 유효성 검사는 이러한 변경 사항을 기반으로 업그레이드에 필요한 노력을 추정하는 데 도움이 됩니다.

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

여기서 인수는 다음과 같습니다.

- `<dir>`: Adobe Commerce 설치 디렉토리.
- `<vanilla dir>`: Adobe Commerce vanilla 설치 디렉토리.

이 명령을 실행할 때 몇 가지 제한 사항이 있습니다.

- 프로젝트 루트(또는 기본) 디렉토리가 제공된 경우에만 실행합니다.
- 코어 수정 사항 목록만 표시합니다.

### 를 사용하십시오 `core:code:changes` 명령을 사용하여 `--help` 옵션

사용 가능 `--help` 옵션 `core:code:changes` 명령:

- `-h, --help`: 해당 특정 명령에 대한 도움말을 표시합니다. 명령을 제공하지 않으면 `list` 명령은 기본 결과입니다.
- `-q, --quiet`: 명령을 실행하는 동안 메시지를 출력하지 마십시오.
- `-v, --version`: 앱 버전을 표시합니다.
- `--ansi, --no-ansi`: ANSI 출력을 사용하도록 설정합니다.
- `-n, --no-interaction`: 명령을 실행하는 동안 대화형 질문을 하지 마십시오.
- `-v, --vv, --vvv, --verbose`: 출력 통신의 세부 정보를 증가시킵니다. 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버그 출력의 경우 3입니다.

## 버전

현재 Adobe Commerce 설치를 Adobe Commerce 버전과 비교할 수 있습니다 `>=2.3`.

명령을 실행할 때 버전을 매개 변수로 제공해야 합니다.

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

>[!NOTE]
>
>이 매개 변수는 사용 가능한 모든 Adobe Commerce 버전 목록을 제공합니다.

위치:

- `-c, --coming-version[=COMING-VERSION]`: Adobe Commerce 타깃팅된 버전입니다.

이전 명령을 실행할 때 몇 가지 제한 사항이 있습니다.

- 이 매개 변수는 특정 버전의 Adobe Commerce을 식별하는 모든 태그를 참조합니다.
- 이를 명시적으로 제공해야 합니다. 의 값만 제공해도 작동하지 않습니다.
- 따옴표가 없는 태그 버전(단일 또는 이중 아님)을 입력합니다. ~~&#39;2.4.1-develop&#39;~~.
- 현재 설치된 버전보다 이전 버전을 제공하거나 현재 지원되는 가장 오래된 버전인 2.3 이전 버전을 제공해서는 안 됩니다.

### 를 사용하십시오 `refactor` 명령

다음 [!DNL Upgrade Compatibility Tool] 에서는 축소된 문제 세트를 자동으로 수정할 수 있습니다.

- 인수를 전달하지 않고 사용할 수 있도록 허용되었지만 이제 이러한 사용이 더 이상 사용되지 않습니다.
- 사용 `$this` Magento 템플릿
- PHP 키워드 사용 `final` 를 반환합니다.

실행:

```bash
bin/uct refactor <dir>
```

## GraphQL 스키마 호환성 확인

다음 [!DNL Upgrade Compatibility Tool] 또한 두 GraphQL 종단점을 검토하고 두 종단점 간의 끊김 및 위험한 변경을 찾는 스키마를 비교할 수 있는 옵션을 제공합니다.

```bash
bin/uct graphql:compare <schema1> <schema2>
```

여기서 인수는 다음과 같습니다.

- `<schema1>`: 기존 설치에 대한 끝점 URL입니다.
- `<schema2>`: vanilla 설치의 끝점 URL입니다.

실행 중이어야 합니다. `instance before` 및 `instance after` 업그레이드.

### GraphQL 비교 명령 `--help` 옵션

사용 가능 `--help` 옵션 `graphql:compare` 명령:

- `-h, --help`: 해당 특정 명령에 대한 도움말을 표시합니다. 명령을 제공하지 않으면 `list` 명령은 기본 결과입니다.
- `-q, --quiet`: 명령을 실행하는 동안 메시지를 출력하지 마십시오.
- `-v, --version`: 앱 버전을 표시합니다.
- `--ansi, --no-ansi`: ANSI 출력을 사용하도록 설정합니다.
- `-n, --no-interaction`: 명령을 실행하는 동안 대화형 질문을 하지 마십시오.
- `-v, --vv, --vvv, --verbose`: 출력 통신의 세부 정보를 증가시킵니다. 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버그 출력의 경우 3입니다.

### GraphQL에 대한 중요한 문제, 오류 및 경고 목록이 있는 예

```terminal
 *   [WARNING] FIELD_CHANGED_KIND: ConfigurableProduct.gender changed type from Int to String.
 *   [WARNING] OPTIONAL_INPUT_FIELD_ADDED: An optional field sku on input type ProductAttributeSortInput was added.
```

자세한 내용은 [개발자 정보](../upgrade-compatibility-tool/developer.md) 추가 정보.

를 실행할 수 있습니다 [!DNL Upgrade Compatibility Tool] PhpStorm 플러그인을 통해 실행 구성을 사용할 수 있습니다. 자세한 내용은 [[!DNL Upgrade Compatibility Tool] 구성 실행](https://devdocs.magento.com/guides/v2.3/ext-best-practices/phpstorm/uct-run-configuration.html) 주제 를 참조하십시오.

## 권장 작업

### 결과 최적화

다음 [!DNL Upgrade Compatibility Tool] 기본적으로 프로젝트에서 식별된 모든 문제와 함께 결과가 포함된 보고서를 제공합니다. 업그레이드를 완료하기 위해 해결해야 하는 문제에 집중할 수 있도록 결과를 최적화할 수 있습니다.

- 옵션을 사용합니다 `--ignore-current-version-compatibility-issues`: 현재 Adobe Commerce 버전에 대해 알려진 모든 중요한 문제, 오류 및 경고를 표시하지 않습니다. 업그레이드하려는 버전에 대한 오류만 제공됩니다.
- 추가 `--min-issue-level` 옵션을 선택하면 이 설정을 통해 최소 문제 수준을 설정하여 업그레이드에 가장 중요한 문제만 우선 순위를 지정할 수 있습니다. 특정 공급업체, 모듈 또는 심지어 디렉토리만 분석하려는 경우 경로를 옵션으로 지정할 수도 있습니다.
- 를 실행합니다. `bin` 옵션이 추가된 명령 `-m`. 이를 통해 [!DNL Upgrade Compatibility Tool] 특정 모듈을 독립적으로 분석하고, [!DNL Upgrade Compatibility Tool].

### Adobe Commerce 우수 사례 따라하기

- 동일한 이름의 모듈이 두 개 있지 않도록 합니다.
- Adobe Commerce 팔로우 [코딩 표준](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).

## 문제 해결

### 세그먼테이션 오류

두 모듈의 이름이 같은 경우 [!DNL Upgrade Compatibility Tool] 세그먼테이션 오류 오류를 표시합니다.

이 오류를 방지하려면 `bin` 옵션이 추가된 명령 `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>다음 `<dir>` 값은 Adobe Commerce 인스턴스가 있는 디렉토리입니다.

다음 `-m` 옵션을 사용하면 [!DNL Upgrade Compatibility Tool] Adobe Commerce 인스턴스에서 동일한 이름의 두 모듈이 발생하지 않도록 각 특정 모듈을 독립적으로 분석합니다.

이 명령 옵션을 사용하면 [!DNL Upgrade Compatibility Tool] 여러 모듈이 포함된 폴더를 분석하려면 다음을 수행하십시오.

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

또한 이 권장 사항은 [!DNL Upgrade Compatibility Tool].

### 빈 출력

>[!NOTE]
>
>다음 `M2_VERSION` 는 Adobe Commerce 인스턴스에 비교할 target Adobe Commerce 버전입니다.

이 명령을 실행한 후

```bash
bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

유일한 출력은 `Upgrade compatibility tool`:

```terminal
bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
Upgrade compatibility tool
```

PHP 메모리 제한이 있을 수 있습니다.
를 설정하여 메모리 제한 무시 `memory_limit` to `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```
