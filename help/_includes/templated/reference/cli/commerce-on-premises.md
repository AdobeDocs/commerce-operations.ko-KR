---
source-git-commit: 23d55385046de18b238c90f6a99be692f1ce7561
workflow-type: tm+mt
source-wordcount: '15643'
ht-degree: 0%

---
# bin/magento(Adobe Commerce 온프레미스)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**버전**: 2.4.5

이 참조에는 `bin/magento` 명령줄 도구.
초기 목록은 `bin/magento list` 명령입니다.
를 사용하십시오 [&quot;CLI 명령 추가&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) 사용자 정의 CLI 명령을 추가하는 가이드

>[!NOTE]
>
>을 호출할 수 있습니다 `bin/magento` 전체 명령 이름 대신 바로 가기를 사용하는 CLI 명령. 예를 들어 `bin/magento setup:upgrade` 사용 `bin/magento s:up`, `bin/magento s:upg`. 자세한 내용은 [단축키 구문](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) CLI 명령에 바로 가기를 사용하는 방법을 이해하기 위한 것입니다.

>[!NOTE]
>
>이 참조는 애플리케이션 코드 베이스에서 생성됩니다. 컨텐츠를 변경하려면 [codebase](https://github.com/magento) 리포지토리를 사용하여 검토를 위해 변경 사항을 제출합니다. 다른 방법은 다음과 같습니다 _피드백 제공_ (오른쪽 상단에 있는 링크를 찾습니다.) 기여 지침은 [코드 기여](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `help`

명령에 대한 도움말 표시

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

명령 이름

- 기본값: `help`


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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `list`

목록 명령

```bash
bin/magento list [--raw] [--format FORMAT] [--] [<namespace>]
```


### `namespace`

네임스페이스 이름


### `--raw`

원시 명령 목록을 출력하려면

- 기본값: `false`
- 값을 허용하지 않음

### `--format`

출력 형식(txt, xml, json 또는 md)

- 기본값: `txt`
- 값 필요


## `admin:adobe-ims:disable`

Adobe IMS 모듈 비활성화

```bash
bin/magento admin:adobe-ims:disable
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `admin:adobe-ims:enable`

Adobe IMS 모듈을 활성화합니다.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

### `--organization-id`, `-o`

Adobe IMS 구성에 대한 조직 ID를 설정합니다. 모듈을 활성화할 때 필요합니다.

- 값을 허용합니다

### `--client-id`, `-c`

Adobe IMS 구성에 대한 클라이언트 ID를 설정합니다. 모듈을 활성화할 때 필요합니다.

- 값을 허용합니다

### `--client-secret`, `-s`

Adobe IMS 구성에 대한 클라이언트 암호 를 설정합니다. 모듈을 활성화할 때 필요합니다.

- 값을 허용합니다

### `--2fa`, `-t`

Adobe Admin Console에서 조직에 대해 2FA가 활성화되어 있는지 확인합니다. 모듈을 활성화할 때 필요합니다.

- 값을 허용합니다

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `admin:adobe-ims:info`

Adobe IMS 모듈 구성 정보

```bash
bin/magento admin:adobe-ims:info
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `admin:adobe-ims:status`

Adobe IMS 모듈 상태

```bash
bin/magento admin:adobe-ims:status
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `admin:user:create`

관리자 만들기

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--admin-user`

(필수) 관리 사용자

- 값 필요

### `--admin-password`

(필수) 관리자 암호

- 값 필요

### `--admin-email`

(필수) 관리 이메일

- 값 필요

### `--admin-firstname`

(필수) 관리자 이름

- 값 필요

### `--admin-lastname`

(필수) 관리자 성

- 값 필요

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `admin:user:unlock`

관리자 계정 잠금 해제

```bash
bin/magento admin:user:unlock <username>
```


### `username`

잠금을 해제할 관리자 사용자 이름

- 필수 여부

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `app:config:dump`

응용 프로그램의 덤프 만들기

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

공백으로 구분된 구성 유형 목록 또는 모두 덤프하려면 생략합니다. [범위, 테마, 시스템, i18n]

- 기본값: `[]`

- 어레이

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `app:config:import`

공유 구성 파일의 데이터를 적절한 데이터 저장소로 가져오기

```bash
bin/magento app:config:import
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `app:config:status`

구성 전달에 업데이트가 필요한지 확인

```bash
bin/magento app:config:status
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `braintree:migrate`

Magento 1 데이터베이스에서 저장된 카드 마이그레이션

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

### `--host`

호스트 이름/IP. 포트는 선택 사항입니다

- 값 필요

### `--dbname`

데이터베이스 이름

- 값 필요

### `--username`

데이터베이스 사용자 이름. 읽기 권한이 있어야 합니다.

- 값 필요

### `--password`

암호

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `cache:clean`

캐시 유형 정리

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

모든 캐시 유형에 적용할 수 있도록 공백으로 구분된 캐시 유형 목록입니다.

- 기본값: `[]`

- 어레이

### `--bootstrap`

부트스트랩의 매개 변수 추가 또는 재정의

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `cache:disable`

캐시 유형 비활성화

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

모든 캐시 유형에 적용할 수 있도록 공백으로 구분된 캐시 유형 목록입니다.

- 기본값: `[]`

- 어레이

### `--bootstrap`

부트스트랩의 매개 변수 추가 또는 재정의

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `cache:enable`

캐시 유형 사용

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

모든 캐시 유형에 적용할 수 있도록 공백으로 구분된 캐시 유형 목록입니다.

- 기본값: `[]`

- 어레이

### `--bootstrap`

부트스트랩의 매개 변수 추가 또는 재정의

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `cache:flush`

캐시 유형에서 사용하는 캐시 저장소를 플러시합니다.

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

모든 캐시 유형에 적용할 수 있도록 공백으로 구분된 캐시 유형 목록입니다.

- 기본값: `[]`

- 어레이

### `--bootstrap`

부트스트랩의 매개 변수 추가 또는 재정의

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `cache:status`

캐시 상태 확인

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

### `--bootstrap`

부트스트랩의 매개 변수 추가 또는 재정의

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `catalog:images:resize`

크기가 조정된 제품 이미지를 만듭니다

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

비동기 모드에서 이미지 크기 조정

- 기본값: `false`
- 값을 허용하지 않음

### `--skip_hidden_images`

제품 페이지에서 숨김으로 표시된 이미지를 처리하지 않음

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `catalog:product:attributes:cleanup`

사용하지 않은 제품 속성을 제거합니다.

```bash
bin/magento catalog:product:attributes:cleanup
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `cms:wysiwyg:restrict`

사용자 HTML 컨텐츠 유효성 검사를 적용할지 또는 대신 경고를 표시할지 여부를 설정합니다

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```


### `restrict`

y\n

- 필수 여부

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `config:sensitive:set`

중요한 구성 값 설정

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```


### `path`

구성 경로(예: group/section/field_name)


### `value`

구성 값


### `--interactive`, `-i`

모든 중요한 변수를 설정하려면 대화형 모드를 활성화하십시오

- 기본값: `false`
- 값을 허용하지 않음

### `--scope`

&#39;default&#39;를 사용하지 않는 경우 구성 범위

- 기본값: `default`
- 값을 허용합니다

### `--scope-code`

구성에 대한 범위 코드, 기본적으로 빈 문자열

- 기본값: &quot;
- 값을 허용합니다

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `config:set`

시스템 구성 변경

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```


### `path`

섹션/그룹/field_name 형식의 구성 경로

- 필수 여부

### `value`

구성 값

- 필수 여부

### `--scope`

구성 범위(기본, 웹 사이트 또는 저장소)

- 기본값: `default`
- 값 필요

### `--scope-code`

범위 코드(범위가 &#39;기본값&#39;이 아닌 경우에만 필수)

- 값 필요

### `--lock-env`, `-e`

관리에서 수정할 수 없는 잠금 값(app/etc/env.php에 저장됨)

- 기본값: `false`
- 값을 허용하지 않음

### `--lock-config`, `-c`

다른 설치와 값을 잠금 및 공유하고, 관리에서 수정을 방지합니다(app/etc/config.php에 저장됨).

- 기본값: `false`
- 값을 허용하지 않음

### `--lock`, `-l`

사용하지 않으면 대신 —lock-env 옵션을 사용하십시오.

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `config:show`

지정된 경로에 대한 구성 값을 표시합니다. 경로를 지정하지 않으면 저장된 값이 모두 표시됩니다

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


### `path`

구성 경로(예: section_id/group_id/field_id)


### `--scope`

구성 범위를 지정하지 않으면 &#39;기본&#39; 범위가 사용됩니다

- 기본값: `default`
- 값을 허용합니다

### `--scope-code`

범위 코드(범위가 아닌 경우에만 필수) `default`)

- 기본값: &quot;
- 값을 허용합니다

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `cron:install`

현재 사용자에 대한 crontab을 생성하고 설치합니다.

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

### `--force`, `-f`

강제 설치 작업

- 기본값: `false`
- 값을 허용하지 않음

### `--non-optional`, `-d`

선택 사항이 아닌(기본값) 작업만 설치합니다

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `cron:remove`

crontab에서 작업 제거

```bash
bin/magento cron:remove
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `cron:run`

예약별로 작업 실행

```bash
bin/magento cron:run [--group GROUP] [--bootstrap BOOTSTRAP]
```

### `--group`

지정된 그룹에서만 작업 실행

- 값 필요

### `--bootstrap`

부트스트랩의 매개 변수 추가 또는 재정의

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `customer:hash:upgrade`

최신 알고리즘에 따라 고객의 해시 업그레이드

```bash
bin/magento customer:hash:upgrade
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `deploy:mode:set`

응용 프로그램 모드를 설정합니다.

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

설정할 애플리케이션 모드입니다. 사용 가능한 옵션은 &quot;개발자&quot; 또는 &quot;프로덕션&quot;입니다

- 필수 여부

### `--skip-compilation`, `-s`

정적 콘텐츠(생성된 코드, 사전 처리된 CSS 및 pub/static/)의 자산 지우기 및 재생성을 건너뜁니다.

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `deploy:mode:show`

현재 응용 프로그램 모드를 표시합니다.

```bash
bin/magento deploy:mode:show
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:di:info`

명령의 종속성 삽입 구성에 대한 정보를 제공합니다.

```bash
bin/magento dev:di:info <class>
```


### `class`

클래스 이름

- 필수 여부

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:email:newsletter-compatibility-check`

뉴스레터 템플릿에서 잠재적인 변수 사용 호환성 문제를 검사합니다.

```bash
bin/magento dev:email:newsletter-compatibility-check
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:email:override-compatibility-check`

잠재적인 변수 사용 호환성 문제에 대해 이메일 템플릿 무시 검색

```bash
bin/magento dev:email:override-compatibility-check
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:profiler:disable`

프로파일러를 비활성화합니다.

```bash
bin/magento dev:profiler:disable
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:profiler:enable`

프로파일러를 활성화합니다.

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

프로파일러 유형


### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:query-log:disable`

DB 쿼리 로깅 사용 안 함

```bash
bin/magento dev:query-log:disable
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:query-log:enable`

DB 쿼리 로깅 활성화

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

### `--include-all-queries`

모든 쿼리를 기록합니다. [true\|false]

- 기본값: `true`
- 값을 허용합니다

### `--query-time-threshold`

시간 임계값을 질의합니다.

- 기본값: `0.001`
- 값을 허용합니다

### `--include-call-stack`

호출 스택을 포함합니다. [true\|false]

- 기본값: `true`
- 값을 허용합니다

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:source-theme:deploy`

테마에 대한 소스 파일을 수집하고 게시합니다.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


### `file`

사전 처리할 파일(확장자 없이 파일을 지정해야 함)

- 기본값: `css/styles-mcss/styles-l`

- 어레이

### `--type`

소스 파일 유형: [less]

- 기본값: `less`
- 값 필요

### `--locale`

로케일: [en_US]

- 기본값: `en_US`
- 값 필요

### `--area`

영역: [frontend\|adminhtml]

- 기본값: `frontend`
- 값 필요

### `--theme`

테마: [공급업체/테마]

- 기본값: `Magento/luma`
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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:template-hints:disable`

프런트 엔드 템플릿 힌트를 비활성화합니다. 캐시 플러시가 필요할 수 있습니다.

```bash
bin/magento dev:template-hints:disable
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:template-hints:enable`

프런트 엔드 템플릿 힌트를 활성화합니다. 캐시 플러시가 필요할 수 있습니다.

```bash
bin/magento dev:template-hints:enable
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:template-hints:status`

프런트 엔드 템플릿 힌트 상태를 표시합니다.

```bash
bin/magento dev:template-hints:status
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:tests:run`

테스트 실행

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

실행할 테스트 유형입니다. 사용 가능한 유형: 모든, 단위, 통합, 통합, 모두, 정적, 정적, 모두, 무결성, 레거시, 기본값

- 기본값: `default`


### `--arguments`, `-c`

PHPUnit에 대한 추가 인수입니다. 예: &quot;-c&#39;—filter=MyTest&#39;&quot;(공백 없음)

- 기본값: &quot;
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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:urn-catalog:generate`

IDE에 대한 URN의 카탈로그를 *.xsd 매핑하여 xml을 강조 표시합니다.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

카탈로그를 출력할 파일의 경로입니다. PhpStorm의 경우 .idea/misc.xml 를 사용합니다.

- 필수 여부

### `--ide`

카탈로그를 생성할 형식입니다. 지원됨: [pstorm, vscode]

- 기본값: `phpstorm`
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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `dev:xml:convert`

XSL 스타일 시트를 사용하여 XML 파일 변환

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```


### `xml-file`

변환할 XML 파일의 경로

- 필수 여부

### `processor`

XML 파일에 적용할 XSL 스타일 시트 경로

- 필수 여부

### `--overwrite`, `-o`

XML 파일 덮어쓰기

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `downloadable:domains:add`

다운로드 가능한 도메인 허용 목록에 도메인 추가

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

도메인 이름

- 기본값: `[]`

- 어레이

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `downloadable:domains:remove`

다운로드 가능한 도메인 허용 목록에서 도메인을 제거합니다

```bash
bin/magento downloadable:domains:remove [<domains>...]
```


### `domains`

도메인 이름

- 기본값: `[]`

- 어레이

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `downloadable:domains:show`

다운로드 가능한 도메인 허용 목록 표시

```bash
bin/magento downloadable:domains:show
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `encryption:payment-data:update`

암호화된 신용 카드 데이터를 최신 암호화 암호화로 다시 암호화합니다.

```bash
bin/magento encryption:payment-data:update
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `i18n:collect-phrases`

코드 베이스에서 구 검색

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```


### `directory`

구문 분석할 디렉터리 경로입니다. —magento 플래그가 설정된 경우에는 필요하지 않습니다.


### `--output`, `-o`

출력 파일에 대한 경로(파일 이름 포함)입니다. 파일을 지정하지 않은 경우 기본값은 stdout입니다.

- 값 필요

### `--magento`, `-m`

—magento 매개 변수를 사용하여 현재 Magento 코드 베이스를 구문 분석합니다. 디렉터리가 지정된 경우 매개 변수를 생략합니다.

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `i18n:pack`

언어 패키지 저장

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```


### `source`

번역이 있는 소스 사전 파일의 경로

- 필수 여부

### `locale`

사전에 대한 Target 로케일(예: &quot;de_DE&quot;)

- 필수 여부

### `--mode`, `-m`

사전의 저장 모드 - &quot;replace&quot; - 언어 팩을 새 언어 팩으로 바꾸기 - &quot;merge&quot; - merge 언어 패키지 기본적으로 &quot;replace&quot;

- 기본값: `replace`
- 값 필요

### `--allow-duplicates`, `-d`

변환의 중복을 저장할 수 있도록 —allow-duplications 매개 변수를 사용합니다. 그렇지 않으면 매개 변수를 생략합니다.

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `i18n:uninstall`

언어 패키지 제거

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```


### `package`

언어 패키지 이름

- 기본값: `[]`

- 필수 여부
- 어레이

### `--backup-code`, `-b`

코드 및 구성 파일 백업 수행(임시 파일 제외)

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `indexer:info`

허용되는 인덱서를 표시합니다.

```bash
bin/magento indexer:info
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `indexer:reindex`

데이터 다시 인덱스

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

모든 인덱스에 적용할 인덱스 유형 또는 생략으로 구분된 인덱스 유형 목록입니다.

- 기본값: `[]`

- 어레이

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `indexer:reset`

인덱서 상태를 유효하지 않음으로 다시 설정합니다.

```bash
bin/magento indexer:reset [<index>...]
```


### `index`

모든 인덱스에 적용할 인덱스 유형 또는 생략으로 구분된 인덱스 유형 목록입니다.

- 기본값: `[]`

- 어레이

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `indexer:set-dimensions-mode`

인덱서 Dimension 모드 설정

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

인덱서 이름 [catalog_product_price|catalog_permissions_category]


### `mode`

인덱서 차원 모드 catalog_product_price none,website,customer_group,website_and_customer_group catalog_permissions_category none,customer_group


### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `indexer:set-mode`

인덱스 모드 유형을 설정합니다.

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```


### `mode`

인덱서 모드 유형 [실시간|예약]


### `index`

모든 인덱스에 적용할 인덱스 유형 또는 생략으로 구분된 인덱스 유형 목록입니다.

- 기본값: `[]`

- 어레이

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `indexer:show-dimensions-mode`

인덱서 Dimension 모드를 표시합니다.

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

모든 인덱스에 적용할 인덱스 유형 목록(catalog_product_price,catalgpermissions_category) 또는 공백으로 구분된 인덱스 유형 목록

- 기본값: `[]`

- 어레이

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `indexer:show-mode`

인덱스 모드 표시

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

모든 인덱스에 적용할 인덱스 유형 또는 생략으로 구분된 인덱스 유형 목록입니다.

- 기본값: `[]`

- 어레이

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `indexer:status`

인덱서의 상태를 표시합니다.

```bash
bin/magento indexer:status [<index>...]
```


### `index`

모든 인덱스에 적용할 인덱스 유형 또는 생략으로 구분된 인덱스 유형 목록입니다.

- 기본값: `[]`

- 어레이

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `info:adminuri`

Magento 관리 URI를 표시합니다

```bash
bin/magento info:adminuri
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `info:backups:list`

사용 가능한 백업 파일 목록을 인쇄합니다.

```bash
bin/magento info:backups:list
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `info:currency:list`

사용 가능한 통화 목록을 표시합니다

```bash
bin/magento info:currency:list
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `info:dependencies:show-framework`

Magento 프레임워크에 대한 종속성 수를 표시합니다

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

### `--output`, `-o`

보고서 파일 이름

- 기본값: `framework-dependencies.csv`
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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `info:dependencies:show-modules`

모듈 간 종속성 수를 표시합니다.

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

### `--output`, `-o`

보고서 파일 이름

- 기본값: `modules-dependencies.csv`
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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `info:dependencies:show-modules-circular`

모듈 간 순환 종속성 수를 표시합니다.

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

### `--output`, `-o`

보고서 파일 이름

- 기본값: `modules-circular-dependencies.csv`
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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `info:language:list`

사용 가능한 언어 로케일 목록을 표시합니다

```bash
bin/magento info:language:list
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `info:timezone:list`

사용 가능한 시간대 목록을 표시합니다

```bash
bin/magento info:timezone:list
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `inventory:reservation:create-compensations`

제공된 보상 인수로 예약을 생성합니다.

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

&quot; 형식의 보상 인수 목록&lt;order_increment_id>:&lt;sku>:&lt;quantity>:&lt;stock-id>&quot;

- 기본값: `[]`

- 어레이

### `--raw`, `-r`

원시 출력

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `inventory:reservation:list-inconsistencies`

판매 가능한 수량이 일치하지 않는 모든 주문 및 제품 표시

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

### `--complete-orders`, `-c`

전체 주문에 대한 불일치만 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--incomplete-orders`, `-i`

불완전한 주문에 대한 불일치만 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--bunch-size`, `-b`

한 번에 로드되는 주문 수를 정의합니다

- 기본값: `50`
- 값을 허용합니다

### `--raw`, `-r`

원시 출력

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `inventory-geonames:import`

소스 선택 알고리즘을 위한 지역 이름 다운로드 및 가져오기

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

가져올 국가 코드 목록

- 기본값: `[]`

- 필수 여부
- 어레이

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `maintenance:allow-ips`

유지 관리 모드 제외 IP 설정

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```


### `ip`

허용된 IP 주소

- 기본값: `[]`

- 어레이

### `--none`

허용되는 IP 주소 지우기

- 기본값: `false`
- 값을 허용하지 않음

### `--add`

기존 목록에 IP 주소 추가

- 기본값: `false`
- 값을 허용하지 않음

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `maintenance:disable`

유지 관리 모드 비활성화

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

허용된 IP 주소(허용되는 IP 목록을 지우려면 &#39;없음&#39;을 사용)

- 기본값: `[]`
- 값 필요

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `maintenance:enable`

유지 관리 모드 사용

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

허용된 IP 주소(허용되는 IP 목록을 지우려면 &#39;없음&#39;을 사용)

- 기본값: `[]`
- 값 필요

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `maintenance:status`

유지 관리 모드 상태를 표시합니다.

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `media-content:sync`

컨텐츠를 자산과 동기화

```bash
bin/magento media-content:sync
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `media-gallery:sync`

데이터베이스의 미디어 저장소 및 미디어 자산 동기화

```bash
bin/magento media-gallery:sync
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `module:config:status`

&#39;app/etc/config.php&#39; 파일의 모듈 구성을 확인하고 최신 상태인지 여부를 보고합니다

```bash
bin/magento module:config:status
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `module:disable`

지정된 모듈을 사용하지 않도록 설정합니다.

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

모듈 이름

- 기본값: `[]`

- 어레이

### `--force`, `-f`

종속성 무시 확인

- 기본값: `false`
- 값을 허용하지 않음

### `--all`

모든 모듈 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--clear-static-content`, `-c`

생성된 정적 보기 파일을 지웁니다. 모듈에 정적 보기 파일이 있는 경우 필요합니다.

- 기본값: `false`
- 값을 허용하지 않음

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `module:enable`

지정된 모듈을 사용합니다

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

모듈 이름

- 기본값: `[]`

- 어레이

### `--force`, `-f`

종속성 무시 확인

- 기본값: `false`
- 값을 허용하지 않음

### `--all`

모든 모듈 사용

- 기본값: `false`
- 값을 허용하지 않음

### `--clear-static-content`, `-c`

생성된 정적 보기 파일을 지웁니다. 모듈에 정적 보기 파일이 있는 경우 필요합니다.

- 기본값: `false`
- 값을 허용하지 않음

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `module:status`

모듈 상태를 표시합니다.

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```


### `module-names`

선택적 모듈 이름

- 기본값: `[]`

- 어레이

### `--enabled`

활성화된 모듈만 인쇄

- 기본값: `false`
- 값을 허용하지 않음

### `--disabled`

비활성화된 모듈만 인쇄

- 기본값: `false`
- 값을 허용하지 않음

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `module:uninstall`

작성기가 설치한 모듈을 제거합니다.

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```


### `module`

모듈 이름

- 기본값: `[]`

- 필수 여부
- 어레이

### `--remove-data`, `-r`

모듈에서 설치한 데이터 제거

- 기본값: `false`
- 값을 허용하지 않음

### `--backup-code`

코드 및 구성 파일 백업 수행(임시 파일 제외)

- 기본값: `false`
- 값을 허용하지 않음

### `--backup-media`

미디어 백업 수행

- 기본값: `false`
- 값을 허용하지 않음

### `--backup-db`

전체 데이터베이스 백업 수행

- 기본값: `false`
- 값을 허용하지 않음

### `--non-composer`

여기에 경과되는 모든 모듈은 작성기가 아닙니다

- 기본값: `false`
- 값을 허용하지 않음

### `--clear-static-content`, `-c`

생성된 정적 보기 파일을 지웁니다. 모듈에 정적 보기 파일이 있는 경우 필요합니다.

- 기본값: `false`
- 값을 허용하지 않음

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `newrelic:create:deploy-marker`

배포 큐에서 항목을 확인하고 적절한 배포 마커를 만듭니다.

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```


### `message`

메시지를 배포하시겠습니까?

- 필수 여부

### `change_log`

변경 로그?

- 필수 여부

### `user`

배포 사용자


### `revision`

개정


### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `queue:consumers:list`

MessageQueue 소비자 목록

```bash
bin/magento queue:consumers:list
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `queue:consumers:start`

MessageQueue 소비자 시작

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```


### `consumer`

시작할 소비자의 이름입니다.

- 필수 여부

### `--max-messages`

프로세스가 종료되기 전에 소비자가 처리할 메시지 수입니다. 지정하지 않으면 큐에 있는 모든 메시지를 처리한 후 종료합니다.

- 값 필요

### `--batch-size`

일괄 처리당 메시지 수. 배치 소비자에만 적용됩니다.

- 값 필요

### `--area-code`

기본 영역(전역, 관리 등)은 기본값입니다.

- 값 필요

### `--single-thread`

이 옵션은 한 소비자의 여러 복사본을 동시에 실행할 수 없도록 합니다.

- 기본값: `false`
- 값을 허용하지 않음

### `--multi-process`

소비자당 프로세스 수.

- 값을 허용합니다

### `--pid-file-path`

PID를 저장하는 파일 경로(이 옵션은 더 이상 사용되지 않으며, 대신 —단일 스레드 사용)

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `remote-storage:sync`

미디어 파일을 원격 스토리지와 동기화합니다.

```bash
bin/magento remote-storage:sync
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `sampledata:deploy`

작성기 기반 Magento 설치를 위해 샘플 데이터 모듈 배포

```bash
bin/magento sampledata:deploy [--no-update]
```

### `--no-update`

작성기 업데이트를 실행하지 않고 composer.json 업데이트

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `sampledata:remove`

composer.json에서 모든 샘플 데이터 패키지 제거

```bash
bin/magento sampledata:remove [--no-update]
```

### `--no-update`

작성기 업데이트를 실행하지 않고 composer.json 업데이트

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `sampledata:reset`

재설치를 위해 모든 샘플 데이터 모듈 재설정

```bash
bin/magento sampledata:reset
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `security:recaptcha:disable-for-user-forgot-password`

관리자 사용자가 암호 양식을 잊어버린 경우 reCAPTCHA 비활성화

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `security:recaptcha:disable-for-user-login`

관리자 사용자 로그인 양식에 대해 reCAPTCHA 비활성화

```bash
bin/magento security:recaptcha:disable-for-user-login
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `security:tfa:google:set-secret`

Google OTP 생성에 사용된 암호를 설정합니다.

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```


### `user`

사용자 이름

- 필수 여부

### `secret`

비밀

- 필수 여부

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `security:tfa:providers`

사용 가능한 모든 공급자 나열

```bash
bin/magento security:tfa:providers
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `security:tfa:reset`

한 사용자에 대한 구성 재설정

```bash
bin/magento security:tfa:reset <user> <provider>
```


### `user`

사용자 이름

- 필수 여부

### `provider`

공급자 코드

- 필수 여부

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:backup`

Magento 응용 프로그램 코드 기본, 미디어 및 데이터베이스 백업

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code`

코드 및 구성 파일 백업 수행(임시 파일 제외)

- 기본값: `false`
- 값을 허용하지 않음

### `--media`

미디어 백업 수행

- 기본값: `false`
- 값을 허용하지 않음

### `--db`

전체 데이터베이스 백업 수행

- 기본값: `false`
- 값을 허용하지 않음

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:config:set`

배포 구성을 만들거나 수정합니다

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

백엔드 프런트 이름(누락된 경우 자동으로 생성됨)

- 값 필요

### `--enable-debug-logging`

디버그 로깅 활성화

- 값 필요

### `--enable-syslog-logging`

Syslog 로깅 활성화

- 값 필요

### `--remote-storage-driver`

원격 저장소 드라이버

- 값 필요

### `--remote-storage-prefix`

원격 저장소 접두사

- 기본값: &quot;
- 값 필요

### `--remote-storage-endpoint`

원격 저장소 끝점

- 값 필요

### `--remote-storage-bucket`

원격 저장소 버킷

- 값 필요

### `--remote-storage-region`

원격 저장소 영역

- 값 필요

### `--remote-storage-key`

원격 저장소 액세스 키

- 기본값: &quot;
- 값 필요

### `--remote-storage-secret`

원격 저장소 암호 키

- 기본값: &quot;
- 값 필요

### `--remote-storage-path-style`

원격 저장소 경로 스타일

- 기본값: `0`
- 값 필요

### `--checkout-async`

비동기 주문 처리를 활성화하시겠습니까? 1 - 예, 0 - 아니오

- 값 필요

### `--amqp-host`

Amqp 서버 호스트

- 기본값: &quot;
- 값 필요

### `--amqp-port`

Amqp 서버 포트

- 기본값: `5672`
- 값 필요

### `--amqp-user`

Amqp 서버 사용자 이름

- 기본값: &quot;
- 값 필요

### `--amqp-password`

Amqp 서버 암호

- 기본값: &quot;
- 값 필요

### `--amqp-virtualhost`

Amqp virtualhost

- 기본값: `/`
- 값 필요

### `--amqp-ssl`

Amqp SSL

- 기본값: &quot;
- 값 필요

### `--amqp-ssl-options`

Amqp SSL 옵션(JSON)

- 기본값: &quot;
- 값 필요

### `--consumers-wait-for-messages`

소비자가 큐에서 메시지를 기다려야 합니까? 1 - 예, 0 - 아니오

- 값 필요

### `--queue-default-connection`

메시지가 기본 연결을 큐에 추가합니다. &#39;db&#39;, &#39;amqp&#39; 또는 사용자 지정 큐 시스템일 수 있습니다.큐 시스템을 설치 및 구성해야 합니다. 그렇지 않으면 메시지가 제대로 처리되지 않습니다.

- 값 필요

### `--deferred-total-calculating`

지연된 합계 계산을 사용하시겠습니까? 1 - 예, 0 - 아니오

- 값 필요

### `--key`

암호화 키

- 값 필요

### `--db-host`

데이터베이스 서버 호스트

- 값 필요

### `--db-name`

데이터베이스 이름

- 값 필요

### `--db-user`

데이터베이스 서버 사용자 이름

- 값 필요

### `--db-engine`

데이터베이스 서버 엔진

- 값 필요

### `--db-password`

데이터베이스 서버 암호

- 값 필요

### `--db-prefix`

데이터베이스 테이블 접두사

- 값 필요

### `--db-model`

데이터베이스 유형

- 값 필요

### `--db-init-statements`

데이터베이스 초기 명령 집합

- 값 필요

### `--skip-db-validation`, `-s`

지정하면 db 연결 유효성 검사를 건너뜁니다

- 기본값: `false`
- 값을 허용하지 않음

### `--http-cache-hosts`

http 캐시 호스트

- 값 필요

### `--db-ssl-key`

SSL을 통해 db 연결을 설정하기 위한 클라이언트 키 파일의 전체 경로

- 기본값: &quot;
- 값 필요

### `--db-ssl-cert`

SSL을 통해 db 연결을 설정하기 위한 클라이언트 인증서 파일의 전체 경로

- 기본값: &quot;
- 값 필요

### `--db-ssl-ca`

SSL을 통해 db 연결을 설정하기 위한 서버 인증서 파일의 전체 경로

- 기본값: &quot;
- 값 필요

### `--db-ssl-verify`

서버 인증 확인

- 기본값: `false`
- 값을 허용하지 않음

### `--session-save`

세션 저장 처리기

- 값 필요

### `--session-save-redis-host`

UNIX 소켓을 사용하는 경우 정규화된 호스트 이름, IP 주소 또는 절대 경로

- 값 필요

### `--session-save-redis-port`

Redis 서버 수신 포트

- 값 필요

### `--session-save-redis-password`

Redis 서버 암호

- 값 필요

### `--session-save-redis-timeout`

연결 시간 초과(초)

- 값 필요

### `--session-save-redis-persistent-id`

영구 연결을 활성화하는 고유한 문자열

- 값 필요

### `--session-save-redis-db`

Redis 데이터베이스 번호

- 값 필요

### `--session-save-redis-compression-threshold`

Redis 압축 임계값

- 값 필요

### `--session-save-redis-compression-lib`

Redis 압축 라이브러리. 값: gzip(기본값), lzf, lz4, 일괄 적용

- 값 필요

### `--session-save-redis-log-level`

Redis 로그 수준입니다. 값: 0(최소 세부 정보) - 7(가장 자세한 정보)

- 값 필요

### `--session-save-redis-max-concurrency`

한 세션의 잠금을 기다릴 수 있는 최대 프로세스 수

- 값 필요

### `--session-save-redis-break-after-frontend`

프런트 엔드 세션에 대한 잠금을 해제하기 전에 대기하는 시간(초)

- 값 필요

### `--session-save-redis-break-after-adminhtml`

관리자 세션에 대한 잠금을 해제하기 전에 대기하는 시간(초)

- 값 필요

### `--session-save-redis-first-lifetime`

첫 번째 쓰기 시 보트가 아닌 세션에 대한 라이프타임(초)입니다(비활성화하려면 0을 사용)

- 값 필요

### `--session-save-redis-bot-first-lifetime`

첫 번째 쓰기 시 봇에 대한 세션의 수명(초)입니다(비활성화하려면 0을 사용)

- 값 필요

### `--session-save-redis-bot-lifetime`

후속 쓰기 시 봇에 대한 세션 수명(0을 사용하여 비활성화)

- 값 필요

### `--session-save-redis-disable-locking`

Redis에서 잠금이 해제됩니다. 값: false(기본값), true

- 값 필요

### `--session-save-redis-min-lifetime`

Redis 최소 세션 수명(초)

- 값 필요

### `--session-save-redis-max-lifetime`

Redis의 최대 세션 수명(초)

- 값 필요

### `--session-save-redis-sentinel-master`

레디스 센티넬 마스터

- 값 필요

### `--session-save-redis-sentinel-servers`

Redis Sentinel 서버, 쉼표로 구분됨

- 값 필요

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel이 마스터를 확인합니다. 값: false(기본값), true

- 값 필요

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel 연결 다시 시도.

- 값 필요

### `--cache-backend`

기본 캐시 처리기

- 값 필요

### `--cache-backend-redis-server`

Redis 서버

- 값 필요

### `--cache-backend-redis-db`

캐시에 대한 데이터베이스 번호

- 값 필요

### `--cache-backend-redis-port`

Redis 서버 수신 포트

- 값 필요

### `--cache-backend-redis-password`

Redis 서버 암호

- 값 필요

### `--cache-backend-redis-compress-data`

압축을 비활성화하려면 0으로 설정합니다(기본값은 1, 활성화됨).

- 값 필요

### `--cache-backend-redis-compression-lib`

사용할 압축 라이브러리 [snappy,lzf,l4z,zstd,gzip] (자동으로 결정하려면 비워 둡니다.)

- 값 필요

### `--cache-id-prefix`

캐시 키의 ID 접두사

- 값 필요

### `--allow-parallel-generation`

비차단 방식으로 캐시 생성 허용

- 기본값: `false`
- 값을 허용하지 않음

### `--page-cache`

기본 캐시 처리기

- 값 필요

### `--page-cache-redis-server`

Redis 서버

- 값 필요

### `--page-cache-redis-db`

캐시에 대한 데이터베이스 번호

- 값 필요

### `--page-cache-redis-port`

Redis 서버 수신 포트

- 값 필요

### `--page-cache-redis-password`

Redis 서버 암호

- 값 필요

### `--page-cache-redis-compress-data`

전체 페이지 캐시를 압축하려면 1로 설정합니다(비활성화하려면 0을 사용).

- 값 필요

### `--page-cache-redis-compression-lib`

사용할 압축 라이브러리 [snappy,lzf,l4z,zstd,gzip] (자동으로 결정하려면 비워 둡니다.)

- 값 필요

### `--page-cache-id-prefix`

캐시 키의 ID 접두사

- 값 필요

### `--lock-provider`

공급자 이름 잠금

- 값 필요

### `--lock-db-prefix`

잠금 충돌을 방지하기 위한 설치 특정 잠금 접두사

- 값 필요

### `--lock-zookeeper-host`

Zookeeper 클러스터에 연결할 호스트 및 포트입니다. 예: 127.0.0.1:2181

- 값 필요

### `--lock-zookeeper-path`

Zookeeper가 잠금을 저장할 경로입니다. 기본 경로는 다음과 같습니다. /magento/locks

- 값 필요

### `--lock-file-path`

파일 잠금이 저장되는 경로입니다.

- 값 필요

### `--document-root-is-pub`

표시할 플래그입니다. Pub가 루트에 있고 true 또는 false일 수 있습니다

- 값 필요

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:db-data:upgrade`

DB에서 데이터 설치 및 업그레이드

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:db-declaration:generate-patch`

패치를 생성하여 특정 폴더에 넣습니다.

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```


### `module`

모듈 이름

- 필수 여부

### `patch`

패치 이름

- 필수 여부

### `--revertable`

패치를 되돌릴 수 있는지 확인합니다.

- 기본값: `false`
- 값을 허용합니다

### `--type`

어떤 유형의 패치를 생성해야 하는지 확인합니다. 사용 가능한 값: `data`, `schema`.

- 기본값: `data`
- 값을 허용합니다

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:db-declaration:generate-whitelist`

선언 설치 관리자에서 편집할 수 있는 테이블 및 열의 허용 목록 생성

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

### `--module-name`

허용 목록이 생성될 모듈의 이름

- 기본값: `all`
- 값을 허용합니다

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:db-schema:add-slave`

체크 아웃 견적 관련 테이블을 별도의 DB 서버로 이동

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

슬레이브 DB 서버 호스트

- 기본값: `localhost`
- 값 필요

### `--dbname`

슬레이브 데이터베이스 이름

- 값 필요

### `--username`

슬레이브 DB 사용자 이름

- 기본값: `root`
- 값 필요

### `--password`

슬레이브 DB 사용자 암호

- 값을 허용합니다

### `--connection`

슬레이브 연결 이름

- 기본값: `default`
- 값을 허용합니다

### `--resource`

슬레이브 리소스 이름

- 기본값: `default`
- 값을 허용합니다

### `--maxAllowedLag`

최대 허용 지연 슬레이브 연결(초)

- 기본값: &quot;
- 값을 허용합니다

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:db-schema:split-quote`

체크 아웃 견적 관련 테이블을 별도의 DB 서버로 이동합니다. 2.4.2 이후 사용되지 않으며 제거됩니다

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

체크 아웃 DB 서버 호스트

- 값 필요

### `--dbname`

체크 아웃 데이터베이스 이름

- 값 필요

### `--username`

체크아웃 DB 사용자 이름

- 값 필요

### `--password`

체크 아웃 DB 사용자 암호

- 값을 허용합니다

### `--connection`

체크아웃 연결 이름

- 기본값: `checkout`
- 값을 허용합니다

### `--resource`

체크아웃 리소스 이름

- 기본값: `checkout`
- 값을 허용합니다

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:db-schema:split-sales`

영업 관련 테이블을 별도의 DB 서버로 이동합니다. 2.4.2 이후 사용되지 않으며 제거됩니다

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

영업 DB 서버 호스트

- 값 필요

### `--dbname`

영업 데이터베이스 이름

- 값 필요

### `--username`

영업 DB 사용자 이름

- 값 필요

### `--password`

영업 DB 사용자 암호

- 값을 허용합니다

### `--connection`

영업 연결 이름

- 기본값: `sales`
- 값을 허용합니다

### `--resource`

영업 자원 이름

- 기본값: `sales`
- 값을 허용합니다

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:db-schema:upgrade`

DB 스키마 설치 및 업그레이드

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

이전 스크립트(InstallSchema, UpgradeSchema)를 db_schema.xml 형식으로 변환할 수 있습니다

- 기본값: `false`
- 값을 허용합니다

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:db:status`

DB 스키마나 데이터에 업그레이드가 필요한지 확인

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:di:compile`

자동으로 생성할 수 있는 ID 구성과 누락된 모든 클래스를 생성합니다.

```bash
bin/magento setup:di:compile
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:install`

Magento 응용 프로그램을 설치합니다

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

백엔드 프런트 이름(누락된 경우 자동으로 생성됨)

- 값 필요

### `--enable-debug-logging`

디버그 로깅 활성화

- 값 필요

### `--enable-syslog-logging`

Syslog 로깅 활성화

- 값 필요

### `--remote-storage-driver`

원격 저장소 드라이버

- 값 필요

### `--remote-storage-prefix`

원격 저장소 접두사

- 기본값: &quot;
- 값 필요

### `--remote-storage-endpoint`

원격 저장소 끝점

- 값 필요

### `--remote-storage-bucket`

원격 저장소 버킷

- 값 필요

### `--remote-storage-region`

원격 저장소 영역

- 값 필요

### `--remote-storage-key`

원격 저장소 액세스 키

- 기본값: &quot;
- 값 필요

### `--remote-storage-secret`

원격 저장소 암호 키

- 기본값: &quot;
- 값 필요

### `--remote-storage-path-style`

원격 저장소 경로 스타일

- 기본값: `0`
- 값 필요

### `--checkout-async`

비동기 주문 처리를 활성화하시겠습니까? 1 - 예, 0 - 아니오

- 값 필요

### `--amqp-host`

Amqp 서버 호스트

- 기본값: &quot;
- 값 필요

### `--amqp-port`

Amqp 서버 포트

- 기본값: `5672`
- 값 필요

### `--amqp-user`

Amqp 서버 사용자 이름

- 기본값: &quot;
- 값 필요

### `--amqp-password`

Amqp 서버 암호

- 기본값: &quot;
- 값 필요

### `--amqp-virtualhost`

Amqp virtualhost

- 기본값: `/`
- 값 필요

### `--amqp-ssl`

Amqp SSL

- 기본값: &quot;
- 값 필요

### `--amqp-ssl-options`

Amqp SSL 옵션(JSON)

- 기본값: &quot;
- 값 필요

### `--consumers-wait-for-messages`

소비자가 큐에서 메시지를 기다려야 합니까? 1 - 예, 0 - 아니오

- 값 필요

### `--queue-default-connection`

메시지가 기본 연결을 큐에 추가합니다. &#39;db&#39;, &#39;amqp&#39; 또는 사용자 지정 큐 시스템일 수 있습니다.큐 시스템을 설치 및 구성해야 합니다. 그렇지 않으면 메시지가 제대로 처리되지 않습니다.

- 값 필요

### `--deferred-total-calculating`

지연된 합계 계산을 사용하시겠습니까? 1 - 예, 0 - 아니오

- 값 필요

### `--key`

암호화 키

- 값 필요

### `--db-host`

데이터베이스 서버 호스트

- 값 필요

### `--db-name`

데이터베이스 이름

- 값 필요

### `--db-user`

데이터베이스 서버 사용자 이름

- 값 필요

### `--db-engine`

데이터베이스 서버 엔진

- 값 필요

### `--db-password`

데이터베이스 서버 암호

- 값 필요

### `--db-prefix`

데이터베이스 테이블 접두사

- 값 필요

### `--db-model`

데이터베이스 유형

- 값 필요

### `--db-init-statements`

데이터베이스 초기 명령 집합

- 값 필요

### `--skip-db-validation`, `-s`

지정하면 db 연결 유효성 검사를 건너뜁니다

- 기본값: `false`
- 값을 허용하지 않음

### `--http-cache-hosts`

http 캐시 호스트

- 값 필요

### `--db-ssl-key`

SSL을 통해 db 연결을 설정하기 위한 클라이언트 키 파일의 전체 경로

- 기본값: &quot;
- 값 필요

### `--db-ssl-cert`

SSL을 통해 db 연결을 설정하기 위한 클라이언트 인증서 파일의 전체 경로

- 기본값: &quot;
- 값 필요

### `--db-ssl-ca`

SSL을 통해 db 연결을 설정하기 위한 서버 인증서 파일의 전체 경로

- 기본값: &quot;
- 값 필요

### `--db-ssl-verify`

서버 인증 확인

- 기본값: `false`
- 값을 허용하지 않음

### `--session-save`

세션 저장 처리기

- 값 필요

### `--session-save-redis-host`

UNIX 소켓을 사용하는 경우 정규화된 호스트 이름, IP 주소 또는 절대 경로

- 값 필요

### `--session-save-redis-port`

Redis 서버 수신 포트

- 값 필요

### `--session-save-redis-password`

Redis 서버 암호

- 값 필요

### `--session-save-redis-timeout`

연결 시간 초과(초)

- 값 필요

### `--session-save-redis-persistent-id`

영구 연결을 활성화하는 고유한 문자열

- 값 필요

### `--session-save-redis-db`

Redis 데이터베이스 번호

- 값 필요

### `--session-save-redis-compression-threshold`

Redis 압축 임계값

- 값 필요

### `--session-save-redis-compression-lib`

Redis 압축 라이브러리. 값: gzip(기본값), lzf, lz4, 일괄 적용

- 값 필요

### `--session-save-redis-log-level`

Redis 로그 수준입니다. 값: 0(최소 세부 정보) - 7(가장 자세한 정보)

- 값 필요

### `--session-save-redis-max-concurrency`

한 세션의 잠금을 기다릴 수 있는 최대 프로세스 수

- 값 필요

### `--session-save-redis-break-after-frontend`

프런트 엔드 세션에 대한 잠금을 해제하기 전에 대기하는 시간(초)

- 값 필요

### `--session-save-redis-break-after-adminhtml`

관리자 세션에 대한 잠금을 해제하기 전에 대기하는 시간(초)

- 값 필요

### `--session-save-redis-first-lifetime`

첫 번째 쓰기 시 보트가 아닌 세션에 대한 라이프타임(초)입니다(비활성화하려면 0을 사용)

- 값 필요

### `--session-save-redis-bot-first-lifetime`

첫 번째 쓰기 시 봇에 대한 세션의 수명(초)입니다(비활성화하려면 0을 사용)

- 값 필요

### `--session-save-redis-bot-lifetime`

후속 쓰기 시 봇에 대한 세션 수명(0을 사용하여 비활성화)

- 값 필요

### `--session-save-redis-disable-locking`

Redis에서 잠금이 해제됩니다. 값: false(기본값), true

- 값 필요

### `--session-save-redis-min-lifetime`

Redis 최소 세션 수명(초)

- 값 필요

### `--session-save-redis-max-lifetime`

Redis의 최대 세션 수명(초)

- 값 필요

### `--session-save-redis-sentinel-master`

레디스 센티넬 마스터

- 값 필요

### `--session-save-redis-sentinel-servers`

Redis Sentinel 서버, 쉼표로 구분됨

- 값 필요

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel이 마스터를 확인합니다. 값: false(기본값), true

- 값 필요

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel 연결 다시 시도.

- 값 필요

### `--cache-backend`

기본 캐시 처리기

- 값 필요

### `--cache-backend-redis-server`

Redis 서버

- 값 필요

### `--cache-backend-redis-db`

캐시에 대한 데이터베이스 번호

- 값 필요

### `--cache-backend-redis-port`

Redis 서버 수신 포트

- 값 필요

### `--cache-backend-redis-password`

Redis 서버 암호

- 값 필요

### `--cache-backend-redis-compress-data`

압축을 비활성화하려면 0으로 설정합니다(기본값은 1, 활성화됨).

- 값 필요

### `--cache-backend-redis-compression-lib`

사용할 압축 라이브러리 [snappy,lzf,l4z,zstd,gzip] (자동으로 결정하려면 비워 둡니다.)

- 값 필요

### `--cache-id-prefix`

캐시 키의 ID 접두사

- 값 필요

### `--allow-parallel-generation`

비차단 방식으로 캐시 생성 허용

- 기본값: `false`
- 값을 허용하지 않음

### `--page-cache`

기본 캐시 처리기

- 값 필요

### `--page-cache-redis-server`

Redis 서버

- 값 필요

### `--page-cache-redis-db`

캐시에 대한 데이터베이스 번호

- 값 필요

### `--page-cache-redis-port`

Redis 서버 수신 포트

- 값 필요

### `--page-cache-redis-password`

Redis 서버 암호

- 값 필요

### `--page-cache-redis-compress-data`

전체 페이지 캐시를 압축하려면 1로 설정합니다(비활성화하려면 0을 사용).

- 값 필요

### `--page-cache-redis-compression-lib`

사용할 압축 라이브러리 [snappy,lzf,l4z,zstd,gzip] (자동으로 결정하려면 비워 둡니다.)

- 값 필요

### `--page-cache-id-prefix`

캐시 키의 ID 접두사

- 값 필요

### `--lock-provider`

공급자 이름 잠금

- 값 필요

### `--lock-db-prefix`

잠금 충돌을 방지하기 위한 설치 특정 잠금 접두사

- 값 필요

### `--lock-zookeeper-host`

Zookeeper 클러스터에 연결할 호스트 및 포트입니다. 예: 127.0.0.1:2181

- 값 필요

### `--lock-zookeeper-path`

Zookeeper가 잠금을 저장할 경로입니다. 기본 경로는 다음과 같습니다. /magento/locks

- 값 필요

### `--lock-file-path`

파일 잠금이 저장되는 경로입니다.

- 값 필요

### `--document-root-is-pub`

표시할 플래그입니다. Pub가 루트에 있고 true 또는 false일 수 있습니다

- 값 필요

### `--base-url`

게에서 사용할 수 있는 URL입니다. 사용되지 않음, config:set with path web/unsecure/base_url

- 값 필요

### `--language`

기본 언어 코드입니다. 사용되지 않음, config:set with path general/locale/code 를 사용하십시오.

- 값 필요

### `--timezone`

기본 시간대 코드입니다. 사용되지 않음, config:set with path general/locale/timezone 을 사용하십시오.

- 값 필요

### `--currency`

기본 통화 코드. 사용되지 않음, 구성:set with path currency/options/base, currency/options/default 및 currency/options/allow

- 값 필요

### `--use-rewrites`

rewrites를 사용합니다. 사용되지 않음, config:set with path web/seo/use_rewrites를 사용합니다.

- 값 필요

### `--use-secure`

보안 URL을 사용합니다. SSL을 사용할 수 있는 경우에만 이 옵션을 활성화합니다. 사용되지 않음, config:set with path web/secure/use_in_frontend 를 사용합니다.

- 값 필요

### `--base-url-secure`

SSL 연결을 위한 기본 URL. 사용되지 않음, config:set with path web/secure/base_url 을 사용하십시오.

- 값 필요

### `--use-secure-admin`

SSL을 사용하여 관리자 인터페이스를 실행합니다. 사용되지 않음, config:set with path web/secure/use_in_adminhtml 을 사용합니다.

- 값 필요

### `--admin-use-security-key`

Magento 관리 URL 및 양식에서 &quot;보안 키&quot; 기능을 사용할지 여부를 결정합니다. 사용되지 않음, config:set with path admin/security/use_form_key 사용

- 값 필요

### `--admin-user`

관리자 사용자

- 값을 허용합니다

### `--admin-password`

관리자 암호

- 값을 허용합니다

### `--admin-email`

관리 이메일

- 값을 허용합니다

### `--admin-firstname`

관리자 이름

- 값을 허용합니다

### `--admin-lastname`

관리자 성

- 값을 허용합니다

### `--search-engine`

검색 엔진. 값: elasticsearch5, elasticsearch6, elasticsearch7

- 값 필요

### `--elasticsearch-host`

Elasticsearch 서버 호스트.

- 값 필요

### `--elasticsearch-port`

Elasticsearch 서버 포트.

- 값 필요

### `--elasticsearch-enable-auth`

인증을 활성화하려면 1로 설정하십시오. (기본값은 0, 비활성화됨)

- 값 필요

### `--elasticsearch-username`

Elasticsearch 사용자 이름. HTTP 인증이 활성화된 경우에만 적용 가능

- 값 필요

### `--elasticsearch-password`

Elasticsearch 암호. HTTP 인증이 활성화된 경우에만 적용 가능

- 값 필요

### `--elasticsearch-index-prefix`

Elasticsearch 인덱스 접두사입니다.

- 값 필요

### `--elasticsearch-timeout`

Elasticsearch 서버 시간 제한.

- 값 필요

### `--cleanup-database`

설치하기 전에 데이터베이스 정리

- 기본값: `false`
- 값을 허용하지 않음

### `--sales-order-increment-prefix`

판매 주문 번호 접두사

- 값 필요

### `--use-sample-data`

샘플 데이터 사용

- 기본값: `false`
- 값을 허용하지 않음

### `--enable-modules`

쉼표로 구분된 모듈 이름 목록입니다. 설치 중에 포함해야 합니다. 사용 가능한 매직 매개 변수 &quot;all&quot;.

- 값을 허용합니다

### `--disable-modules`

쉼표로 구분된 모듈 이름 목록입니다. 설치하는 동안 사용하지 않아야 합니다. 사용 가능한 매직 매개 변수 &quot;all&quot;.

- 값을 허용합니다

### `--convert-old-scripts`

이전 스크립트(InstallSchema, UpgradeSchema)를 db_schema.xml 형식으로 변환할 수 있습니다

- 기본값: `false`
- 값을 허용합니다

### `--interactive`, `-i`

대화형 Magento 설치

- 기본값: `false`
- 값을 허용하지 않음

### `--safe-mode`

열 제거와 같은 파괴적인 작업에 대한 덤프를 사용하여 안전하게 Magento 설치

- 값을 허용합니다

### `--data-restore`

덤프에서 제거된 데이터 복원

- 값을 허용합니다

### `--dry-run`

Magento 설치은 연습 실행 모드에서 실행됩니다

- 기본값: `false`
- 값을 허용합니다

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:performance:generate-fixtures`

고정장치 생성

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```


### `profile`

프로필 구성 파일의 경로

- 필수 여부

### `--skip-reindex`, `-s`

다시 인덱스 건너뛰기

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:rollback`

Magento 응용 프로그램 코드베이스, 미디어 및 데이터베이스를 롤백합니다

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code-file`, `-c`

var/backups에 있는 코드 백업 파일의 기본 이름

- 값 필요

### `--media-file`, `-m`

var/backups의 미디어 백업 파일 기본 이름

- 값 필요

### `--db-file`, `-d`

var/backups에 있는 db 백업 파일의 기본 이름

- 값 필요

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:static-content:deploy`

정적 보기 파일 배포

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```


### `languages`

정적 보기 파일을 출력할 ISO-639 언어 코드의 공백으로 구분된 목록입니다.

- 기본값: `[]`

- 어레이

### `--force`, `-f`

모든 모드로 파일을 배포합니다.

- 기본값: `false`
- 값을 허용하지 않음

### `--strategy`, `-s`

지정된 전략을 사용하여 파일을 배포합니다.

- 기본값: `quick`
- 값을 허용합니다

### `--area`, `-a`

지정된 영역에 대해서만 파일을 생성합니다.

- 기본값: `all`
- 여러 값을 허용합니다

### `--exclude-area`

지정된 영역에 대한 파일을 생성하지 마십시오.

- 기본값: `none`
- 여러 값을 허용합니다

### `--theme`, `-t`

지정된 테마에 대해서만 정적 보기 파일을 생성합니다.

- 기본값: `all`
- 여러 값을 허용합니다

### `--exclude-theme`

지정된 테마에 대한 파일을 생성하지 마십시오.

- 기본값: `none`
- 여러 값을 허용합니다

### `--language`, `-l`

지정된 언어에 대해서만 파일을 생성합니다.

- 기본값: `all`
- 여러 값을 허용합니다

### `--exclude-language`

지정한 언어에 대한 파일을 생성하지 마십시오.

- 기본값: `none`
- 여러 값을 허용합니다

### `--jobs`, `-j`

지정된 작업 수를 사용하여 병렬 처리를 활성화합니다.

- 기본값: `0`
- 값을 허용합니다

### `--max-execution-time`

배포 정적 프로세스의 최대 예상 실행 시간(초)입니다.

- 기본값: `900`
- 값을 허용합니다

### `--symlink-locale`

배포용으로 전달되지만 사용자 지정 사항이 없는 해당 로케일 파일의 symlink를 만듭니다.

- 기본값: `false`
- 값을 허용하지 않음

### `--content-version`

정적 콘텐츠 사용자 지정 버전은 정적 콘텐츠 버전이 동일하고 캐싱이 제대로 작동하는지 확인하기 위해 여러 노드에서 배포를 실행하는 경우 사용할 수 있습니다.

- 값 필요

### `--refresh-content-version-only`

정적 콘텐츠 버전을 새로 고치는 것은 브라우저 캐시 및 CDN 캐시에서 정적 콘텐츠를 새로 고치는 데만 사용할 수 있습니다.

- 기본값: `false`
- 값을 허용하지 않음

### `--no-javascript`

JavaScript 파일을 배포하지 마십시오.

- 기본값: `false`
- 값을 허용하지 않음

### `--no-js-bundle`

JavaScript 번들 파일을 배포하지 마십시오.

- 기본값: `false`
- 값을 허용하지 않음

### `--no-css`

CSS 파일을 배포하지 마십시오.

- 기본값: `false`
- 값을 허용하지 않음

### `--no-less`

LESS 파일을 배포하지 마십시오.

- 기본값: `false`
- 값을 허용하지 않음

### `--no-images`

이미지를 배포하지 마십시오.

- 기본값: `false`
- 값을 허용하지 않음

### `--no-fonts`

글꼴 파일을 배포하지 마십시오.

- 기본값: `false`
- 값을 허용하지 않음

### `--no-html`

HTML 파일을 배포하지 마십시오.

- 기본값: `false`
- 값을 허용하지 않음

### `--no-misc`

다른 유형의 파일(.md, .jbf, .csv 등)은 배포하지 마십시오.

- 기본값: `false`
- 값을 허용하지 않음

### `--no-html-minify`

HTML 파일을 축소하지 마십시오.

- 기본값: `false`
- 값을 허용하지 않음

### `--no-parent`

상위 테마를 컴파일하지 마십시오. 빠른 표준 전략에서만 지원됩니다.

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:store-config:set`

저장소 구성을 설치합니다. 2.2.0 이후 더 이상 사용되지 않습니다. 대신 config:set 을 사용하십시오

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--base-url`

게에서 사용할 수 있는 URL입니다. 사용되지 않음, config:set with path web/unsecure/base_url

- 값 필요

### `--language`

기본 언어 코드입니다. 사용되지 않음, config:set with path general/locale/code 를 사용하십시오.

- 값 필요

### `--timezone`

기본 시간대 코드입니다. 사용되지 않음, config:set with path general/locale/timezone 을 사용하십시오.

- 값 필요

### `--currency`

기본 통화 코드. 사용되지 않음, 구성:set with path currency/options/base, currency/options/default 및 currency/options/allow

- 값 필요

### `--use-rewrites`

rewrites를 사용합니다. 사용되지 않음, config:set with path web/seo/use_rewrites를 사용합니다.

- 값 필요

### `--use-secure`

보안 URL을 사용합니다. SSL을 사용할 수 있는 경우에만 이 옵션을 활성화합니다. 사용되지 않음, config:set with path web/secure/use_in_frontend 를 사용합니다.

- 값 필요

### `--base-url-secure`

SSL 연결을 위한 기본 URL. 사용되지 않음, config:set with path web/secure/base_url 을 사용하십시오.

- 값 필요

### `--use-secure-admin`

SSL을 사용하여 관리자 인터페이스를 실행합니다. 사용되지 않음, config:set with path web/secure/use_in_adminhtml 을 사용합니다.

- 값 필요

### `--admin-use-security-key`

Magento 관리 URL 및 양식에서 &quot;보안 키&quot; 기능을 사용할지 여부를 결정합니다. 사용되지 않음, config:set with path admin/security/use_form_key 사용

- 값 필요

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:uninstall`

Magento 응용 프로그램을 제거

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `setup:upgrade`

Magento 애플리케이션, DB 데이터 및 스키마를 업그레이드합니다

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--keep-generated`

생성된 파일이 삭제되지 않도록 합니다. 프로덕션에 배포할 때를 제외하고는 이 옵션을 사용하지 않습니다. 자세한 내용은 시스템 통합자 또는 관리자에게 문의하십시오.

- 기본값: `false`
- 값을 허용하지 않음

### `--convert-old-scripts`

이전 스크립트(InstallSchema, UpgradeSchema)를 db_schema.xml 형식으로 변환할 수 있습니다

- 기본값: `false`
- 값을 허용합니다

### `--safe-mode`

열 제거와 같은 파괴적인 작업에 대한 덤프를 사용하여 안전하게 Magento 설치

- 값을 허용합니다

### `--data-restore`

덤프에서 제거된 데이터 복원

- 값을 허용합니다

### `--dry-run`

Magento 설치은 연습 실행 모드에서 실행됩니다

- 기본값: `false`
- 값을 허용합니다

### `--magento-init-params`

명령에 추가하여 Magento 초기화 매개변수를 사용자 정의합니다. 예: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[기본][path]= /var/www/example.com&amp;MAGE_DIRS[캐시][path]=/var/tmp/cache&quot;

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `store:list`

저장소 목록을 표시합니다

```bash
bin/magento store:list
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `store:website:list`

웹 사이트 목록을 표시합니다

```bash
bin/magento store:website:list
```

### `--help`, `-h`

이 도움말 메시지 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--quiet`, `-q`

메시지를 출력하지 않음

- 기본값: `false`
- 값을 허용하지 않음

### `--verbose`, `-v|-vv|-vvv`

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `support:backup:code`

코드 백업 만들기

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

### `--name`

덤프 이름

- 값을 허용합니다

### `--output`, `-o`

출력 경로

- 값을 허용합니다

### `--logs`, `-l`

로그 포함

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `support:backup:db`

DB 백업 만들기

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

### `--name`

덤프 이름

- 값을 허용합니다

### `--output`, `-o`

출력 경로

- 값을 허용합니다

### `--logs`, `-l`

로그 포함

- 기본값: `false`
- 값을 허용하지 않음

### `--ignore-sanitize`, `-i`

기밀 정보 가리기 무시

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `support:utility:check`

필요한 백업 유틸리티 확인

```bash
bin/magento support:utility:check [--hide-paths]
```

### `--hide-paths`

필요한 콘솔 유틸리티만 확인

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `support:utility:paths`

유틸리티 경로 만들기 목록

```bash
bin/magento support:utility:paths [-f|--force]
```

### `--force`, `-f`

강제

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `theme:uninstall`

테마 제거

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```


### `theme`

테마의 경로입니다. 테마 경로는 영역/공급업체/이름인 전체 경로로 지정해야 합니다. 예를 들어, 전면/Magento/공백

- 기본값: `[]`

- 필수 여부
- 어레이

### `--backup-code`

코드 백업 수행(임시 파일 제외)

- 기본값: `false`
- 값을 허용하지 않음

### `--clear-static-content`, `-c`

생성된 정적 보기 파일을 지웁니다.

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음


## `varnish:vcl:generate`

Varnish VCL을 생성하여 명령줄에 반사

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

### `--access-list`

Varnish를 제거할 수 있는 IP 액세스 목록

- 기본값: `localhost`
- 값 필요

### `--backend-host`

웹 백엔드의 호스트

- 기본값: `localhost`
- 값 필요

### `--backend-port`

웹 백엔드의 포트

- 기본값: `8080`
- 값 필요

### `--export-version`

Varnish 파일 버전

- 기본값: `4`
- 값 필요

### `--grace-period`

유예 기간(초)

- 기본값: `300`
- 값 필요

### `--output-file`

vcl을 쓸 파일의 경로

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

메시지 세부 정보 증가: 일반 출력의 경우 1, 자세한 출력의 경우 2, 디버용 3

- 기본값: `false`
- 값을 허용하지 않음

### `--version`, `-V`

이 응용 프로그램 버전 표시

- 기본값: `false`
- 값을 허용하지 않음

### `--ansi`

ANSI 출력 강제 적용

- 기본값: `false`
- 값을 허용하지 않음

### `--no-ansi`

ANSI 출력 사용 안 함

- 기본값: `false`
- 값을 허용하지 않음

### `--no-interaction`, `-n`

대화형 질문 없음

- 기본값: `false`
- 값을 허용하지 않음
