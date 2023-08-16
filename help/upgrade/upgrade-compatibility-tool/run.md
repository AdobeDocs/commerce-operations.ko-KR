---
title: 실행 [!DNL Upgrade Compatibility Tool]
description: 다음 단계에 따라 [!DNL Upgrade Compatibility Tool] Adobe Commerce 프로젝트에 대한 명령줄 인터페이스에서 다음을 수행합니다.
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 0%

---

# 다운로드 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

을(를) 시작하려면 [!DNL Upgrade Compatibility Tool] 명령줄 인터페이스에서 다음 명령을 실행하여 다운로드합니다.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

도구에서 다음을 사용하여 실행 권한을 부여해야 할 수 있습니다. `chmod` 명령:

```bash
chmod +x ./uct/bin/uct
```

## 다음 [!DNL Upgrade Compatibility Tool] 명령줄 인터페이스에서

다음 [!DNL Upgrade Compatibility Tool] 는 설치된 모든 모듈을 분석하여 특정 버전에 대해 Adobe Commerce 사용자 지정 인스턴스를 확인하는 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 중요한 문제, 오류 및 경고 목록을 반환합니다.

이 항목 보기 [비디오 튜토리얼](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) 자세히 알아보기 [!DNL Upgrade Compatibility Tool].

에 사용할 수 있는 명령 [!DNL Upgrade Compatibility Tool] 명령줄 인터페이스에서 다음을 수행합니다.

| **명령** | **설명** |
|----------------|-----------------|
| `upgrade:check` | 이 명령은 [!DNL Upgrade Compatibility Tool] 에 설치된 모든 모듈을 분석합니다. |
| `dbschema:diff` | 이 명령은 지정된 두 Adobe Commerce 버전 간의 데이터베이스 스키마의 모든 차이점을 표시합니다. |
| `core:code:changes` | 이 명령은 현재 Adobe Commerce 설치를 깨끗한 바닐라 설치와 비교합니다. |
| `refactor` | 이 명령은 축소된 문제 세트를 자동으로 수정합니다. |
| `graphql:compare` | 이 명령은 두 GraphQL 종단점을 검사하고 해당 스키마를 비교하는 옵션을 제공합니다. |
| `list` | 이 명령은 모든 [!DNL Upgrade Compatibility Tool] 사용 가능한 명령. |
| `help` | 이 명령은 사용 가능한 모든 항목을 반환합니다. `help`옵션 [!DNL Upgrade Compatibility Tool]. 이 명령은 이전 명령과 함께 옵션뿐만 아니라 실행할 수도 있습니다. |

## 사용 `upgrade:check` 명령

다음 `upgrade:check` 명령은 특정 Adobe Commerce 인스턴스에 대한 핵심 코드 변경 사항과 이에 설치된 모든 사용자 지정 코드 변경 사항을 확인합니다.

다음 `upgrade:check` 명령은 도구를 실행하는 기본 명령입니다.

```bash
bin/uct upgrade:check <dir>
```

위치 `<dir>` 값은 Adobe Commerce 인스턴스가 있는 디렉토리입니다.

에 사용 가능한 옵션 `upgrade:check` 명령:

| **명령** | **사용 가능한 옵션** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: 사용 가능한 모든 옵션을 반환합니다.</li><li>—current-version: 현재 Adobe Commerce 버전. 이 매개 변수는 필수이며 항상 사용해야 합니다.</li><li>—최소 문제 수준: 최소 문제 수준에 따라 문제를 필터링할 수 있습니다(기본값은 WARNING).</li><li>—ignore-current-version-compatibility-issues(또는 -i): 보고서에 현재 버전의 중요한 문제, 오류 및 경고를 포함하지 않으려는 경우.</li><li>—coming-version(또는 -c): 특정 Adobe Commerce 버전을 타깃팅합니다. 생략하면 사용 가능한 최신 버전이 사용됩니다.</li></ul> |

다음 [!DNL Upgrade Compatibility Tool] 을(를) 실행할 수 있도록 허용 `upgrade:check` 이 있는 명령 `--ignore-current-version-compatibility-issues` 옵션을 선택합니다. 현재 버전에서 의 타겟팅된 버전으로 업데이트하면서 새로 도입되는 문제만 가져오려면 이 옵션을 사용하십시오. [!DNL Upgrade Compatibility Tool] 보고서:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> 이는 PHP API 유효성 검사에만 적용됩니다.

### 추가 `--coming-version` 옵션

현재 Adobe Commerce 설치를 모든 Adobe Commerce 버전과 비교할 수 있습니다 `>=2.3` 를 사용하여 `--coming-version` 옵션을 선택합니다.

를 실행할 때 버전을 매개 변수로 제공해야 합니다. `upgrade:check` 명령:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

위치 `-c, --coming-version[=COMING-VERSION]` 는 Adobe Commerce 대상 버전을 나타냅니다.

를 실행할 때 몇 가지 제한 사항이 있습니다. `--coming-version`:

- 이 매개 변수는 Adobe Commerce의 특정 버전을 식별하는 모든 태그를 나타냅니다.
- 이를 명시적으로 제공하는 것이 요건이며, 그 가치만을 제공하는 것은 효과가 없다.
- 따옴표 없이 태그 버전을 제공합니다(작은따옴표나 큰따옴표 모두 제외). ~~&#39;2.4.1-개발&#39;~~.
- 현재 설치된 버전보다 이전 버전을 제공하거나 현재 지원되는 가장 오래된 버전인 2.3보다 이전 버전을 제공해서는 안 됩니다.

## 사용 `dbschema:diff` 명령

두 Adobe Commerce 버전의 데이터베이스 스키마 간의 차이점을 검색할 수 있습니다.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

여기서 인수는 다음과 같습니다.

- `<current-version>`: 비교할 모든 Adobe Commerce 버전.
- `<target-version>`: 또한 비교할 모든 Adobe Commerce 버전입니다.

실행 예:

```bash
bin/uct dbschema:diff 2.4.3 2.4.3-p3

DB schema differences between versions 2.4.3 and 2.4.3-p3:

Table klarna_payments_quote constraint QUOTE_ID_KLARNA_PAYMENTS_QUOTE_QUOTE_ID_QUOTE_ENTITY_ID is present only in version 2.4.3-p3
Table klarna_payments_quote index KLARNA_PAYMENTS_QUOTE_SESSION_ID is present only in version 2.4.3-p3
Table customer_entity column session_cutoff is present only in version 2.4.3-p3
Table customer_visitor column session_id length value is different. 2.4.3: "64", 2.4.3-p3: "1"
Table customer_visitor column session_id comment value is different. 2.4.3: "Session ID", 2.4.3-p3: "Deprecated: Session ID value no longer used"
Table customer_visitor column created_at is present only in version 2.4.3-p3
Table oauth_consumer column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table oauth_token column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table admin_user_session column session_id nullable value is different. 2.4.3: "false", 2.4.3-p3: "true"
Table admin_user_session column session_id length value is different. 2.4.3: "128", 2.4.3-p3: "1"
Table admin_user_session column session_id comment value is different. 2.4.3: "Session ID value", 2.4.3-p3: "Deprecated: Session ID value no longer used"

Total detected differences between version 2.4.3 and 2.4.3-p3: 11
```

## 사용 `core:code:changes` 명령

현재 Adobe Commerce 설치를 비교하여 Adobe Commerce의 핵심 코드가 사용자 지정을 구현하기 위해 수정되었는지 확인할 수 있습니다. 이 명령은 핵심 수정 사항 목록만 표시합니다.

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

여기서 인수는 다음과 같습니다.

- `<dir>`: Adobe Commerce 설치 디렉토리
- `<vanilla dir>`: Adobe Commerce vanilla 설치 디렉토리

에 사용 가능한 옵션 `core:code:changes` 명령:

| **명령** | **사용 가능한 옵션** |
|----------------|-----------------|
| `core:code:changes` | `--help`: 사용 가능한 모든 반환 `--help` 옵션. |

>[!NOTE]
>
> 사용자 지정 코드를 핵심 코드 외부에 보관하는 것이 좋습니다. Adobe Commerce 2.4 참조 [업그레이드 안내서](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) 추가 업그레이드 모범 사례를 확인하십시오.

### 바닐라 설치

A _바닐라_ 설치는 특정 릴리스 버전에 대해 지정된 버전 태그 또는 분기를 깔끔하게 설치하는 것입니다.

다음 `bin/uct core:code:changes` 명령은 시스템에 vanilla 인스턴스가 있는지 확인합니다. 바닐라 설치를 처음 사용하는 경우 대화형 명령줄 질문이 Adobe Commerce 저장소에서 바닐라 프로젝트를 다운로드하라는 메시지를 표시합니다(`https://repo.magento.com/`).

다음을 실행할 수 있습니다. [!DNL Upgrade Compatibility Tool] 명령을 사용하여 `--vanilla-dir` Adobe Commerce vanilla 설치 디렉터리를 지정하는 옵션입니다.

다음을 참조하십시오. [바닐라 인스턴스 배포](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) 항목 을 참조하십시오.

## 사용 `refactor` 명령

다음 [!DNL Upgrade Compatibility Tool] 은(는) 축소된 문제 세트를 자동으로 해결하는 기능을 제공합니다.

- 인수를 전달하지 않고 사용할 수 있도록 허용된 함수지만, 이러한 사용을 사용하면 더 이상 사용되지 않습니다.
- 사용 `$this` Magento 템플릿에서 사용할 수 있습니다.
- PHP 키워드 사용 `final` 개인 메서드에서 사용할 수 있습니다.

이를 위해 다음을 실행합니다. `refactor` 명령:

```bash
bin/uct refactor <dir>
```

위치 `<dir>` 값은 Adobe Commerce 인스턴스가 있는 디렉토리입니다.

에 사용 가능한 옵션 `refactor` 명령:

| **명령** | **사용 가능한 옵션** |
|----------------|-----------------|
| `refactor` | `--help`: 사용 가능한 모든 반환 `--help` 옵션. |

## 사용 `graphql:compare` 명령

이 명령은 옵션을 [!DNL Upgrade Compatibility Tool] 두 GraphQL 종단점을 고려하고 스키마 간에 호환되거나 위험한 변경 사항을 찾는 스키마를 비교하려면 다음을 수행하십시오.

```bash
bin/uct graphql:compare <schema1> <schema2>
```

여기서 인수는 다음과 같습니다.

- `<schema1>`: 기존 설치의 끝점 URL
- `<schema2>`: 바닐라 설치용 끝점 URL

에 사용 가능한 옵션 `graphql:compare` 명령:

| **명령** | **사용 가능한 옵션** |
|----------------|-----------------|
| `graphql:compare` | `--help`: 사용 가능한 모든 반환 `--help` 옵션. |

## 사용 `list` 명령

목록 반환 [!DNL Upgrade Compatibility Tool] 사용 가능한 명령, 실행:

```bash
bin/uct list
```

## 사용 `help` 명령

을(를) 보려면 [!DNL Upgrade Compatibility Tool] 명령 일반 옵션 및 도움말, 실행:

```bash
bin/uct --help
```

사용 가능한 모든 항목이 있는 목록을 반환합니다. `help` 옵션 [!DNL Upgrade Compatibility Tool] 명령줄 인터페이스에서 다음을 수행합니다.

```terminal
- --raw             To output raw command list
- --format=FORMAT   The output format (txt, xml, json, or md) [default: "txt"]
- --short           To skip describing commands' arguments
- -h, --help            Display help for the given command. When no command is given display help for the list command
- -q, --quiet           Do not output any message
- -V, --version         Display this application version
- --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
- -n, --no-interaction  Do not ask any interactive question
- -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

실행 가능 `--help` 특정 명령을 실행할 때의 옵션입니다. 반환 `--help` 지정된 명령에 대한 옵션입니다.

의 예 `upgrade:check` 명령 포함 `--help` 옵션:

```bash
bin/uct upgrade:check --help
```

에 대해 실행할 수 있는 특정 옵션이 반환됩니다. `upgrade:check` 명령:

```terminal
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --min-issue-level[=MIN-ISSUE-LEVEL]            Minimal issue level you want to see in the report (warning, error or critical). [default: "warning"]
- -i, --ignore-current-version-compatibility-issues  Ignore common issues for current and coming version
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

## Adobe Commerce 모범 사례 따르기

- 이름이 같은 모듈이 두 개 있는 것은 피하십시오.
- Adobe Commerce 팔로우 [코딩 표준](https://developer.adobe.com/commerce/php/coding-standards/).
- Adobe Commerce 2.4 [업그레이드 안내서](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) 우수 사례입니다.
- 실행 [!DNL Upgrade Compatibility Tool] 다음에서 [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) 대상 [클라우드 인프라의 Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} 프로젝트.

## 결과 최적화

다음 [!DNL Upgrade Compatibility Tool] 에서는 기본적으로 프로젝트에서 식별된 모든 문제가 포함된 결과가 포함된 보고서를 제공합니다. 업그레이드를 완료하기 위해 수정해야 하는 문제에 집중하도록 결과를 최적화할 수 있습니다.

- 옵션 사용 `--ignore-current-version-compatibility-issues` 현재 버전에서 의 타깃팅된 버전으로 업데이트하면서 도입되는 새로운 문제만 가져오려는 경우 [!DNL Upgrade Compatibility Tool] 보고서.
- 추가 `--min-issue-level` 옵션, 이 설정을 사용하면 최소 문제 수준을 설정하여 업그레이드와 관련하여 가장 중요한 문제만 우선 순위를 지정할 수 있습니다.
- 다음 [!DNL Upgrade Compatibility Tool] 실행하려면 2GB 이상의 RAM이 필요합니다. 이 설정은 낮은 메모리 제한으로 인한 문제를 피하기 위해 권장됩니다. 다음 [!DNL Upgrade Compatibility Tool] 다음을 실행할 경우 질문을 표시합니다. `upgrade:check` 낮은 명령 `memory_limit` 설정.
