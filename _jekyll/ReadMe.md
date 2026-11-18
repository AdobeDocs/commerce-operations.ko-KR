---
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 63e52c8451f368e2d2a36096fc11c7ead62ee94e
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%
---

# 개요

이 프로젝트는 Rake 작업을 사용하여 설명서 워크플로의 일부를 자동화합니다. 대부분의 작업은 ExL Commerce 문서 리포지토리에서 공유되며 [`adobe-comdox-exl-rake-tasks`](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks) gem에서 가져옵니다. 아래의 몇 가지 작업은 이 저장소에만 해당됩니다.

**일반적인 작업(템플릿 렌더링, 이미지 관리, 이미지 최적화/감사, 새로운 기능 다이제스트 생성)에 대해서는 [adobe-comdox-exl-rake-tasks README](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md)을(를) 참조하십시오.**

> Gemfile과 Rakefile이 있는 `_jekyll/` 디렉터리 내에서 아래의 모든 `bundle exec rake` 명령을 실행해야 합니다.

## 저장소별 레이크 작업

### `whatsnew_bp`

모범 사례에서 뉴스 다이제스트에 대한 데이터를 생성합니다. 기본 기간은 마지막 업데이트 이후입니다. `since` 인수를 사용하여 다른 마침표를 지정할 수 있습니다.

**사용량:**

```sh
bundle exec rake whatsnew_bp
```

**인수 `since`개 사용:**

```sh
bundle exec rake whatsnew_bp since="jul 4"
```

### `whatsnew_consolidated`

게시된 새로운 기능 테이블을 구성된 Commerce 설명서 프로젝트의 `help/_includes/automated/whatsnew/consolidated.md`에 통합합니다.

```sh
bundle exec rake whatsnew_consolidated
```

[`_config.yml`](_config.yml)의 `whatsnew_consolidated.projects` 아래에서 프로젝트를 구성합니다. 각 항목에는 저장소 이름, 프로젝트 제목 및 절대 HTTP(S) 웹 사이트 URL이 필요합니다.

```yaml
whatsnew_consolidated:
  projects:
    - repo: commerce-operations.en
      title: Adobe Commerce operational guides
      website: https://experienceleague.adobe.com/ko/docs/commerce-operations/operational-guides/home
    - repo: commerce-webapi
      title: Adobe Commerce web APIs
      website: https://developer.adobe.com/commerce/webapi/
    - repo: commerce.en
      title: Adobe Commerce
      website: https://experienceleague.adobe.com/ko/docs/commerce
```

항목을 이동하여 섹션 순서를 변경합니다. 두 플랫폼 모두에서 프로젝트를 자유롭게 인터리브할 수 있습니다. `.en`(으)로 끝나는 저장소 이름은 ExL 원본 경로 `help/_includes/templated/whats-new.md`을(를) 사용합니다. 다른 모든 리포지토리는 DevSite 원본 경로 `src/pages/_includes/templated/whats-new.md`을(를) 사용합니다.

작업은 `AdobeDocs` GitHub 조직에서 공개 `main` 파일을 가져옵니다. 각 프로젝트 제목을 일반 텍스트 머리글로 표시하고 `website`에 새 기능 업데이트의 소스로 구성된 설명서 홈 페이지에 프로젝트 제목을 연결하는 문장으로 각 테이블을 소개합니다. 전체에서 `Description | Type | Date/source` 테이블 헤더를 사용합니다. DevSite 프로젝트에서만 이스케이프 처리된 `\<br/\>` 태그가 `<br/>`이(가) 되었습니다. 그렇지 않으면 본문 행, 중복, 링크 및 소스 행 순서는 변경되지 않습니다. 각 소스는 자체 기간을 정의합니다.

알려진 no-update 메시지가 있는 프로젝트는 생략됩니다. 모든 프로젝트에 항목이 없는 경우 포함에는 하나의 전체 업데이트 없음 메시지가 포함됩니다. 구성, 가져오기, 구문 분석 또는 쓰기 실패가 기존 포함을 바꾸지 않고 작업에 실패합니다.

이 작업에서는 생성 또는 업데이트 사용 페이지를 예약하지 않습니다.

포커스가 있는 테스트 세트에는 `_jekyll` Rakefile을 로드하고 Bundler를 통해 실행되는 레이크 진입점 테스트가 포함되어 있습니다. 먼저 Bundler 및 `_jekyll` 번들을 설치하십시오.

```sh
cd _jekyll && bundle install
```

그런 다음 저장소 루트에서 테스트를 실행합니다.

```sh
ruby _jekyll/test/consolidated_whatsnew_test.rb
```

### `whatsnew_feedback`

기존 로컬 `help/_includes/automated/whatsnew/consolidated.md` 포함을 필터링하여 `help/_includes/automated/whatsnew/consolidated-feedback.md`을(를) 만듭니다.

```sh
bundle exec rake whatsnew_feedback
```

작업이 `Feedback`을(를) 쉼표로 구분된 전체 형식 값으로 일치시키므로 대소문자와 주변 공백을 무시합니다. `Feedback, technical`과(와) 같은 결합된 형식이 포함됩니다. 설명, 소스 링크 또는 부분 형식 이름에 언급된 내용은 적합하지 않습니다.

일치하는 행, 중복, 일반 텍스트 프로젝트 제목, 소스 문장(있는 경우), 프로젝트 및 행 순서는 변경되지 않습니다. 일치하는 항목이 없는 프로젝트는 생략됩니다. 일치하는 항목이 없으면 출력에는 전체 비피드백 메시지가 한 개 포함됩니다.

입력이 이미 있어야 합니다. `bundle exec rake whatsnew_consolidated`을(를) 새로 고치려면 별도로 실행하십시오. 피드백 작업은 원격 콘텐츠를 가져오거나 프로젝트 구성을 읽거나 입력을 다시 생성하지 않습니다.

누락되었거나 형식이 잘못된 입력이 필터링된 기존 포함을 바꾸지 않고 작업에 실패합니다. 입력 파일은 수정되지 않으며 필터링된 출력은 자동으로 게시됩니다.

### `get_released_versions`

`magento/magento2` 저장소에서 마지막 10개의 릴리스 버전을 가져옵니다. 설치 및 인증을 위해 [GitHub CLI](https://cli.github.com/)가 필요합니다.

**사용량:**

```sh
bundle exec rake get_released_versions
```

**출력:** 릴리스 태그 이름과 날짜를 사용하여 `tmp/core-release.txt`을(를) 생성합니다.

### `first_merge_date`

지정된 분기에 첫 번째 병합의 날짜를 가져옵니다. 설치 및 인증을 위해 [GitHub CLI](https://cli.github.com/)가 필요합니다.

**사용량:**

```sh
bundle exec rake first_merge_date base=develop
```

**인수:**

- `base`(필수): 병합을 검사할 대상 분기 이름입니다.

## 사용 가능한 작업 나열

설명이 있는 사용 가능한 모든 레이크 작업을 보려면 다음을 사용합니다.

```sh
bundle exec rake --tasks
```

특정 작업에 대한 자세한 내용은 다음을 참조하십시오.

```sh
bundle exec rake -T [task_name]
```

## 관계 파일 형식 포함

`include-relationships.yml` 파일은 기본 콘텐츠 파일과 포함된 파일 간의 관계를 추적합니다. 이 파일은 기존 포함 파일을 읽고 이를 참조하는 기본 파일을 찾아 관계를 검색하는 `includes:maintain_relationships` 작업([adobe-comdox-exl-rake-tasks README](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md) 작업 사용 참조)에 의해 자동으로 유지됩니다.

**파일 구조:**

```yaml
---
metadata:
  last_updated: '2025-08-22 14:04:37'
  description: 'Index of main files and their included files for automatic timestamp updates'
  total_relationships: 57
  auto_discovered: true
  discovery_date: '2025-08-22 14:04:37'
relationships:
  configuration/deployment/example-environment-variables.md:
    - "/help/_includes/config-save-config.md"
    - "/help/_includes/config-update-build-system.md"
    - "/help/_includes/config-update-prod-system.md"
  # ... more relationships
```

**필드:**
- `metadata.last_updated`: 마지막 업데이트의 타임스탬프
- `metadata.total_relationships`: 포함된 총 기본 파일 수
- `metadata.auto_discovered`: 파일이 자동으로 생성되었음을 나타냅니다.
- `metadata.discovery_date`: 관계를 처음 발견한 날짜
- `relationships`: 기본 파일을 포함된 파일에 매핑

**Include 문 형식:**
기본 컨텐츠 파일은 다음 구문을 사용하여 다른 파일을 포함합니다.

```markdown
{{$include /help/_includes/filename.md}}
```

## 사전 요구 사항

- Ruby와 Bundler가 설치되었습니다.
- Gemfile에 지정된 필수 GEMS(일반 작업은 `adobe-comdox-exl-rake-tasks`에서 제공하며, `whatsnew` 작업에는 `whatsup_github`이(가) 추가로 필요합니다.)
- `get_released_versions` 및 `first_merge_date` 작업에 대한 [GitHub CLI](https://cli.github.com/).

## 설정

필요한 Gems 설치:

```sh
bundle install
```
