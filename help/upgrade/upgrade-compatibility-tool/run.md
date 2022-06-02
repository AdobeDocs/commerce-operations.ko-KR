---
title: '"실행 [!DNL Upgrade Compatibility Tool]"'
description: 다음 단계에 따라 을(를) 실행합니다 [!DNL Upgrade Compatibility Tool] Adobe Commerce 프로젝트에서 확인하십시오.
source-git-commit: ee949c72e42d329fdfb7f4068aeeb3cdc20e1758
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---


# 다운로드 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

를 시작하려면 [!DNL Upgrade Compatibility Tool] 명령줄 인터페이스에서 다음 명령을 실행하여 다운로드합니다.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

>[!NOTE]
>
> 자세한 내용은 [전제 조건](../upgrade-compatibility-tool/prerequisites.md) 페이지를 참조하십시오.

## 를 실행합니다. [!DNL Upgrade Compatibility Tool]

다음 [!DNL Upgrade Compatibility Tool] 은 Adobe Commerce에 설치된 모든 모듈을 분석하여 특정 버전에 대해 사용자 지정 인스턴스를 확인하는 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 중요한 문제, 오류 및 경고 목록을 반환합니다.

다음 [!DNL Upgrade Compatibility Tool] 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 코드에서 해결해야 하는 잠재적인 문제를 식별합니다.

다음 보기 [비디오 튜토리얼](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) 를 참조하십시오 [!DNL Upgrade Compatibility Tool].

## 권장 작업

### 결과 최적화

다음 [!DNL Upgrade Compatibility Tool] 기본적으로 프로젝트에서 식별된 모든 문제와 함께 결과가 포함된 보고서를 제공합니다. 업그레이드를 완료하기 위해 해결해야 하는 문제에 집중할 수 있도록 결과를 최적화할 수 있습니다.

- 옵션을 사용합니다 `--ignore-current-version-compatibility-issues`: 현재 Adobe Commerce 버전에 대해 알려진 모든 중요한 문제, 오류 및 경고를 표시하지 않습니다. 업그레이드하려는 버전에 대한 오류만 제공됩니다.
- 추가 `--min-issue-level` 옵션을 선택하면 이 설정을 통해 최소 문제 수준을 설정하여 업그레이드에 가장 중요한 문제만 우선 순위를 지정할 수 있습니다.
- 특정 공급업체, 모듈 또는 심지어 디렉토리만 분석하려는 경우 경로를 옵션으로 지정할 수도 있습니다. 를 실행합니다. `bin` 옵션이 추가된 명령 `-m`. 이를 통해 [!DNL Upgrade Compatibility Tool] 특정 모듈을 독립적으로 분석하고, [!DNL Upgrade Compatibility Tool].

### Adobe Commerce 우수 사례 따라하기

- 동일한 이름의 모듈이 두 개 있지 않도록 합니다.
- Adobe Commerce 팔로우 [코딩 표준](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).

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

를 사용할 수 있습니다 `graphql:compare` 두 GraphQL 스키마를 비교하여 변경 사항이 있는지 확인하는 명령 자세한 내용은 [GraphQL 스키마 호환성 확인](../upgrade-compatibility-tool/run.md#graphql-schema-compatibility-verification) 섹션을 참조하십시오.

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

여기서 인수는 다음과 같습니다.

- `<dir>`: Adobe Commerce 설치 디렉토리.

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
