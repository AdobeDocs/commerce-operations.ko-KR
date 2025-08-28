---
source-git-commit: ff21c497db7dd2aab90ded90fb3bba853e3c20f6
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 1%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->
**버전**: 3.0.24

이 참조에는 `bin/uct` 명령줄 도구를 통해 사용할 수 있는 9개의 명령이 포함되어 있습니다.
Adobe Commerce에서 `bin/uct list` 명령을 사용하여 초기 목록이 자동으로 생성됩니다.

## 일반

[개요](/help/upgrade/upgrade-compatibility-tool/overview.md)에서 도구에 대해 자세히 알아보세요.

이 참조 설명서는 애플리케이션 소스 코드에서 생성됩니다. 설명서를 변경하려면 관련 [codebase](https://github.com/magento) 리포지토리에서 해당 명령에 대한 가져오기 요청을 열어야 합니다. 자세한 내용은 [코드 기여](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)를 참조하십시오.

### 글로벌 옵션

#### `--help`, `-h`

해당 명령에 대한 도움말을 표시합니다. 명령을 지정하지 않은 경우 list 명령에 대한 도움말을 표시합니다.

- 기본값: `false`
- 값을 수락하지 않음

#### `--quiet`, `-q`

메시지 출력 안 함

- 기본값: `false`
- 값을 수락하지 않음

#### `--verbose`, `-v|-vv|-vvv`

메시지의 자세한 정도를 증가시킵니다. 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버그의 경우 3

- 기본값: `false`
- 값을 수락하지 않음

#### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 수락하지 않음

#### `--ansi`

ANSI 출력 강제(또는 비활성화 —no-ansi)

- 값을 수락하지 않음

#### `--no-ansi`

&quot;—ansi&quot; 옵션 무시

- 기본값: `false`
- 값을 수락하지 않음

#### `--no-interaction`, `-n`

대화식 질문하지 않음

- 기본값: `false`
- 값을 수락하지 않음


## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

셸 완료 제안을 제공하는 내부 명령

### 옵션

전역 옵션에 대해서는 [전역 옵션](#global-options)을 참조하십시오.

#### `--shell`, `-s`

껍질 유형(&quot;bash&quot;, &quot;fish&quot;, &quot;zsh&quot;)

- 값 필요

#### `--input`, `-i`

입력 토큰의 배열(예: COMP_WORDS 또는 argv)

- 기본값: `[]`
- 값 필요

#### `--current`, `-c`

커서가 있는 &quot;입력&quot; 배열의 인덱스(예: COMP_CWORD)

- 값 필요

#### `--api-version`, `-a`

완료 스크립트의 API 버전

- 값 필요

#### `--symfony`, `-S`

더 이상 사용되지 않음

- 값 필요


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

셸 완료 스크립트 덤프

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion  | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion )"
```

### 인수

#### `shell`

셸 유형(예: &quot;bash&quot;), &quot;$SHELL&quot; 환경 변수 값이 제공되지 않으면 사용됩니다.

### 옵션

전역 옵션에 대해서는 [전역 옵션](#global-options)을 참조하십시오.

#### `--debug`

완료 디버그 로그 추적

- 기본값: `false`
- 값을 수락하지 않음


## `help`

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```

명령에 대한 도움말 표시

```
The help command displays help for a given command:

  uct/bin/uct help list

You can also output the help in other formats by using the --format option:

  uct/bin/uct help --format=xml list

To display the list of available commands, please use the list command.
```

### 인수

#### `command_name`

명령 이름

- 기본값: `help`

### 옵션

전역 옵션에 대해서는 [전역 옵션](#global-options)을 참조하십시오.

#### `--format`

출력 형식(txt, xml, json 또는 md)

- 기본값: `txt`
- 값 필요

#### `--raw`

원시 명령 도움말을 출력하려면

- 기본값: `false`
- 값을 수락하지 않음


## `list`

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

목록 명령

```
The list command lists all commands:

  uct/bin/uct list

You can also display the commands for a specific namespace:

  uct/bin/uct list test

You can also output the information in other formats by using the --format option:

  uct/bin/uct list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  uct/bin/uct list --raw
```

### 인수

#### `namespace`

네임스페이스 이름

### 옵션

전역 옵션에 대해서는 [전역 옵션](#global-options)을 참조하십시오.

#### `--raw`

원시 명령 목록을 출력하려면

- 기본값: `false`
- 값을 수락하지 않음

#### `--format`

출력 형식(txt, xml, json 또는 md)

- 기본값: `txt`
- 값 필요

#### `--short`

명령의 인수 설명을 건너뛰려면

- 기본값: `false`
- 값을 수락하지 않음


## `refactor`

```bash
bin/uct refactor <path>
```

자동으로 해결할 수 있는 문제를 해결합니다. 제공된 경로의 코드가 업데이트됩니다.

### 인수

#### `path`

의 문제를 해결하기 위한 경로입니다.

- 필수

### 옵션

전역 옵션에 대해서는 [전역 옵션](#global-options)을 참조하십시오.


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

업그레이드 호환성 도구는 설치된 모든 Adobe Commerce 이외 모듈을 분석하여 특정 버전에 대해 Adobe Commerce 인스턴스를 확인하는 명령줄 도구입니다. 새 버전의 Adobe Commerce 코드로 업그레이드하기 전에 해결해야 하는 오류 및 경고 목록을 반환합니다.

### 인수

#### `dir`

Adobe Commerce 설치 디렉토리.

- 필수


#### `vanilla-dir`

Adobe Commerce vanilla 설치 디렉토리.

### 옵션

전역 옵션에 대해서는 [전역 옵션](#global-options)을 참조하십시오.

#### `--output`, `-o`

출력을 내보낼 파일의 경로(Json 형식)

- 값을 허용합니다.


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

선택한 두 버전 간의 Adobe Commerce DB 스키마 차이점을 나열할 수 있습니다. 사용 가능한 버전: 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4-p2 | 2.3.5 | 2.3.5-p1 | 2.3.5-p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2.4.4-p4 | 2.4.4-p5 | 2.4.5-p2 | 2.4.5-p3 | 2.4.5-p4 | 2.4.6 | 2.4.6-p1 | 2.4.6-p2 | 2.4.7-베타1 | 2.4.4-p6 | 2.4.5-p5 | 2.4.6-p3 | 2.4.7-베타2 | 2.4.4-p7 | 2.4.5-p6 | 2.4.6-p4 | 2.4.7-베타3 | 2.4.7 | 2.4.6-p5 | 2.4.5-p7 | 2.4.4-p8 | 2.4.4-p9 | 2.4.5-p8 | 2.4.6-p6 | 2.4.7-p1 | 2.4.4-p10 | 2.4.5-p9 | 2.4.6-p7 | 2.4.7-p2 | 2.4.4-p11 | 2.4.5-p10 | 2.4.6-p8 | 2.4.7-p3 | 2.4.8-Beta1 | 2.4.4-p12 | 2.4.5-p11 | 2.4.6-p9 | 2.4.7-p4 | 2.4.8-베타2 | 2.4.4-p13 | 2.4.5-p12 | 2.4.6-p10 | 2.4.7-p5 | 2.4.8 | 2.4.9-alpha2 | 2.4.8-p2 | 2.4.7-p7 | 2.4.6-p12 | 2.4.5-p14 | 2.4.4-p15 | 2.4.9-alpha1 | 2.4.8-p1 | 2.4.7-p6 | 2.4.6-p11 | 2.4.5-p13 | 2.4.4-p14

### 인수

#### `current-version`

현재 버전(예: 2.3.2)

- 필수


#### `target-version`

대상 버전(예: 2.4.5)

- 필수

### 옵션

전역 옵션에 대해서는 [전역 옵션](#global-options)을 참조하십시오.


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

GraphQL 스키마 호환성 확인

### 인수

#### `schema1`

첫 번째 GraphQL 스키마를 가리키는 엔드포인트 URL입니다.

- 필수


#### `schema2`

두 번째 GraphQL 스키마를 가리키는 끝점 URL입니다.

- 필수

### 옵션

전역 옵션에 대해서는 [전역 옵션](#global-options)을 참조하십시오.

#### `--output`, `-o`

출력을 내보낼 파일의 경로(JSON 형식)

- 값을 허용합니다.


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

업그레이드 호환성 도구는 설치된 모든 모듈을 분석하여 특정 버전에 대해 Adobe Commerce 사용자 지정 인스턴스를 확인하는 명령줄 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 오류 및 경고 목록을 반환합니다.

### 인수

#### `dir`

Adobe Commerce 설치 디렉토리.

- 필수

### 옵션

전역 옵션에 대해서는 [전역 옵션](#global-options)을 참조하십시오.

#### `--current-version`, `-a`

생략하면 현재 Adobe Commerce 버전, Adobe Commerce 설치 버전이 사용됩니다.

- 값을 허용합니다.

#### `--coming-version`, `-c`

Target Adobe Commerce 버전. 생략하면 최신 릴리스된 안정적인 버전의 Adobe Commerce이 사용됩니다. 사용 가능한 Adobe Commerce 버전: 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4-p3 \| 2.4.4-p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4-p8 \| 2.4.4-p9 \| 2.4.4-p10 \| 2.4.4-p11 \| 2.4.4-p12 \| 2.4.4-p13 \| 2.4.4-p14 \| 2.4.4-p15 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5-p2 \| 2.4.5-p3 \| 2.4.5-p4 \| 2.4.5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.5-p8 \| 2.4.5-p9 \| 2.4.5-p10 \| 2.4.5-p11 \| 2.4.5-p12 \| 2.4.5-p13 \| 2.4.5-p14 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6-p3 \| 2.4.6-p4 \| 2.4.6-p5 \| 2.4.6-p6 \| 2.4.6-p7 \| 2.4.6-p8 \| 2.4.6-p9 \| 2.4.6-p10 \| 2.4.6-p11 \| 2.4.6-p12 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7 \| 2.4.7-p1 \| 2.4.7-p2 \| 2.4.7-p3 \| 2.4.7-p4 \| 2.4.7-p5 \| 2.4.7-p6 \| 2.4.7-p7 \| 2.4.8-beta1 \| 2.4.8-beta2 \| 2.4.8 \| 2.4.8-p1 \| 2.4.8-p2 \| 2.4.9-alpha1 \| 2.4.9-alpha2

- 값을 허용합니다.

#### `--json-output-path`

출력을 json 형식으로 내보낼 파일의 경로

- 값을 허용합니다.

#### `--html-output-path`

출력을 HTML 형식으로 내보낼 파일의 경로

- 값을 허용합니다.

#### `--min-issue-level`

보고서에 표시하려는 최소 문제 수준(경고, 오류 또는 위험)입니다.

- 기본값: `warning`
- 값을 허용합니다.

#### `--ignore-current-version-compatibility-issues`, `-i`

현재 및 향후 버전에 대한 일반적인 문제 무시

- 기본값: `false`
- 값을 수락하지 않음

#### `--context`

실행 컨텍스트. 이 옵션은 통합을 위한 것이며 실행 결과에 영향을 주지 않습니다.

- 값 필요

