---
source-git-commit: 90e3f9cb6033c91be67947e84520d3e2537ca5d9
workflow-type: tm+mt
source-wordcount: '358'
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
