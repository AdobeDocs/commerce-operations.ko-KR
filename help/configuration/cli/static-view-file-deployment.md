---
title: 정적 보기 파일 배포
description: 프로덕션 모드 중에 상거래 파일 시스템에 정적 파일을 쓰는 방법을 알아봅니다.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 0%

---


# 정적 보기 파일 배포

{{file-system-owner}}

정적 보기 파일 배포 명령을 사용하여 작성할 수 있습니다 [정적 파일](https://glossary.magento.com/static-files) 전자 상거래 소프트웨어가 [프로덕션 모드](../bootstrap/application-modes.md#production-mode).

용어 _정적 보기 파일_ 는 다음을 나타냅니다.

- &quot;정적&quot;은 사이트에 대해 캐시할 수 있음을 의미합니다. 즉, 파일이 동적으로 생성되지 않습니다. 예로는 LESS에서 생성된 이미지 및 CSS가 있습니다.
- &quot;보기&quot;는 프레젠테이션 계층(MVC에서)을 나타냅니다.

정적 보기 파일은 `<magento_root>/pub/static` 디렉토리이고 일부는 `<magento_root>/var/view_preprocessed` 디렉터리도 있습니다.

정적 보기 파일 배포는 다음과 같이 애플리케이션 모드의 영향을 받습니다.

- [기본값](../bootstrap/application-modes.md#default-mode) 및 [개발자](../bootstrap/application-modes.md#developer-mode) 모드: Commerce는 요청 시 이러한 파일을 생성하지만, 나머지 파일은 액세스 속도를 위해 파일에 캐시됩니다.
- [프로덕션](../bootstrap/application-modes.md#production-mode) 모드: 정적 파일은 _not_ 생성되었거나 캐시되었습니다.

이 항목에서 설명한 명령을 사용하여 정적 보기 파일을 상거래 파일 시스템에 수동으로 작성해야 합니다. 이후 취약점을 제한하고 파일의 우발적 또는 악의적인 덮어쓰기를 방지하기 위해 권한을 제한할 수 있습니다.

>[!WARNING]
>
>_개발자 모드만_: 새 모듈을 설치하거나 활성화하면 새 JavaScript, CSS, 레이아웃 등이 로드될 수 있습니다. 정적 파일에 문제가 발생하지 않도록 하려면 이전 파일을 정리하여 새 모듈에 대한 모든 변경 사항을 가져오는지 확인해야 합니다. 생성된 정적 보기 파일을 여러 가지 방법으로 정리할 수 있습니다. 을(를) 참조하십시오. [자세한 내용은 정적 파일 캐시 항목 정리](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/cache_for_frontdevs.html#clean_static_cache) 추가 정보.

**정적 보기 파일을 배포하려면**:

1. Commerce 서버에 또는으로 로그인합니다 [파일 시스템 소유자에게 전환](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 다음 내용의 내용을 삭제합니다. `<magento_root>/pub/static`를 제외하고 `.htaccess` 파일. 이 파일을 삭제하지 마십시오.
1. 정적 보기 파일 배포 도구 실행 `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >관리자에서 정적 보기 파일 병합을 사용하는 경우 `pub/static` 디렉터리 시스템에 쓸 수 있어야 합니다.

   명령 옵션:

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

다음 표에서는 이 명령의 매개 변수와 값에 대해 설명합니다.

| 옵션 | 설명 | 필수? |
| ------ | ----------- | --------- |
| `<languages>` | 공백으로 구분된 [ISO-639](http://www.loc.gov/standards/iso639-2/php/code_list.php) 정적 보기 파일을 출력할 언어 코드입니다. 기본값은 입니다. `en_US`)<br>다음을 실행하여 목록을 찾습니다. `bin/magento info:language:list` | 아니요 |
| `--language (-l)` | 지정된 언어에 대해서만 파일을 생성합니다. 옵션이 지정되지 않은 기본값은 모든 ISO-639 언어 코드에 대한 파일을 생성하는 것입니다. 한 번에 하나의 언어 코드 이름을 지정할 수 있습니다. 기본값은 입니다. **모두**.<br>For example: `--language en_US --language es_ES` | 아니요 |
| `--exclude-language` | 지정된 언어 코드의 파일을 생성합니다. 옵션이 지정되지 않은 기본값은 아무 것도 제외하는 것입니다. 하나의 언어 코드 또는 쉼표로 구분된 언어 코드 목록을 지정할 수 있습니다. 기본값은 입니다. **없음**. | 아니요 |
| `--theme <theme>` | 정적 콘텐츠를 배포할 헤미입니다. 기본값은 입니다. **모두**.<br>예: `--theme Magento/blank --theme Magento/luma` | 아니요 |
| `--exclude-theme <theme>` | 정적 콘텐츠를 배포할 때 제외할 테마. 기본값은 입니다. **없음**.<br>For example, `--exclude-theme Magento/blank` | 아니요 |
| `--area (-a)` | 지정된 영역에 대해서만 파일을 생성합니다. 옵션이 지정되지 않은 기본값은 모든 영역에 대한 파일을 생성하는 것입니다. 유효한 값은 `adminhtml` 및 `frontend`. 기본값은 입니다. **모두**.<br>예: `--area adminhtml` | 아니요 |
| `--exclude-area` | 지정된 영역에 대한 파일을 생성하지 마십시오. 옵션이 지정되지 않은 기본값은 아무 것도 제외하는 것입니다. 기본값은 입니다. **없음**. | 아니요 |
| `--jobs (-j)` | 지정된 작업 수를 사용하여 병렬 처리를 활성화합니다. 기본값은 0입니다(병렬 프로세스에서 실행되지 않음). 기본값은 입니다. **0**. | 아니요 |
| `--symlink-locale` | 배포용으로 전달되지만 사용자 지정 사항이 없는 해당 로케일 파일의 symlink를 만듭니다. | 아니요 |
| `--content-version=CONTENT-VERSION` | 정적 콘텐츠 사용자 지정 버전은 정적 콘텐츠 버전이 동일하고 캐싱이 제대로 작동하는지 확인하기 위해 여러 노드에서 배포를 실행하는 경우 사용할 수 있습니다. | 아니요 |
| `--no-javascript` | JavaScript 파일을 배포하지 않음 | 아니요 |
| `--no-css` | CSS 파일을 배포하지 마십시오. | 아니요 |
| `--no-less` | LESS 파일을 배포하지 마십시오. | 아니요 |
| `--no-images` | 이미지를 배포하지 마십시오. | 아니요 |
| `--no-fonts` | 글꼴 파일을 배포하지 마십시오. | 아니요 |
| `--no-html` | HTML 파일을 배포하지 마십시오. | 아니요 |
| `--no-misc` | 다른 유형의 파일을 배포하지 마십시오: MD, JBF, CSV, JSON, TXT, HTC, SWF | 아니요 |
| `--no-html-minify` | HTML 파일을 축소하지 마십시오. | 아니요 |
| `-s <quick\|standard\|compact>` | 배포 전략을 정의합니다. 둘 이상의 로컬이 있는 경우에만 이러한 옵션을 사용하십시오.<ul><li>를 사용하십시오 [빠른 전략](static-view-file-strategy.md#quick-strategy) 배포 시간을 최소화하려면 다음을 수행하십시오. 지정하지 않은 경우 기본 명령 옵션입니다.</li><li>를 사용하십시오 [표준 전략](static-view-file-strategy.md#standard-strategy) 를 눌러 모든 패키지에 대해 모든 정적 보기 파일을 배포합니다.</li><li>를 사용하십시오 [콤팩트한 전략](static-view-file-strategy.md#compact-strategy) 서버의 디스크 공간을 절약합니다.</li></ul> | 아니요 |
| `--no-parent` | 현재 테마의 상위 테마에 대한 파일을 생성하지 마십시오. 배포하려는 현재 테마의 상위 테마를 명시적으로 사용하지 않는 경우에는 이 플래그를 사용하는 것이 좋습니다. 이렇게 하면 프로세스의 속도가 크게 향상됩니다. 이 플래그는 Commerce 2.4.2에서 사용할 수 있습니다 | 아니요 |
| `--force (-f)` | 모든 모드로 파일을 배포합니다. 기본적으로 정적 콘텐츠 배포 도구는 프로덕션 모드에서만 실행할 수 있습니다. 이 옵션을 사용하여 기본 또는 개발자 모드로 실행합니다. | 아니요 |

>[!INFO]
>
>두 값을 모두 지정하는 경우 `<languages>` 및 `--language`, `<languages>` 가 우선합니다.

## 예

다음은 몇 가지 명령 예입니다.

### 테마 및 HTML 축소 제외

다음 명령은 미국 영어(`en_US`) 언어에서는 Commerce와 함께 제공되는 Luma 테마를 제외하며 HTML 파일을 축소하지 않습니다.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

샘플 출력:

```terminal
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/backend
=== frontend -> Magento/blank -> en_US ===
=== adminhtml -> Magento/backend -> en_US ===
...........................................................
... more ...
Successful: 2055 files; errors: 0
---

New version of deployed files: 1466710645
............
Successful: 1993 files; errors: 0
---
```

다음 명령은 표준 배포 전략과 함께 4개의 작업이 있는 JavaScript만 배포합니다.

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

다음 명령은 3개의 작업이 있는 CSS 및 LESS만 배포하고 빠른 배포 전략입니다.

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### 하나의 테마 및 하나의 영역에 대한 정적 보기 파일 생성

다음 명령은 글꼴을 생성하지 않고 모든 언어, 프론트엔드 영역만, 상거래 Luma 테마에 대해서만 정적 보기 파일을 생성합니다.

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

샘플 출력:

```terminal
Requested languages: en_US
Requested areas: frontend
Requested themes: Magento/luma
=== frontend -> Magento/luma -> en_US ===
...........................................................
... more ...
........................................................................
Successful: 2092 files; errors: 0
---

New version of deployed files: 1466711110
```

## Commerce를 설치하지 않고 정적 보기 파일 배포

중요한 프로덕션 시스템에서 빌드 프로세스를 방지하기 위해 별도의 비프로덕션 환경에서 배포 프로세스를 실행할 수 있습니다.

이렇게 하려면 다음 단계를 수행합니다.

1. 실행 [`bin/magento app:config:dump`](../cli/export-configuration.md) 를 입력하여 프로덕션 시스템에서 구성을 내보냅니다.
1. 내보낸 파일을 비프로덕션 코드 베이스에 복사합니다.
1. 정적 보기 파일 배포: `bin/magento setup:static-content:deploy`

## 정적 보기 파일 배포 도구 문제 해결

[먼저 상거래 소프트웨어를 설치합니다](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html); 그렇지 않으면 정적 보기 파일 배포 도구를 실행할 수 없습니다.

**증상**: 정적 보기 파일 배포 도구를 실행하면 다음 오류가 표시됩니다.

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**솔루션**:

다음 단계를 사용하십시오.

1. 를 사용하여 상거래 소프트웨어 설치 [명령줄](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli.html).
1. Commerce 서버에 또는으로 로그인합니다 [다음으로 전환](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html): 파일 시스템 소유자입니다.
1. 다음 내용의 내용을 삭제합니다. `<magento_root>/pub/static` 디렉토리(단, `.htaccess` 파일. 이 파일을 삭제하지 마십시오.
1. 정적 보기 파일 배포: `bin/magento setup:static-content:deploy`

## 정적 콘텐츠 배포 도구 사용자 지정을 위한 개발자용 팁

정적 콘텐츠 배포 도구의 사용자 지정 구현을 만들 때는 클라이언트에서 사용할 수 있어야 하는 파일에 대해 원자적 파일 작성만 사용하십시오. 원자적이지 않은 파일 쓰기를 사용하는 경우 해당 파일이 부분 컨텐츠가 있는 클라이언트에 로드될 수 있습니다.

이를 원자성으로 만드는 옵션 중 하나는 임시 디렉토리에 저장된 파일에 쓰고 쓰기 작업을 마친 후 대상 디렉토리(클라이언트에서 클라이언트로 로드됨)로 복사하거나 이동하는 것입니다. 파일에 쓰는 방법에 대한 자세한 내용은 [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
