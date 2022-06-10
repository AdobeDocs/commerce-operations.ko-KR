---
title: '"실행 [!DNL Upgrade Compatibility Tool]"'
description: 다음 단계에 따라 을(를) 실행합니다 [!DNL Upgrade Compatibility Tool] ( Adobe Commerce 프로젝트에 대한 명령줄 인터페이스 사용)을 참조하십시오.
source-git-commit: 1dde98ab903f54aee0a094efd86dbf296065e92c
workflow-type: tm+mt
source-wordcount: '1081'
ht-degree: 0%

---


# 다운로드 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

를 시작하려면 [!DNL Upgrade Compatibility Tool] 명령줄 인터페이스에서 다음 명령을 실행하여 다운로드합니다.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## 다음 [!DNL Upgrade Compatibility Tool] 명령줄 인터페이스

다음 [!DNL Upgrade Compatibility Tool] 은 Adobe Commerce에 설치된 모든 모듈을 분석하여 특정 버전에 대해 사용자 지정 인스턴스를 확인하는 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 중요한 문제, 오류 및 경고 목록을 반환합니다.

다음 보기 [비디오 튜토리얼](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) 를 참조하십시오 [!DNL Upgrade Compatibility Tool].

사용 가능한 명령 [!DNL Upgrade Compatibility Tool] 명령줄 인터페이스에서 다음을 수행합니다.

| **명령** | **설명** |
|----------------|-----------------|
| `upgrade:check` | 이 명령은 [!DNL Upgrade Compatibility Tool] 에 설치된 모든 모듈을 분석하여 |
| `core:code:changes` | 이 명령은 현재 Adobe Commerce 설치를 깨끗한 vanilla 설치와 비교합니다. |
| `refactor` | 이 명령은 축소된 문제 집합을 자동으로 수정합니다. |
| `graphql:compare` | 이 명령은 두 GraphQL 끝점을 검색하고 해당 스키마를 비교할 수 있는 옵션을 제공합니다. |
| `list` | 이 명령은 모든 [!DNL Upgrade Compatibility Tool] 사용 가능한 명령. |
| `help` | 이 명령은 사용 가능한 모든 것을 반환합니다 `help`옵션 [!DNL Upgrade Compatibility Tool]. 이 명령은 이전 명령과 함께 실행할 수 있습니다. |

## 를 사용하십시오 `upgrade:check` 명령

다음 `upgrade:check` 명령은 해당 특정 Adobe Commerce 인스턴스에 대한 코어 코드 변경 사항과 이 인스턴스에 설치된 모든 사용자 지정 코드 변경 사항을 확인합니다.

다음 `upgrade:check` 명령은 도구를 실행하는 기본 명령입니다.

```bash
bin/uct upgrade:check <dir>
```

위치 `<dir>` 값은 Adobe Commerce 인스턴스가 있는 디렉토리입니다.

사용 가능한 옵션 `upgrade:check` 명령:

| **명령** | **사용 가능한 옵션** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: 사용 가능한 모든 옵션을 반환합니다.</li><li>—min-issue-level: 최소 문제 수준에 따라 문제를 필터링할 수 있습니다(기본값은 WARNING).</li><li>—ignore-current-version-compatibility-issues(또는 -i): 보고서에서 현재 버전의 심각한 문제, 오류 및 경고를 포함시키지 않으려는 경우.</li><li>—coming-version (또는 -c): 특정 Adobe Commerce 버전 Target.</li></ul> |

다음 [!DNL Upgrade Compatibility Tool] 다음을 실행할 수 있습니다. `upgrade:check` 명령을 사용하여 명령 `--ignore-current-version-compatibility-issues` 선택 사항입니다. 현재 버전에서 사용 중인 의 타깃팅된 버전으로 업데이트하여 도입된 새로운 문제를 가져오려는 경우에만 이 옵션을 사용합니다 [!DNL Upgrade Compatibility Tool] 보고서:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> 이는 PHP API 유효성 검사에만 적용됩니다.

### 추가 `--coming-version` 옵션

현재 Adobe Commerce 설치를 모든 Adobe Commerce 버전과 비교할 수 있습니다 `>=2.3` 사용 `--coming-version` 선택 사항입니다.

를 실행할 때 버전을 매개 변수로 제공해야 합니다 `upgrade:check` 명령:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

위치 `-c, --coming-version[=COMING-VERSION]` 는 Adobe Commerce 타깃팅된 버전을 참조합니다.

를 실행할 때에는 몇 가지 제한 사항이 있습니다 `--coming-version`:

- 이 매개 변수는 특정 버전의 Adobe Commerce을 식별하는 모든 태그를 참조합니다.
- 이를 명시적으로 제공해야 합니다. 의 값만 제공해도 작동하지 않습니다.
- 따옴표가 없는 태그 버전(단일 또는 이중 아님)을 입력합니다. ~~&#39;2.4.1-develop&#39;~~.
- 현재 설치된 버전보다 이전 버전을 제공하거나 현재 지원되는 가장 오래된 버전인 2.3 이전 버전을 제공해서는 안 됩니다.

## 를 사용하십시오 `core:code:changes` 명령

현재 Adobe Commerce 설치를 비교하여 사용자 지정을 구현하기 위해 Adobe Commerce의 핵심 코드가 수정되었는지 확인할 수 있습니다. 이 명령은 코어 수정 사항 목록만 표시합니다.

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

여기서 인수는 다음과 같습니다.

- `<dir>`: Adobe Commerce 설치 디렉토리.
- `<vanilla dir>`: Adobe Commerce vanilla 설치 디렉토리.

사용 가능한 옵션 `core:code:changes` 명령:

| **명령** | **사용 가능한 옵션** |
|----------------|-----------------|
| `core:code:changes` | `--help`: 사용 가능한 모든 반환 `--help` 옵션. |

>[!NOTE]
>
> 사용자 지정 코드를 코어 코드에서 제거하는 것이 좋습니다. Adobe Commerce 2.4 참조 [업그레이드 안내서](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) 를 참조하십시오.

### 바닐라 설치

A _바닐라_ 설치는 특정 릴리스 버전에 대해 지정된 버전 태그 또는 분기를 새로 설치하는 것입니다.

다음 `bin/uct core:code:changes` 시스템에서 vanilla 인스턴스가 있는지 확인합니다. vanilla 설치를 처음 사용하는 경우 대화형 명령줄 질문이 Adobe Commerce 리포지토리에서 vanilla 프로젝트를 다운로드하라는 메시지를 표시합니다(`https://repo.magento.com/`).

를 실행할 수 있습니다 [!DNL Upgrade Compatibility Tool] 명령을 사용하여 `--vanilla-dir` Adobe Commerce vanilla 설치 디렉토리를 지정하는 옵션.

자세한 내용은 [바닐라 인스턴스 배포](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) 주제 를 참조하십시오.

## 를 사용하십시오 `refactor` 명령

다음 [!DNL Upgrade Compatibility Tool] 에서는 축소된 문제 세트를 자동으로 수정할 수 있습니다.

- 인수를 전달하지 않고 사용할 수 있도록 허용되었지만 이제 이러한 사용이 더 이상 사용되지 않습니다.
- 사용 `$this` Magento 템플릿
- PHP 키워드 사용 `final` 를 반환합니다.

이를 위해 를 실행합니다. `refactor` 명령:

```bash
bin/uct refactor <dir>
```

위치 `<dir>` 값은 Adobe Commerce 인스턴스가 있는 디렉토리입니다.

사용 가능한 옵션 `refactor` 명령:

| **명령** | **사용 가능한 옵션** |
|----------------|-----------------|
| `refactor` | `--help`: 사용 가능한 모든 반환 `--help` 옵션. |

## 를 사용하십시오 `graphql:compare` 명령

이 명령은 [!DNL Upgrade Compatibility Tool] 두 개의 GraphQL 끝점을 도입하고 스키마 간에 끊김 및 위험 변경 사항을 찾는 스키마를 비교하려면 다음을 수행합니다.

```bash
bin/uct graphql:compare <schema1> <schema2>
```

여기서 인수는 다음과 같습니다.

- `<schema1>`: 기존 설치에 대한 끝점 URL입니다.
- `<schema2>`: vanilla 설치의 끝점 URL입니다.

사용 가능한 옵션 `graphql:compare` 명령:

| **명령** | **사용 가능한 옵션** |
|----------------|-----------------|
| `graphql:compare` | `--help`: 사용 가능한 모든 반환 `--help` 옵션. |

## 를 사용하십시오 `list` 명령

목록 반환 [!DNL Upgrade Compatibility Tool] 사용 가능한 명령, 실행:

```bash
bin/uct list
```

## 를 사용하십시오 `--help` 명령

를 보려면 [!DNL Upgrade Compatibility Tool] 명령 일반 옵션 및 도움말:

```bash
bin/uct --help
```

사용 가능한 모든 목록이 반환됩니다 `help` 옵션 [!DNL Upgrade Compatibility Tool] 명령줄 인터페이스에서 다음을 수행합니다.

```terminal
- -m, --module-path[=MODULE-PATH]: Path of the modules to be analysed
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

그러나 실행할 수 있습니다 `--help` 특정 명령을 실행할 때 옵션으로 사용할 수 있습니다. 이렇게 하면 특정 항목이 반환됩니다 `--help` 특정 명령에 대한 옵션

의 예 `upgrade:check` 명령 `--help` 옵션:

```bash
bin/uct upgrade:check --help
```

에 대해 실행할 수 있는 특정 옵션을 반환합니다 `upgrade:check` 명령:

```terminal
--min-issue-level.
-i, --ignore-current-version-compatibility-issues.
```

## Adobe Commerce 우수 사례 따라하기

- 동일한 이름의 모듈이 두 개 있지 않도록 합니다.
- Adobe Commerce 팔로우 [코딩 표준](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).
- Adobe Commerce 2.4 [업그레이드 안내서](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) 모범 사례에 따라 태깅합니다.

## 결과 최적화

다음 [!DNL Upgrade Compatibility Tool] 기본적으로 프로젝트에서 식별된 모든 문제와 함께 결과가 포함된 보고서를 제공합니다. 업그레이드를 완료하기 위해 해결해야 하는 문제에 집중할 수 있도록 결과를 최적화할 수 있습니다.

- 옵션을 사용합니다 `--ignore-current-version-compatibility-issues` 를 사용 중인 현재 버전에서 사용 중인 대상 버전으로 업데이트하여 도입된 새로운 문제를 가져오려는 경우에만 [!DNL Upgrade Compatibility Tool] 보고서 세트에 대해 설명합니다.
- 추가 `--min-issue-level` 옵션을 선택하면 이 설정을 통해 최소 문제 수준을 설정하여 업그레이드에 가장 중요한 문제만 우선 순위를 지정할 수 있습니다.
- 다음 [!DNL Upgrade Compatibility Tool] 실행하려면 2GB 이상의 RAM이 필요합니다. 이 설정은 메모리 부족 때문에 문제가 발생하지 않도록 하는 것이 좋습니다. 다음 [!DNL Upgrade Compatibility Tool] 질문을 실행하면 `upgrade:check` 낮은 명령 `memory_limit` 설정
- 특정 공급업체, 모듈 또는 심지어 디렉토리만 분석하려는 경우 경로를 옵션으로 지정할 수도 있습니다. 를 실행합니다. `bin` 옵션이 추가된 명령 `-m`. 이를 통해 [!DNL Upgrade Compatibility Tool] 특정 모듈을 독립적으로 분석하고, [!DNL Upgrade Compatibility Tool]. 을(를) 지정합니다. `-m` 특정 모듈에 대해 도구를 실행하는 옵션:

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

여기서 인수는 다음과 같습니다.

- `<dir>`: Adobe Commerce 설치 디렉토리.
- `[=MODULE-PATH]`: 특정 모듈 경로 디렉터리입니다.
