---
title: 일반 명령
description: 일반적인 Adobe Commerce CLI 명령과 사용 예제에 대해 알아봅니다. 개발 및 관리를 위한 필수 명령줄 도구를 살펴봅니다.
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# 일반 명령

다음은 사용 가능한 몇 가지 명령을 요약한 것입니다.

**전체 명령 목록을 표시하려면**:

```bash
bin/magento list
```

도움말 명령 예:

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

명령은 요약 양식으로만 표시됩니다. 명령에 대한 자세한 내용을 보려면 명령 열의 링크를 클릭하십시오.

| 명령 | 설명 |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | 캐시 관리 |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | 인덱서 관리 |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Commerce cron job 실행 |
| [`magento setup:di:compile`](../cli/code-compiler.md) | 존재하지 않는 모든 프록시와 공장을 컴파일하고, 하나의 스토어와 웹 사이트에 대한 클래스 정의, 상속 정보 및 플러그인 정의를 미리 컴파일합니다. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | 모듈 종속성, 순환 종속성 및 Commerce 프레임워크 종속성. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | 번역 사전 또는 번역 패키지 만들기 |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | 정적 보기 파일 배포 |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | LESS에서 CSS 만들기 |
| [`magento dev:tests:run`](../cli/unit-tests.md) | 자동화된 테스트 실행 |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | 새로운 XSLT(Extensible Stylesheet Language Transformations) 스타일시트와 일치하도록 레이아웃 XML 파일 업데이트 |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | 성능 테스트에 사용할 데이터를 생성합니다. |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Commerce 애플리케이션을 설치한 후 선택적 샘플 데이터를 설치합니다.<br><br>샘플 데이터에 대한 자세한 내용은 [선택적 샘플 데이터](../../installation/sample-data/overview.md)를 참조하십시오. |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | 백엔드 구성 관리 |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | 관리자 사용자를 생성/편집/잠금 해제합니다. |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | 개발자 템플릿 힌트를 활성화/비활성화합니다. |

## 일반 인수

다음 인수는 [모든 명령](/help/tools/reference/commerce-on-premises.md)에 공통됩니다. 이러한 명령은 Commerce 소프트웨어를 설치하기 전이나 설치한 후에 실행할 수 있습니다.

| 긴 버전 | 짧은 버전 | 의미 |
|--- |--- |--- |
| `--help` | `-h` | 모든 명령에 대한 도움말을 봅니다. 예: `./magento help setup:install` 또는 `./magento help setup:config:set`. |
| `--quiet` | `-q` | 자동 모드, 출력 없음. |
| `--no-interaction` | `-n` | 대화형 질문 없음. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 세부 정보 수준입니다. 예를 들어 `--verbose=3` 또는 `-vvv`은(는) 가장 자세한 출력인 디버그 자세한 정보를 표시합니다. 기본값은 `--verbose=1` 또는 `-v`입니다. |
| `--version` | `-V` | 이 응용 프로그램 버전 표시 |
| `--ansi` | 해당 사항 없음 | ANSI 출력 강제 실행 |
| `--no-ansi` | 해당 사항 없음 | ANSI 출력 비활성화 |
