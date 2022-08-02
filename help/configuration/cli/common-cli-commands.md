---
title: 일반적인 명령
description: 일반적인 Commerce CLI 명령 및 사용 샘플링을 봅니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---


# 일반적인 명령

다음은 사용 가능한 명령 중 일부를 요약한 것입니다.

**전체 명령 목록을 표시하려면**:

```bash
bin/magento list
```

예제 도움말 명령:

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

명령은 요약 양식으로만 표시됩니다. 명령에 대한 자세한 내용을 보려면 명령 열의 링크를 클릭합니다.

| 명령 | 설명 |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | 캐시 관리 |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | 인덱서 관리 |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | 전자 상거래 충돌 작업 실행 |
| [`magento setup:di:compile`](../cli/code-compiler.md) | 존재하지 않는 모든 프록시 및 공장을 컴파일합니다. 그리고 하나의 스토어 및 웹 사이트에 대한 클래스 정의, 상속 정보 및 플러그인 정의를 미리 컴파일합니다. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | 모듈 종속성, 순환 종속성 및 상거래 프레임워크 종속성. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | 번역 사전 또는 번역 패키지를 만듭니다 |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | 정적 보기 파일 배포 |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | LESS에서 CSS 만들기 |
| [`magento dev:tests:run`](../cli/unit-tests.md) | 자동화된 테스트 실행 |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | 레이아웃 XML 파일을 업데이트하여 새로운 XSLT(Extensible Stylesheet Language Transformations) 스타일시트와 일치합니다 |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | 성능 테스트에 사용할 데이터를 생성합니다. |
| [`magento sampledata:install`](https://devdocs.magento.com/guides/v2.4/install-gde/install/sample-data.html) | Commerce 응용 프로그램을 설치한 후 선택적 샘플 데이터를 설치합니다.<br><br>샘플 데이터에 대한 자세한 내용은 [선택적 샘플 데이터](https://devdocs.magento.com/guides/v2.4/install-gde/install/sample-data.html). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | 백엔드 구성 관리 |
| [`magento admin:user:{create/unlock}`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-admin.html) | 관리자 사용자를 생성/편집/잠금 해제합니다. |
| [`magento dev:template-hints:{enable/disable}`](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/debug-theme.html) | 개발자 템플릿 힌트를 활성화/비활성화합니다. |

## 일반적인 인수

다음 인수는 모든 명령에 공통입니다. 이러한 명령은 상거래 소프트웨어가 설치되기 전이나 후에 실행할 수 있습니다.

| 긴 버전 | 짧은 버전 | 의미 |
|--- |--- |--- |
| `--help` | `-h` | 명령에 대한 도움말을 가져옵니다. 예, `./magento help setup:install` 또는 `./magento help setup:config:set`. |
| `--quiet` | `-q` | 자동 모드; 출력이 없습니다. |
| `--no-interaction` | `-n` | 대화형 질문 없음. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 자세한 정도. 예, `--verbose=3` 또는 `-vvv` 가장 자세한 출력인 디버그 세부 정보를 표시합니다. 기본값은 입니다. `--verbose=1` 또는 `-v`. |
| `--version` | `-V` | 이 응용 프로그램 버전 표시 |
| `--ansi` | n/a | ANSI 출력 강제 적용 |
| `--no-ansi` | n/a | ANSI 출력 사용 안 함 |
