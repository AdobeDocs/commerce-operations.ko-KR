---
source-git-commit: ebd32f3fac571efa729122d0e84471b6de540630
workflow-type: tm+mt
source-wordcount: '19002'
ht-degree: 0%

---
# magento-cloud(클라우드 기반의 Adobe Commerce)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**버전**: 1.38.1 <!-- app.version -->

이 참조에는 `magento-cloud` 명령줄 도구.
초기 목록은 `magento-cloud list` 명령입니다.

>[!NOTE]
>
>이 참조는 애플리케이션 코드 베이스에서 생성됩니다. 컨텐츠를 변경하려면 [codebase](https://github.com/magento) 리포지토리를 사용하여 검토를 위해 변경 사항을 제출합니다. 다른 방법은 다음과 같습니다 _피드백 제공_ (오른쪽 상단에 있는 링크를 찾습니다.) 기여 지침은 [코드 기여](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

BASH 완료 후크.

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--generate-hook`, `-g`



이 응용 프로그램에 대한 완료를 설정하는 BASH 코드를 생성합니다.
- 기본값: `false`
- 값을 허용하지 않음



### `--program`, `-p`



완료를 트리거해야 하는 프로그램 이름 &lt;comment>(기본값은 절대 응용 프로그램 경로)&lt;/comment>.
- 값 필요



### `--multiple`, `-m`



생성된 후크는 여러 응용 프로그램에 사용할 수 있습니다.
- 기본값: `false`
- 값을 허용하지 않음


### `--shell-type`

셸 유형(zsh 또는 bash)을 설정합니다. 그렇지 않으면 자동으로 결정됩니다.
- 값을 허용합니다 <!-- options --> <!-- options.size -->

## `bot`

Magento 클라우드 보트

```bash
magento-cloud bot [--party] [--parrot]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--party`


- 기본값: `false`
- 값을 허용하지 않음


### `--parrot`


- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `clear-cache`

CLI 캐시 지우기

```bash
magento-cloud clear-cache
```

<!-- app.name -->

```bash
clearcache
```

<!-- app.name -->

```bash
cc
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `decode`

MAGENTO_CLOUD_VARIABLES 등의 인코딩된 문자열을 디코딩합니다

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```

<!-- app.name --> <!-- command.usage -->

### `value`

디코딩할 변수 값
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



변수 내에서 볼 속성입니다
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `docs`

온라인 설명서를 엽니다.

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```

<!-- app.name --> <!-- command.usage -->

### `search`

검색어

- 기본값: `[]`

- 어레이 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--browser`

URL을 여는 데 사용할 브라우저입니다. 없음에 대해 0을 설정합니다.
- 값 필요


### `--pipe`

stdout에 URL을 출력합니다.
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `help`

명령에 대한 도움말을 표시합니다.

```bash
help [--format FORMAT] [--raw] [--] [<command_name>]
```

<!-- app.name --> <!-- command.usage -->

### `command_name`

명령 이름
- 기본값: `help`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--format`

출력 형식(txt, xml, json 또는 md)
- 기본값: `txt`
- 값 필요


### `--raw`

원시 명령 도움말을 출력하려면
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `legacy-migrate`

기존 파일 구조에서 마이그레이션

```bash
magento-cloud legacy-migrate [--no-backup]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-backup`

프로젝트의 백업을 만들지 마십시오.
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `list`

명령 나열

```bash
list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```

<!-- app.name --> <!-- command.usage -->

### `namespace`

네임스페이스 이름
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

원시 명령 목록을 출력하려면
- 기본값: `false`
- 값을 허용하지 않음


### `--format`

출력 형식(txt, xml, json 또는 md)
- 기본값: `txt`
- 값 필요 <!-- options --> <!-- options.size -->

## `multi`

여러 프로젝트에서 명령 실행

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd>
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

실행할 명령
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--projects`, `-p`



프로젝트 ID 목록(쉼표로 및/또는 공백으로 구분)
- 값 필요


### `--continue`

예외가 발생하더라도 명령을 계속 실행합니다
- 기본값: `false`
- 값을 허용하지 않음


### `--sort`

프로젝트 옵션 목록을 정렬할 속성입니다
- 기본값: `title`
- 값 필요


### `--reverse`

프로젝트 옵션 순서 취소
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `web`

웹 UI 열기

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--browser`

URL을 여는 데 사용할 브라우저입니다. 없음에 대해 0을 설정합니다.
- 값 필요


### `--pipe`

stdout에 URL을 출력합니다.
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `welcome`

Magento Cloud 시작

```bash
magento-cloud welcome
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `winky`



```bash
magento-cloud winky
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `activity:cancel`

활동 취소

```bash
magento-cloud activity:cancel [--type TYPE] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

활동 ID. 기본값은 가장 최근 취소 가능한 활동으로 설정됩니다.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

유형별 필터링(기본 활동을 선택할 때)
- 값 필요



### `--all`, `-a`



모든 환경에서 최근 활동 확인(기본 활동을 선택할 때)
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `activity:get`

단일 활동에 대한 자세한 정보 보기

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

활동 ID. 기본값은 가장 최근 활동으로 설정됩니다.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



볼 속성입니다.
- 값 필요


### `--type`

유형별 필터링(기본 활동을 선택할 때)
- 값 필요


### `--state`

상태별로 필터링(기본 활동을 선택할 때): in_progress, 보류 중, 완료 또는 취소됨
- 기본값: `[]`
- 값 필요


### `--result`

결과별 필터링(기본 활동을 선택할 때): 성공 또는 실패
- 값 필요



### `--incomplete`, `-i`



불완전한 활동만 포함합니다(기본 활동을 선택할 때). 이것은 약칭이다 &lt;info>—state=in_progress,보류 중&lt;/info>
- 기본값: `false`
- 값을 허용하지 않음



### `--all`, `-a`



모든 환경에서 최근 활동 확인(기본 활동을 선택할 때)
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `activity:list`

환경 또는 프로젝트에 대한 활동 목록 가져오기

```bash
magento-cloud activity:list [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
activities
```

<!-- app.name -->

```bash
act
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

유형별 활동 필터링
- 값 필요


### `--limit`

표시되는 결과 수를 제한합니다
- 기본값: `10`
- 값 필요


### `--start`

이 날짜 이전에 만들어진 활동만 나열됩니다
- 값 필요


### `--state`

상태별로 활동 필터링: in_progress, 보류 중, 완료 또는 취소됨
- 기본값: `[]`
- 값 필요


### `--result`

결과별 활동 필터링: 성공 또는 실패
- 값 필요



### `--incomplete`, `-i`



불완전한 활동만 나열
- 기본값: `false`
- 값을 허용하지 않음



### `--all`, `-a`



모든 환경의 활동 나열
- 기본값: `false`
- 값을 허용하지 않음


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `activity:log`

활동에 대한 로그 표시

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

활동 ID. 기본값은 가장 최근 활동으로 설정됩니다.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

활동 새로 고침 간격(초)입니다. 새로 고침을 비활성화하려면 0으로 설정합니다.
- 기본값: `3`
- 값 필요



### `--timestamps`, `-t`



각 메시지 옆에 타임스탬프를 표시합니다
- 기본값: `false`
- 값을 허용하지 않음


### `--type`

유형별 필터링(기본 활동을 선택할 때)
- 값 필요


### `--state`

상태별로 필터링(기본 활동을 선택할 때): in_progress, 보류 중, 완료 또는 취소됨
- 기본값: `[]`
- 값 필요


### `--result`

결과별 필터링(기본 활동을 선택할 때): 성공 또는 실패
- 값 필요



### `--incomplete`, `-i`



불완전한 활동만 포함합니다(기본 활동을 선택할 때). 이것은 약칭이다 &lt;info>—state=in_progress,보류 중&lt;/info>
- 기본값: `false`
- 값을 허용하지 않음



### `--all`, `-a`



모든 환경에서 최근 활동 확인(기본 활동을 선택할 때)
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `api:curl`

Magento Cloud API에서 인증된 cURL 요청을 실행합니다

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

API 경로
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



사용할 요청 메서드
- 값 필요



### `--data`, `-d`



보낼 데이터
- 값 필요



### `--include`, `-i`



출력에 헤더 포함
- 기본값: `false`
- 값을 허용하지 않음



### `--head`, `-I`



헤더만 가져오기
- 기본값: `false`
- 값을 허용하지 않음


### `--disable-compression`

curl - 압축된 플래그 사용 안 함
- 기본값: `false`
- 값을 허용하지 않음


### `--enable-glob`

curl 글로빙 사용(—glob 플래그 제거)
- 기본값: `false`
- 값을 허용하지 않음



### `--header`, `-H`



추가 헤더
- 기본값: `[]`
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `app:config-get`

앱 구성 보기

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



볼 구성 속성
- 값 필요


### `--refresh`

캐시를 새로 고치는지 여부
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--identity-file`, `-i`



[사용되지 않는 옵션, 더 이상 사용되지 않습니다.]
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `app:list`

프로젝트의 앱 나열

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
apps
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

캐시를 새로 고치는지 여부
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `auth:api-token-login`

API 토큰을 사용하여 Cloud에 로그인

```bash
magento-cloud auth:api-token-login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `auth:browser-login`

브라우저를 통해 Marketing Cloud에 로그인

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```

<!-- app.name -->

```bash
login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



이미 로그인한 경우에도 다시 로그인합니다.
- 기본값: `false`
- 값을 허용하지 않음


### `--browser`

URL을 여는 데 사용할 브라우저입니다. 없음에 대해 0을 설정합니다.
- 값 필요


### `--pipe`

stdout에 URL을 출력합니다.
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `auth:info`

계정 정보 표시

```bash
magento-cloud auth:info [-P|--property PROPERTY] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<property>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

볼 계정 속성
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



볼 계정 속성(대체 구문)
- 값 필요


### `--refresh`

캐시를 새로 고치는지 여부
- 기본값: `false`
- 값을 허용하지 않음


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `auth:logout`

Magento Cloud에서 로그아웃

```bash
magento-cloud logout [-a|--all] [--other]
```

<!-- app.name -->

```bash
logout
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



모든 로컬 세션에서 로그아웃
- 기본값: `false`
- 값을 허용하지 않음


### `--other`

다른 로컬 세션에서 로그아웃
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 사용되지 않음 ]&lt;/> 사용자 이름과 암호를 사용하여 Marketing Cloud에 로그인합니다

```bash
magento-cloud auth:password-login
```

<!-- app.name -->

```bash
auth:login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `auth:token`

Cloud API 요청에 대한 OAuth 2 액세스 토큰 가져오기

```bash
magento-cloud auth:token
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `blackfire:setup`

프로젝트에 대한 Blackfire.io 통합 설정

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--server_id`

서버 ID
- 값 필요


### `--server_token`

서버 토큰
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `certificate:add`

프로젝트에 SSL 인증서 추가

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--cert`

인증서 파일의 경로
- 값 필요


### `--key`

인증서 개인 키 파일의 경로입니다
- 값 필요


### `--chain`

인증서 체인 파일의 경로
- 기본값: `[]`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `certificate:delete`

프로젝트에서 인증서 삭제

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

인증서 ID(또는 인증서 ID의 시작)
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `certificate:get`

인증서 보기

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

인증서 ID(또는 인증서 ID의 시작)
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



볼 인증서 속성
- 값 필요


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `certificate:list`

프로젝트 인증서 나열

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
certificates
```

<!-- app.name -->

```bash
certs
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--domain`

도메인 이름별로 필터링(대/소문자 구분 안 함 검색)
- 값 필요


### `--exclude-domain`

도메인 이름별로 일치하는 인증서 제외(대/소문자 구분 안 함 검색)
- 값 필요


### `--issuer`

발급자별로 필터링
- 값 필요


### `--only-auto`

자동 제공된 인증서만 표시
- 기본값: `false`
- 값을 허용하지 않음


### `--no-auto`

수동으로 추가한 인증서만 표시
- 기본값: `false`
- 값을 허용하지 않음


### `--ignore-expiry`

만료된 인증서와 만료되지 않은 인증서를 모두 표시합니다
- 기본값: `false`
- 값을 허용하지 않음


### `--only-expired`

만료된 인증서만 표시
- 기본값: `false`
- 값을 허용하지 않음


### `--no-expired`

만료되지 않은 인증서만 표시(기본값)
- 기본값: `false`
- 값을 허용하지 않음


### `--pipe-domains`

인증서가 적용되는 도메인 이름 목록만 반환합니다
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `commit:get`

커밋 세부 정보 표시

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<commit>]
```

<!-- app.name --> <!-- command.usage -->

### `commit`

커밋 SHA입니다. 이렇게 하면 상위 커밋에 대해 &quot;HEAD&quot;을 적용하고, 삽입 기호(^) 또는 기울기(~) 접미사를 사용할 수도 있습니다.
- 기본값: `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



표시할 커밋 속성입니다.
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요


### `--format`

사용되지 않음
- 값 필요


### `--columns`

사용되지 않음
- 기본값: `[]`
- 값 필요


### `--no-header`

사용되지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `commit:list`

목록 커밋

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```

<!-- app.name -->

```bash
commits
```

<!-- app.name --> <!-- command.usage -->

### `commit`

시작 Git 커밋 SHA입니다. 이렇게 하면 상위 커밋에 대해 &quot;HEAD&quot;을 적용하고, 삽입 기호(^) 또는 기울기(~) 접미사를 사용할 수도 있습니다.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--limit`

표시할 커밋 수입니다.
- 기본값: `10`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `db:dump`

원격 데이터베이스의 로컬 덤프 만들기

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
sql-dump
```

<!-- app.name -->

```bash
environment:sql-dump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--schema`

덤프할 스키마입니다. 기본 스키마(일반적으로 &quot;main&quot;)를 사용하려면 생략합니다.
- 값 필요



### `--file`, `-f`



덤프의 사용자 지정 파일 이름입니다
- 값 필요



### `--directory`, `-d`



덤프에 대한 사용자 지정 디렉터리
- 값 필요



### `--gzip`, `-z`



gzip을 사용하여 덤프를 압축
- 기본값: `false`
- 값을 허용하지 않음



### `--timestamp`, `-t`



덤프 파일 이름에 타임스탬프 추가
- 기본값: `false`
- 값을 허용하지 않음



### `--stdout`, `-o`



파일 대신 STDOUT으로 출력
- 기본값: `false`
- 값을 허용하지 않음


### `--table`

포함할 테이블
- 기본값: `[]`
- 값 필요


### `--exclude-table`

제외할 테이블
- 기본값: `[]`
- 값 필요


### `--schema-only`

스키마만 덤프, 데이터 없음
- 기본값: `false`
- 값을 허용하지 않음


### `--charset`

덤프의 문자 집합 인코딩입니다.
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--relationship`, `-r`



사용할 서비스 관계
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `db:size`

데이터베이스의 디스크 사용량 예측

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



크기(바이트)를 표시합니다.
- 기본값: `false`
- 값을 허용하지 않음



### `--cleanup`, `-C`



테이블을 정리할 수 있는지 확인하고 권장 사항을 표시합니다(InnoDb만 해당).
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--relationship`, `-r`



사용할 서비스 관계
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `db:sql`

원격 데이터베이스에서 SQL 실행

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```

<!-- app.name -->

```bash
sql
```

<!-- app.name -->

```bash
environment:sql
```

<!-- app.name --> <!-- command.usage -->

### `query`

실행할 SQL 문
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

테이블 형식 없이 원시 출력 생성
- 기본값: `false`
- 값을 허용하지 않음


### `--schema`

사용할 스키마. 기본 스키마(일반적으로 &quot;main&quot;)를 사용하려면 생략합니다. 스키마를 사용하지 않으려면 빈 문자열을 전달합니다.
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--relationship`, `-r`



사용할 서비스 관계
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `domain:add`

프로젝트에 새 도메인 추가

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

도메인 이름
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

이 도메인의 인증서 파일 경로
- 값 필요


### `--key`

제공된 인증서에 대한 개인 키 파일의 경로입니다.
- 값 필요


### `--chain`

제공된 인증서에 대한 인증서 체인 파일 또는 파일의 경로
- 기본값: `[]`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `domain:delete`

프로젝트에서 도메인 삭제

```bash
magento-cloud domain:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

도메인 이름
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `domain:get`

도메인에 대한 세부 정보 표시

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

도메인 이름
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



볼 도메인 속성
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `domain:list`

모든 도메인 목록 가져오기

```bash
magento-cloud domains [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
domains
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `domain:update`

도메인 업데이트

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

도메인 이름
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

이 도메인의 인증서 파일 경로
- 값 필요


### `--key`

제공된 인증서에 대한 개인 키 파일의 경로입니다.
- 값 필요


### `--chain`

제공된 인증서에 대한 인증서 체인 파일 또는 파일의 경로
- 기본값: `[]`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:activate`

환경 활성화

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name --> <!-- command.usage -->

### `environment`

활성화할 환경

- 기본값: `[]`

- 어레이 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--parent`

활성화하기 전에 새 환경 상위 설정
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:branch`

환경 분기

```bash
magento-cloud branch [--title TITLE] [--force] [--no-clone-parent] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```

<!-- app.name -->

```bash
branch
```

<!-- app.name --> <!-- command.usage -->

### `id`

새 환경의 ID(분기 이름)입니다
<!-- argument -->

### `parent`

새 환경의 상위
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--title`

새 환경의 제목
- 값 필요


### `--force`

분기를 로컬로 체크 아웃할 수 없는 경우에도 새 환경을 만듭니다
- 기본값: `false`
- 값을 허용하지 않음


### `--no-clone-parent`

상위 분기의 데이터를 복제하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:checkout`

환경 확인

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```

<!-- app.name -->

```bash
checkout
```

<!-- app.name --> <!-- command.usage -->

### `id`

체크 아웃할 환경의 ID입니다. 예: &quot;sprint2&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:delete`

환경 삭제

```bash
magento-cloud environment:deactivate [--delete-branch] [--no-delete-branch] [--inactive] [--merged] [--exclude EXCLUDE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name -->

```bash
environment:deactivate
```

<!-- app.name --> <!-- command.usage -->

### `environment`

삭제할 환경

- 기본값: `[]`

- 어레이 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--delete-branch`

원격 Git 분기를 삭제할 수도 있습니다
- 기본값: `false`
- 값을 허용하지 않음


### `--no-delete-branch`

원격 Git 분기는 삭제하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--inactive`

모든 비활성 환경 삭제
- 기본값: `false`
- 값을 허용하지 않음


### `--merged`

병합된 모든 환경 삭제
- 기본값: `false`
- 값을 허용하지 않음


### `--exclude`

삭제하지 않는 환경
- 기본값: `[]`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:http-access`

환경에 대한 HTTP 액세스 설정 업데이트

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
httpaccess
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access`

&quot;permission:address&quot; 형식의 액세스 제한. 모든 주소를 지우려면 0을 사용합니다.
- 기본값: `[]`
- 값 필요


### `--auth`

&quot;username:password&quot; 형식의 HTTP Basic 인증 자격 증명입니다. 모든 자격 증명을 지우려면 0을 사용합니다.
- 기본값: `[]`
- 값 필요


### `--enabled`

액세스 제어를 사용할지 여부: 활성화하려면 1이고 비활성화하려면 0입니다
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:info`

환경에 대한 속성 읽기 또는 설정

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
environment:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

속성의 이름입니다
<!-- argument -->

### `value`

속성에 대한 새 값 설정
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

캐시를 새로 고치는지 여부
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:init`

공개 Git 리포지토리에서 환경 초기화

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```

<!-- app.name --> <!-- command.usage -->

### `url`

Git 리포지토리 URL
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--profile`

프로필의 이름입니다
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:list`

환경 목록 가져오기

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
environments
```

<!-- app.name -->

```bash
env
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--no-inactive`, `-I`



비활성 환경 표시 안 함
- 기본값: `false`
- 값을 허용하지 않음


### `--pipe`

간단한 환경 ID 목록을 출력합니다.
- 기본값: `false`
- 값을 허용하지 않음


### `--refresh`

목록을 새로 고치는지 여부.
- 기본값: `1`
- 값 필요


### `--sort`

정렬 기준 속성
- 기본값: `title`
- 값 필요


### `--reverse`

내림차순 정렬
- 기본값: `false`
- 값을 허용하지 않음


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:logs`

환경 로그 읽기

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [--] [<type>]
```

<!-- app.name -->

```bash
log
```

<!-- app.name -->

```bash
logs
```

<!-- app.name --> <!-- command.usage -->

### `type`

로그 유형(예: &quot;access&quot; 또는 &quot;error&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--lines`

표시할 줄 수
- 기본값: `100`
- 값 필요


### `--tail`

계속해서 로그 테일
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요


### `--worker`

작업자 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:merge`

환경 병합

```bash
magento-cloud merge [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
merge
```

<!-- app.name --> <!-- command.usage -->

### `environment`

병합할 환경
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:push`

환경에 코드 푸시

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--branch] [--parent PARENT] [-W|--no-wait] [--wait] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```

<!-- app.name -->

```bash
push
```

<!-- app.name --> <!-- command.usage -->

### `source`

소스 참조: 분기 이름 또는 커밋 해시
- 기본값: `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

대상 분기 이름입니다
- 값 필요



### `--force`, `-f`



정방향 업데이트 허용
- 기본값: `false`
- 값을 허용하지 않음


### `--force-with-lease`

원격 추적 분기가 최신 상태인 경우 순방향 업데이트 허용
- 기본값: `false`
- 값을 허용하지 않음



### `--set-upstream`, `-u`



대상 환경을 소스 분기의 업스트림으로 설정합니다
- 기본값: `false`
- 값을 허용하지 않음


### `--activate`

푸시하기 전에 환경 활성화
- 기본값: `false`
- 값을 허용하지 않음


### `--branch`

사용되지 않음: 별칭 —activate
- 기본값: `false`
- 값을 허용하지 않음


### `--parent`

새 환경 상위 설정(—activate 또는 —branch에서만 사용)
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:redeploy`

환경 재배포

```bash
magento-cloud redeploy [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
redeploy
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:relationships`

환경의 관계 표시

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```

<!-- app.name -->

```bash
relationships
```

<!-- app.name --> <!-- command.usage -->

### `environment`

환경
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



볼 관계 속성
- 값 필요


### `--refresh`

관계를 새로 고칠 것인지 여부
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:scp`

scp를 사용하여 현재 환경에 파일 복사

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```

<!-- app.name -->

```bash
scp
```

<!-- app.name --> <!-- command.usage -->

### `files`

복사할 파일. 원격 사용: 접두사를 사용하여 원격 위치를 정의할 수 있습니다.

- 기본값: `[]`

- 어레이 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--recursive`, `-r`



전체 디렉터리를 반복적으로 복사
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요


### `--worker`

작업자 이름
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:set-remote`

분기에 매핑할 원격 환경 설정

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```

<!-- app.name --> <!-- command.usage -->

### `environment`

환경 컴퓨터 이름입니다. 분기에 대한 매핑을 제거하려면 0으로 설정하십시오
- 필수 여부

   <!-- argument -->

### `branch`

매핑할 Git 분기(기본값: 현재 분기)
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:ssh`

현재 환경에 SSH

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```

<!-- app.name -->

```bash
ssh
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

환경에서 실행할 명령입니다.

- 기본값: `[]`

- 어레이 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

SSH URL만 출력합니다.
- 기본값: `false`
- 값을 허용하지 않음


### `--all`

모든 SSH URL을 출력합니다(모든 앱의 경우).
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요


### `--worker`

작업자 이름
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:synchronize`

환경의 코드 및/또는 데이터를 해당 상위에서 동기화

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```

<!-- app.name -->

```bash
sync
```

<!-- app.name --> <!-- command.usage -->

### `synchronize`

동기화할 사항: &quot;code&quot;, &quot;data&quot; 또는 둘 다

- 기본값: `[]`

- 어레이 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--rebase`

병합하지 않고 리디렉션을 통해 코드 동기화
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:url`

환경의 공개 URL 가져오기

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
url
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--primary`, `-1`



기본 경로의 URL만 반환
- 기본값: `false`
- 값을 허용하지 않음


### `--browser`

URL을 여는 데 사용할 브라우저입니다. 없음에 대해 0을 설정합니다.
- 값 필요


### `--pipe`

stdout에 URL을 출력합니다.
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `environment:xdebug`

환경에서 Xdebug로 터널을 엽니다.

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
xdebug
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

로컬 포트
- 기본값: `9000`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요


### `--worker`

작업자 이름
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `integration:activity:get`

단일 통합 활동에 대한 세부 정보 보기

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

통합 ID. 목록에서 선택하려면 비워 둡니다.
<!-- argument -->

### `activity`

활동 ID. 기본값은 가장 최근 통합 활동으로 설정됩니다.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



볼 속성입니다.
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



[사용되지 않는 옵션, 사용되지 않음]
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `integration:activity:list`

통합을 위한 활동 목록 가져오기

```bash
magento-cloud i:act [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name -->

```bash
i:act
```

<!-- app.name -->

```bash
integration:activities
```

<!-- app.name --> <!-- command.usage -->

### `id`

통합 ID. 목록에서 선택하려면 비워 둡니다.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

유형별 활동 필터링
- 값 필요


### `--limit`

표시되는 결과 수를 제한합니다
- 기본값: `10`
- 값 필요


### `--start`

이 날짜 이전에 만들어진 활동만 나열됩니다
- 값 필요


### `--state`

상태별로 활동 필터링
- 기본값: `[]`
- 값 필요


### `--result`

결과별 활동 필터링
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



[사용되지 않는 옵션, 사용되지 않음]
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `integration:activity:log`

통합 활동에 대한 로그를 표시합니다

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

통합 ID. 목록에서 선택하려면 비워 둡니다.
<!-- argument -->

### `activity`

활동 ID. 기본값은 가장 최근 통합 활동으로 설정됩니다.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--timestamps`, `-t`



각 메시지 옆에 타임스탬프를 표시합니다
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



[사용되지 않는 옵션, 사용되지 않음]
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `integration:add`

프로젝트에 통합 추가

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

통합 유형(&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;hipchat&#39;, &#39;webhook&#39;, &#39;health.email&#39;, &#39;health.pagerdity&#39;, &#39;health.pagerdale&#39;, &#39;health.webhook&#39;, &#39;script&#39;)
- 값 필요


### `--base-url`

서버 설치의 기본 URL
- 값 필요


### `--username`

Bitbucket Server 사용자 이름
- 값 필요


### `--token`

통합을 위한 액세스 토큰
- 값 필요


### `--key`

Bitbucket OAuth 소비자 키
- 값 필요


### `--secret`

Bitbucket OAuth 소비자 암호
- 값 필요


### `--server-project`

프로젝트(예: &#39;namespace/repo&#39;)
- 값 필요


### `--repository`

추적할 저장소(예: &#39;owner/repository&#39;)
- 값 필요


### `--build-merge-requests`

GitLab: 환경으로 병합 요청 작성
- 기본값: `true`
- 값 필요


### `--build-pull-requests`

모든 가져오기 요청을 환경으로 작성
- 기본값: `true`
- 값 필요


### `--build-draft-pull-requests`

초안 끌어오기 요청 작성
- 기본값: `true`
- 값 필요


### `--build-pull-requests-post-merge`

병합 후 상태에 따라 끌어오기 요청을 작성합니다
- 기본값: `false`
- 값 필요


### `--build-wip-merge-requests`

GitLab: WIP 병합 요청 작성
- 기본값: `true`
- 값 필요


### `--merge-requests-clone-parent-data`

GitLab: 병합 요청을 위한 데이터 복제
- 기본값: `true`
- 값 필요


### `--pull-requests-clone-parent-data`

끌어오기 요청에 대해 상위 환경의 데이터 복제
- 기본값: `true`
- 값 필요


### `--resync-pull-requests`

모든 빌드에서 풀 요청 환경 데이터 다시 동기화
- 기본값: `false`
- 값 필요


### `--fetch-branches`

원격(비활성 환경으로)에서 모든 분기 가져오기
- 기본값: `true`
- 값 필요


### `--prune-branches`

원격 사이트에 없는 분기 삭제
- 기본값: `true`
- 값 필요


### `--room`

HipChat 룸 ID
- 값 필요


### `--url`

Webhook: JSON 데이터를 받을 URL
- 값 필요


### `--shared-key`

Webhook: JWS 공유 암호 키
- 값 필요


### `--file`

업로드할 스크립트가 포함된 로컬 파일의 이름입니다
- 값 필요


### `--events`

작업할 이벤트 목록(예: environment.push
- 기본값: `*`
- 값 필요


### `--states`

작업할 상태 목록(예: 보류 중, in_progress, complete)
- 기본값: `complete`
- 값 필요


### `--environments`

포함할 환경 ID
- 기본값: `*`
- 값 필요


### `--excluded-environments`

제외할 환경 ID
- 기본값: `[]`
- 값 필요


### `--from-address`

[선택 사항입니다] 경고 전자 메일의 사용자 지정 보낸 사람 주소
- 값 필요


### `--recipients`

수신자 이메일 주소
- 기본값: `[]`
- 값 필요


### `--channel`

Slack 채널
- 값 필요


### `--routing-key`

PagerDuty 라우팅 키
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `integration:delete`

프로젝트에서 통합 삭제

```bash
magento-cloud integration:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

통합 ID입니다. 목록에서 선택하려면 비워 둡니다.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `integration:get`

통합에 대한 세부 사항 보기

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

통합 ID. 목록에서 선택하려면 비워 둡니다.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



볼 통합 속성
- 값을 허용합니다


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `integration:list`

프로젝트 통합 목록 보기

```bash
magento-cloud integrations [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
integrations
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `integration:update`

통합 업데이트

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

업데이트할 통합의 ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

통합 유형(&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;hipchat&#39;, &#39;webhook&#39;, &#39;health.email&#39;, &#39;health.pagerdity&#39;, &#39;health.pagerdale&#39;, &#39;health.webhook&#39;, &#39;script&#39;)
- 값 필요


### `--base-url`

서버 설치의 기본 URL
- 값 필요


### `--username`

Bitbucket Server 사용자 이름
- 값 필요


### `--token`

통합을 위한 액세스 토큰
- 값 필요


### `--key`

Bitbucket OAuth 소비자 키
- 값 필요


### `--secret`

Bitbucket OAuth 소비자 암호
- 값 필요


### `--server-project`

프로젝트(예: &#39;namespace/repo&#39;)
- 값 필요


### `--repository`

추적할 저장소(예: &#39;owner/repository&#39;)
- 값 필요


### `--build-merge-requests`

GitLab: 환경으로 병합 요청 작성
- 기본값: `true`
- 값 필요


### `--build-pull-requests`

모든 가져오기 요청을 환경으로 작성
- 기본값: `true`
- 값 필요


### `--build-draft-pull-requests`

초안 끌어오기 요청 작성
- 기본값: `true`
- 값 필요


### `--build-pull-requests-post-merge`

병합 후 상태에 따라 끌어오기 요청을 작성합니다
- 기본값: `false`
- 값 필요


### `--build-wip-merge-requests`

GitLab: WIP 병합 요청 작성
- 기본값: `true`
- 값 필요


### `--merge-requests-clone-parent-data`

GitLab: 병합 요청을 위한 데이터 복제
- 기본값: `true`
- 값 필요


### `--pull-requests-clone-parent-data`

끌어오기 요청에 대해 상위 환경의 데이터 복제
- 기본값: `true`
- 값 필요


### `--resync-pull-requests`

모든 빌드에서 풀 요청 환경 데이터 다시 동기화
- 기본값: `false`
- 값 필요


### `--fetch-branches`

원격(비활성 환경으로)에서 모든 분기 가져오기
- 기본값: `true`
- 값 필요


### `--prune-branches`

원격 사이트에 없는 분기 삭제
- 기본값: `true`
- 값 필요


### `--room`

HipChat 룸 ID
- 값 필요


### `--url`

Webhook: JSON 데이터를 받을 URL
- 값 필요


### `--shared-key`

Webhook: JWS 공유 암호 키
- 값 필요


### `--file`

업로드할 스크립트가 포함된 로컬 파일의 이름입니다
- 값 필요


### `--events`

작업할 이벤트 목록(예: environment.push
- 기본값: `*`
- 값 필요


### `--states`

작업할 상태 목록(예: 보류 중, in_progress, complete)
- 기본값: `complete`
- 값 필요


### `--environments`

포함할 환경 ID
- 기본값: `*`
- 값 필요


### `--excluded-environments`

제외할 환경 ID
- 기본값: `[]`
- 값 필요


### `--from-address`

[선택 사항입니다] 경고 전자 메일의 사용자 지정 보낸 사람 주소
- 값 필요


### `--recipients`

수신자 이메일 주소
- 기본값: `[]`
- 값 필요


### `--channel`

Slack 채널
- 값 필요


### `--routing-key`

PagerDuty 라우팅 키
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `integration:validate`

기존 통합의 유효성 검사

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

통합 ID. 목록에서 선택하려면 비워 둡니다.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `local:build`

로컬에서 현재 프로젝트 빌드

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```

<!-- app.name -->

```bash
build
```

<!-- app.name --> <!-- command.usage -->

### `app`

빌드할 응용 프로그램 지정

- 기본값: `[]`

- 어레이 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--abslinks`, `-a`



절대 링크 사용
- 기본값: `false`
- 값을 허용하지 않음



### `--source`, `-s`



소스 디렉토리입니다. 기본값은 현재 프로젝트 루트입니다.
- 값 필요



### `--destination`, `-d`



각 앱의 웹 루트가 symlink로 연결되는 대상입니다. 기본값: _www
- 값 필요



### `--copy`, `-c`



소스에서 symlink 대신 빌드 디렉토리에 복사합니다.
- 기본값: `false`
- 값을 허용하지 않음


### `--clone`

Git을 사용하여 현재 HEAD을 빌드 디렉터리에 복제합니다
- 기본값: `false`
- 값을 허용하지 않음


### `--run-deploy-hooks`

배포 및/또는 post_deploy 후크 실행
- 기본값: `false`
- 값을 허용하지 않음


### `--no-clean`

이전 빌드를 제거하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--no-archive`

빌드 보관 파일을 만들거나 사용하지 않음
- 기본값: `false`
- 값을 허용하지 않음


### `--no-backup`

이전 빌드를 백업하지 않음
- 기본값: `false`
- 값을 허용하지 않음


### `--no-cache`

캐싱 비활성화
- 기본값: `false`
- 값을 허용하지 않음


### `--no-build-hooks`

빌드 후 후크를 실행하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--no-deps`

빌드 종속성을 로컬로 설치하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--working-copy`

Drush: git을 사용하여 버전을 다운로드하지 않고 각 Drupal 모듈의 리포지토리를 복제합니다
- 기본값: `false`
- 값을 허용하지 않음


### `--concurrency`

Drush: 동시에 처리할 동시 프로젝트 수 설정
- 기본값: `4`
- 값 필요


### `--lock`

Drush: 잠금 파일 만들기 또는 업데이트(Drush 버전 7+에서만 사용 가능)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `local:clean`

이전 프로젝트 빌드 제거

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```

<!-- app.name -->

```bash
clean
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep`

유지할 최대 빌드 수
- 기본값: `5`
- 값 필요


### `--max-age`

빌드의 최대 페이지(초)입니다. 설정하지 않으면 무시됩니다.
- 값 필요


### `--include-active`

활성 빌드를 삭제할 수도 있습니다.
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `local:dir`

로컬 프로젝트 루트 찾기

```bash
magento-cloud dir [<subdir>]
```

<!-- app.name -->

```bash
dir
```

<!-- app.name --> <!-- command.usage -->

### `subdir`

찾을 하위 디렉터리(&#39;local&#39;, &#39;web&#39; 또는 &#39;shared&#39;)
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `mount:download`

다시 동기화를 사용하여 마운트에서 파일 다운로드

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



모든 마운트에서 다운로드
- 기본값: `false`
- 값을 허용하지 않음



### `--mount`, `-m`



마운트(앱 상대 경로)
- 값 필요


### `--target`

파일을 다운로드할 디렉터리입니다. —모두 사용하면 마운트 경로가 추가됩니다
- 값 필요


### `--source-path`

마운트 경로가 아닌 마운트 소스 경로를 타겟의 하위 디렉토리로 사용합니다. 이 경우 모두 사용됩니다
- 기본값: `false`
- 값을 허용하지 않음


### `--delete`

대상 디렉토리에서 외부 파일을 삭제할지 여부
- 기본값: `false`
- 값을 허용하지 않음


### `--exclude`

다운로드(패턴)에서 제외할 파일
- 기본값: `[]`
- 값 필요


### `--include`

다운로드(패턴)에 포함할 파일
- 기본값: `[]`
- 값 필요


### `--refresh`

캐시를 새로 고치는지 여부
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요


### `--worker`

작업자 이름
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `mount:list`

마운트 목록 가져오기

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name -->

```bash
mounts
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--paths`

마운트 경로만 출력(라인당 하나)
- 기본값: `false`
- 값을 허용하지 않음


### `--refresh`

캐시를 새로 고치는지 여부
- 기본값: `false`
- 값을 허용하지 않음


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요


### `--worker`

작업자 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `mount:size`

마운트의 디스크 사용량을 확인합니다

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



크기 표시(바이트)
- 기본값: `false`
- 값을 허용하지 않음


### `--refresh`

캐시 새로 고침
- 기본값: `false`
- 값을 허용하지 않음


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요


### `--worker`

작업자 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `mount:upload`

rsync를 사용하여 파일을 마운트에 업로드합니다.

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--source`

업로드할 파일이 포함된 디렉토리
- 값 필요



### `--mount`, `-m`



마운트(앱 상대 경로)
- 값 필요


### `--delete`

마운트에서 외부 파일을 삭제할 것인지 여부
- 기본값: `false`
- 값을 허용하지 않음


### `--exclude`

업로드에서 제외할 파일(패턴)
- 기본값: `[]`
- 값 필요


### `--include`

업로드에 포함할 파일(패턴)
- 기본값: `[]`
- 값 필요


### `--refresh`

캐시를 새로 고치는지 여부
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요


### `--worker`

작업자 이름
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `project:clear-build-cache`

프로젝트의 빌드 캐시 지우기

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT] [--host HOST]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `project:curl`

프로젝트의 API에서 인증된 cURL 요청을 실행합니다

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [-p|--project PROJECT] [--host HOST] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

API 경로
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



사용할 요청 메서드
- 값 필요



### `--data`, `-d`



보낼 데이터
- 값 필요



### `--include`, `-i`



출력에 헤더 포함
- 기본값: `false`
- 값을 허용하지 않음



### `--head`, `-I`



헤더만 가져오기
- 기본값: `false`
- 값을 허용하지 않음


### `--disable-compression`

curl - 압축된 플래그 사용 안 함
- 기본값: `false`
- 값을 허용하지 않음


### `--enable-glob`

curl 글로빙 사용(—glob 플래그 제거)
- 기본값: `false`
- 값을 허용하지 않음



### `--header`, `-H`



추가 헤더
- 기본값: `[]`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `project:get`

로컬에서 프로젝트 복제

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [--host HOST] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```

<!-- app.name -->

```bash
get
```

<!-- app.name --> <!-- command.usage -->

### `project`

프로젝트 ID
<!-- argument -->

### `directory`

복제할 디렉토리입니다. 기본값은 프로젝트 제목입니다
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--environment`, `-e`



복제할 환경 ID입니다. 기본값은 프로젝트 기본값이나 사용 가능한 첫 번째 환경입니다
- 값 필요


### `--depth`

얕은 클론 생성: 기록에 있는 커밋 수 제한
- 값 필요


### `--build`

복제 후 프로젝트 빌드
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `project:info`

프로젝트에 대한 속성을 읽거나 설정합니다

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
project:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

속성의 이름입니다
<!-- argument -->

### `value`

속성에 대한 새 값 설정
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

캐시를 새로 고치는지 여부
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `project:list`

모든 활성 프로젝트 목록 가져오기

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
projects
```

<!-- app.name -->

```bash
pro
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--pipe`

간단한 프로젝트 ID 목록 출력
- 기본값: `false`
- 값을 허용하지 않음


### `--host`

지역 호스트 이름별로 필터링(정확히 일치)
- 값 필요


### `--title`

제목에 따라 필터링(대/소문자 구분 안 함 검색)
- 값 필요


### `--my`

소유한 프로젝트만 표시
- 기본값: `false`
- 값을 허용하지 않음


### `--refresh`

목록을 새로 고치는지 여부
- 기본값: `1`
- 값 필요


### `--sort`

정렬 기준 속성
- 기본값: `title`
- 값 필요


### `--reverse`

내림차순 정렬
- 기본값: `false`
- 값을 허용하지 않음


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `project:set-remote`

현재 Git 리포지토리에 대한 원격 프로젝트 설정

```bash
magento-cloud project:set-remote [<project>]
```

<!-- app.name --> <!-- command.usage -->

### `project`

프로젝트 ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 사용되지 않음 ]&lt;/> 프로젝트에서 변수를 삭제합니다

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

변수 이름
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 사용되지 않음 ]&lt;/> 프로젝트에 대한 변수 보기

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name -->

```bash
project-variables
```

<!-- app.name -->

```bash
pvget
```

<!-- app.name -->

```bash
project:variable:list
```

<!-- app.name --> <!-- command.usage -->

### `name`

변수 이름
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

전체 변수 값만 출력합니다(&quot;name&quot;을 지정해야 함).
- 기본값: `false`
- 값을 허용하지 않음


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 사용되지 않음 ]&lt;/> 프로젝트에 대한 변수 설정

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
pvset
```

<!-- app.name --> <!-- command.usage -->

### `name`

변수 이름
- 필수 여부

   <!-- argument -->

### `value`

변수 값
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

값을 JSON으로 표시
- 기본값: `false`
- 값을 허용하지 않음


### `--no-visible-build`

빌드 시 이 변수를 노출하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--no-visible-runtime`

런타임에 이 변수를 노출하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `repo:cat`

프로젝트 리포지토리에서 파일 읽기

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

파일 경로
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--commit`, `-c`



커밋 SHA입니다. 이렇게 하면 상위 커밋에 대해 &quot;HEAD&quot;을 적용하고, 삽입 기호(^) 또는 기울기(~) 접미사를 사용할 수도 있습니다.
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `repo:ls`

프로젝트 리포지토리의 파일 나열

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

하위 디렉토리에 대한 경로
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--directories`, `-d`



디렉터리만 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--files`, `-f`



파일만 표시
- 기본값: `false`
- 값을 허용하지 않음


### `--git-style`

&quot;git ls-tree&quot;와 유사한 스타일 출력
- 기본값: `false`
- 값을 허용하지 않음



### `--commit`, `-c`



커밋 SHA입니다. 이렇게 하면 상위 커밋에 대해 &quot;HEAD&quot;을 적용하고, 삽입 기호(^) 또는 기울기(~) 접미사를 사용할 수도 있습니다.
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `route:get`

경로에 대한 자세한 정보 보기

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```

<!-- app.name --> <!-- command.usage -->

### `route`

경로의 원래 URL입니다
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--id`

선택할 경로 ID
- 값 필요



### `--primary`, `-1`



기본 경로를 선택합니다
- 기본값: `false`
- 값을 허용하지 않음



### `--property`, `-P`



표시할 속성
- 값 필요


### `--refresh`

경로 캐시 무시
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



[사용되지 않는 옵션, 더 이상 사용되지 않습니다.]
- 값 필요



### `--identity-file`, `-i`



[사용되지 않는 옵션, 더 이상 사용되지 않습니다.]
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `route:list`

환경에 대한 모든 경로 나열

```bash
magento-cloud routes [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<environment>]
```

<!-- app.name -->

```bash
routes
```

<!-- app.name -->

```bash
environment:routes
```

<!-- app.name --> <!-- command.usage -->

### `environment`

환경 ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

경로 캐시 무시
- 기본값: `false`
- 값을 허용하지 않음


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `self:install`

CLI 구성 파일 설치 또는 업데이트

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```

<!-- app.name -->

```bash
local:install
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--shell-type`

자동 완료에 대한 셸 유형(bash 또는 zsh)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `self:stats`

GitHub 패키지 다운로드에서 통계 보기

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--page`, `-p`



페이지 번호
- 기본값: `1`
- 값 필요



### `--count`, `-c`



페이지당 결과 수(최대: 100)
- 기본값: `20`
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `self:update`

CLI를 최신 버전으로 업데이트

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```

<!-- app.name -->

```bash
self-update
```

<!-- app.name -->

```bash
update
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-major`

부 버전 또는 패치 버전 간 업데이트만 가능
- 기본값: `false`
- 값을 허용하지 않음


### `--unstable`

가능한 경우 새 불안정한 버전으로 업데이트합니다
- 기본값: `false`
- 값을 허용하지 않음


### `--manifest`

매니페스트 파일 위치 재정의
- 값 필요


### `--current-version`

현재 버전 무시
- 값 필요


### `--timeout`

버전 확인에 대한 시간 제한
- 기본값: `30`
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `service:list`

프로젝트에 서비스 나열

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
services
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

캐시를 새로 고치는지 여부
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `service:mongo:dump`

MongoDB에서 데이터의 이진 아카이브 덤프를 만듭니다

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongodump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



덤프할 컬렉션
- 값 필요



### `--gzip`, `-z`



gzip을 사용하여 덤프를 압축
- 기본값: `false`
- 값을 허용하지 않음



### `--stdout`, `-o`



파일 대신 STDOUT으로 출력
- 기본값: `false`
- 값을 허용하지 않음



### `--relationship`, `-r`



사용할 서비스 관계
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `service:mongo:export`

MongoDB에서 데이터 내보내기

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongoexport
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



내보낼 컬렉션
- 값 필요


### `--jsonArray`

데이터를 단일 JSON 배열로 내보냅니다
- 기본값: `false`
- 값을 허용하지 않음


### `--type`

내보내기 유형(예: &quot;csv&quot;
- 값 필요



### `--fields`, `-f`



내보낼 필드
- 기본값: `[]`
- 값 필요



### `--relationship`, `-r`



사용할 서비스 관계
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `service:mongo:restore`

데이터의 이진 아카이브 덤프를 MongoDB로 복원

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongorestore
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



복원할 컬렉션입니다.
- 값 필요



### `--relationship`, `-r`



사용할 서비스 관계
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `service:mongo:shell`

MongoDB 셸 사용

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongo
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--eval`

셸에 JavaScript 조각을 전달합니다
- 값 필요



### `--relationship`, `-r`



사용할 서비스 관계
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `service:redis-cli`

Redis CLI 액세스

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```

<!-- app.name -->

```bash
redis
```

<!-- app.name --> <!-- command.usage -->

### `args`

Redis 명령에 추가할 인수
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--relationship`, `-r`



사용할 서비스 관계
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 베타 ]&lt;/> 세션 간 전환

```bash
magento-cloud session:switch [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

새 세션 ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `snapshot:create`

환경에 대한 스냅샷 만들기

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
backup
```

<!-- app.name -->

```bash
backup:create
```

<!-- app.name -->

```bash
environment:backup
```

<!-- app.name --> <!-- command.usage -->

### `environment`

환경
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--live`

라이브 백업: 환경을 중지하지 마십시오. 설정된 경우 백업 도중 환경이 실행 및 접속 상태로 유지됩니다. 따라서 일관되지 않은 상태에서 데이터를 백업할 위험이 있어 다운타임이 줄어듭니다.
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `snapshot:list`

사용 가능한 환경 스냅샷 목록

```bash
magento-cloud snapshots [--limit LIMIT] [--start START] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
snapshots
```

<!-- app.name -->

```bash
backups
```

<!-- app.name -->

```bash
backup:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--limit`

스냅샷 수를 목록으로 제한
- 기본값: `10`
- 값 필요


### `--start`

이 날짜 이전에 만들어진 스냅샷만 나열됩니다.
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `snapshot:restore`

환경 스냅샷 복원

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```

<!-- app.name -->

```bash
environment:restore
```

<!-- app.name -->

```bash
snapshot:restore
```

<!-- app.name --> <!-- command.usage -->

### `snapshot`

스냅샷의 이름입니다. 기본값은 가장 최근 값으로 설정됩니다
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

복원할 환경입니다. 기본값은 스냅샷의 현재 환경으로 설정됩니다
- 값 필요


### `--branch-from`

—target이 아직 존재하지 않으면 새 환경의 상위를 지정합니다
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 베타 ]&lt;/> 소스 작업 실행

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```

<!-- app.name --> <!-- command.usage -->

### `operation`

작업 이름
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--variable`

작업 중에 설정할 변수(형식) &lt;info>type:name=value&lt;/info>
- 기본값: `[]`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `ssh-cert:info`

현재 SSH 인증서에 대한 정보 표시

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-refresh`

인증서가 잘못된 경우 인증서를 새로 고치지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--property`, `-P`



표시할 인증서 속성
- 값 필요


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `ssh-cert:load`

SSH 인증서 생성

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh-only`

필요한 경우 인증서만 새로 고칩니다(SSH 구성을 작성하지 않음)
- 기본값: `false`
- 값을 허용하지 않음


### `--new`

인증서를 강제로 새로 고칩니다.
- 기본값: `false`
- 값을 허용하지 않음


### `--new-key`

[사용되지 않음] 대신 —new
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `ssh-key:add`

새 SSH 키 추가

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

기존 SSH 공개 키의 경로입니다
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--name`

키를 식별할 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `ssh-key:delete`

SSH 키 삭제

```bash
magento-cloud ssh-key:delete [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

삭제할 SSH 키의 ID입니다
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `ssh-key:list`

계정에 SSH 키 목록 가져오기

```bash
magento-cloud ssh-keys [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
ssh-keys
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `subscription:info`

구독 속성 읽기 또는 수정

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<property>] [<value>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

속성의 이름입니다
<!-- argument -->

### `value`

속성에 대한 새 값 설정
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--id`, `-s`



구독 ID
- 값 필요


### `--date-fmt`

날짜 형식(PHP 날짜 형식 문자열)
- 기본값: `c`
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `tunnel:close`

SSH 터널 닫기

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



모든 터널 닫기
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `tunnel:info`

SSH 터널에 대한 관계 정보 보기

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



볼 관계 속성
- 값 필요



### `--encode`, `-c`



base64로 인코딩된 JSON으로 출력
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `tunnel:list`

SSH 터널 나열

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
tunnels
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



모든 터널 보기
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `tunnel:open`

앱 관계로 SSH 터널 열기

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--gateway-ports`, `-g`



원격 호스트가 로컬 전달된 포트에 연결할 수 있도록 허용
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `tunnel:single`

앱 관계에 대한 단일 SSH 터널 열기

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

로컬 포트
- 값 필요



### `--gateway-ports`, `-g`



원격 호스트가 로컬 전달된 포트에 연결할 수 있도록 허용
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--app`, `-A`



원격 응용 프로그램 이름
- 값 필요



### `--relationship`, `-r`



사용할 서비스 관계
- 값 필요



### `--identity-file`, `-i`



사용할 SSH ID(개인 키)
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `user:add`

프로젝트에 사용자 추가

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

사용자의 이메일 주소입니다
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



사용자의 프로젝트 역할(&#39;admin&#39; 또는 &#39;viewer&#39;) 또는 환경별 역할(예: &#39;master:contributor&#39; 또는 &#39;stage:viewer&#39;). 문자 % 는 환경 ID에서 와일드카드로 사용할 수 있습니다(예: ). &#39;%:viewer&#39;. 역할은 약칭할 수 있습니다(예: ). &#39;master:c&#39;
- 기본값: `[]`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `user:delete`

프로젝트에서 사용자 삭제

```bash
magento-cloud user:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <email>
```

<!-- app.name --> <!-- command.usage -->

### `email`

사용자의 이메일 주소입니다
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `user:get`

사용자의 역할 보기

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```

<!-- app.name -->

```bash
user:role
```

<!-- app.name --> <!-- command.usage -->

### `email`

사용자의 이메일 주소입니다
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



역할 수준(&#39;프로젝트&#39; 또는 &#39;환경&#39;)
- 값 필요


### `--pipe`

역할을 다음으로 출력(변경한 후)
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--role`, `-r`



[사용되지 않음: 사용자:업데이트 를 사용하여 사용자 역할 변경]
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `user:list`

프로젝트 사용자 나열

```bash
magento-cloud users [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
users
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `user:update`

프로젝트에서 사용자 역할 업데이트

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

사용자의 이메일 주소입니다
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



사용자의 프로젝트 역할(&#39;admin&#39; 또는 &#39;viewer&#39;) 또는 환경별 역할(예: &#39;master:contributor&#39; 또는 &#39;stage:viewer&#39;). 문자 % 는 환경 ID에서 와일드카드로 사용할 수 있습니다(예: ). &#39;%:viewer&#39;. 역할은 약칭할 수 있습니다(예: ). &#39;master:c&#39;
- 기본값: `[]`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `variable:create`

변수 만들기

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

변수 이름
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



변수(&#39;project&#39; 또는 &#39;environment&#39;)를 설정할 레벨
- 값 필요


### `--name`

변수 이름
- 값 필요


### `--value`

변수 값
- 값 필요


### `--json`

변수가 JSON 형식이 지정되었는지 여부
- 기본값: `false`
- 값 필요


### `--sensitive`

변수가 중요한지 여부
- 기본값: `false`
- 값 필요


### `--prefix`

변수 이름의 접두사(예: &#39;none&#39; 또는 &#39;env:&#39;)
- 기본값: `none`
- 값 필요


### `--enabled`

변수를 활성화할지 여부
- 기본값: `true`
- 값 필요


### `--inheritable`

변수가 하위 환경에 의해 상속될 수 있는지 여부
- 기본값: `true`
- 값 필요


### `--visible-build`

변수가 빌드 시 표시되어야 하는지 여부
- 기본값: `true`
- 값 필요


### `--visible-runtime`

런타임 시 변수를 표시해야 하는지 여부
- 기본값: `true`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `variable:delete`

변수 삭제

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

변수 이름
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



변수 수준(&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; 또는 &#39;e&#39;)
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 사용되지 않음 ]&lt;/> 활성화된 환경 수준 변수 비활성화

```bash
magento-cloud variable:disable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

변수 이름
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 사용되지 않음 ]&lt;/> 비활성화된 환경 수준 변수를 활성화합니다

```bash
magento-cloud variable:enable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

변수 이름
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `variable:get`

변수 보기

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```

<!-- app.name -->

```bash
vget
```

<!-- app.name --> <!-- command.usage -->

### `name`

변수 이름
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



단일 변수 속성 보기
- 값 필요



### `--level`, `-l`



변수 수준(&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; 또는 &#39;e&#39;)
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요


### `--pipe`

[사용되지 않는 옵션] 변수 값만 출력
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `variable:list`

목록 변수

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
variables
```

<!-- app.name -->

```bash
var
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--level`, `-l`



변수 수준(&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; 또는 &#39;e&#39;)
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 사용되지 않음 ]&lt;/> 환경에 대한 변수 설정

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
vset
```

<!-- app.name --> <!-- command.usage -->

### `name`

변수 이름
- 필수 여부

   <!-- argument -->

### `value`

변수 값
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

값을 JSON으로 표시
- 기본값: `false`
- 값을 허용하지 않음


### `--disabled`

변수를 비활성화된 것으로 표시합니다
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `variable:update`

변수 업데이트

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

변수 이름
- 필수 여부

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



변수 수준(&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; 또는 &#39;e&#39;)
- 값 필요


### `--value`

변수 값
- 값 필요


### `--json`

변수가 JSON 형식이 지정되었는지 여부
- 기본값: `false`
- 값 필요


### `--sensitive`

변수가 중요한지 여부
- 기본값: `false`
- 값 필요


### `--enabled`

변수를 활성화할지 여부
- 기본값: `true`
- 값 필요


### `--inheritable`

변수가 하위 환경에 의해 상속될 수 있는지 여부
- 기본값: `true`
- 값 필요


### `--visible-build`

변수가 빌드 시 표시되어야 하는지 여부
- 기본값: `true`
- 값 필요


### `--visible-runtime`

런타임 시 변수를 표시해야 하는지 여부
- 기본값: `true`
- 값 필요



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요



### `--no-wait`, `-W`



작업이 완료될 때까지 기다리지 마십시오
- 기본값: `false`
- 값을 허용하지 않음


### `--wait`

작업이 완료될 때까지 대기(기본값)
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size -->

## `worker:list`

배치된 모든 작업자 목록 가져오기

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
workers
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

캐시를 새로 고치는지 여부
- 기본값: `false`
- 값을 허용하지 않음



### `--project`, `-p`



프로젝트 ID 또는 URL
- 값 필요


### `--host`

프로젝트의 API 호스트 이름
- 값 필요



### `--environment`, `-e`



환경 ID
- 값 필요


### `--format`

출력 형식(&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; 또는 &quot;plain&quot;)
- 기본값: `table`
- 값 필요


### `--columns`

표시할 열(쉼표로 구분된 목록 또는 여러 값)
- 기본값: `[]`
- 값 필요


### `--no-header`

테이블 헤더를 출력하지 마십시오
- 기본값: `false`
- 값을 허용하지 않음



### `--help`, `-h`



이 도움말 메시지 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--quiet`, `-q`



메시지를 출력하지 않음
- 기본값: `false`
- 값을 허용하지 않음



### `--verbose`, `-v|-vv|-vvv`



메시지 세부 정보 증가
- 기본값: `false`
- 값을 허용하지 않음



### `--version`, `-V`



이 응용 프로그램 버전 표시
- 기본값: `false`
- 값을 허용하지 않음



### `--yes`, `-y`



예/아니오 질문에 &quot;예&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음



### `--no`, `-n`



예/아니오 질문에 &quot;아니오&quot;라고 대답하십시오. 상호 작용 비활성화
- 기본값: `false`
- 값을 허용하지 않음 <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->