---
source-git-commit: 4589c405bab743001e967a9825d578ee1a03c216
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---
# 개요

이 프로젝트에는 뉴스 다이제스트에 대한 데이터 생성, 템플릿 파일 렌더링, 이미지 최적화 및 맵 생성과 같은 워크플로의 다양한 측면을 자동화하는 여러 가지 Rake 작업이 포함되어 있습니다. 아래는 Rakefile에 정의된 각 Rake 작업에 대한 설명과 사용 지침이다.

## 레이크 작업

### `render`

`_jekyll/templates`의 데이터를 사용하여 `_jekyll/_data/` 디렉터리에 있는 템플릿화된 파일을 렌더링합니다. 결과는 `help/includes/templated` 디렉터리에 있습니다. 이 작업은 렌더링 후 포함 관계 및 타임스탬프를 자동으로 유지 관리합니다.

**사용량:**

```sh
rake render
```

**기능:**
- 렌더링 스크립트를 실행하여 템플릿화된 파일을 생성합니다.
- `includes:maintain_all`을(를) 실행하여 포함 관계 및 타임스탬프 업데이트
- 렌더링 후 모든 포함 메타데이터가 최신 상태인지 확인합니다.

### `image_optim`

수정된 커밋되지 않은 파일의 이미지를 최적화합니다. 다른 이미지의 경우 `path` 인수를 사용하여 디렉터리 또는 파일을 지정하십시오.

**사용량:**

```sh
rake image_optim
```

**인수 `path`개 사용:**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

뉴스 다이제스트에 대한 데이터를 생성합니다. 기본 기간은 마지막 업데이트 이후입니다. `since` 인수를 사용하여 다른 마침표를 지정할 수 있습니다.

**사용량:**

```sh
rake whatsnew
```

**인수 `since`개 사용:**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

모범 사례에서 뉴스 다이제스트에 대한 데이터를 생성합니다. 기본 기간은 마지막 업데이트 이후입니다. `since` 인수를 사용하여 다른 마침표를 지정할 수 있습니다.

**사용량:**

```sh
rake whatsnew_bp
```

**인수 `since`개 사용:**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

Azure 지역 맵을 생성합니다. 입력 데이터 파일은 `_jekyll/tmp/azure-regions.json`에 배치해야 합니다. 결과는 `_jekyll/tmp/azure-regions.svg`에서 찾을 수 있습니다. Python, [PyGMT](https://www.pygmt.org/latest/install.html) 및 [pdf2svg](https://formulae.brew.sh/formula/pdf2svg)이(가) 설치되어 있어야 합니다.

**사용량:**

```sh
rake azure_regions
```

### `get_released_versions`

`magento/magento2` 저장소에서 마지막 10개의 릴리스 버전을 가져옵니다. 설치 및 인증을 위해 [GitHub CLI](https://cli.github.com/)가 필요합니다.

**사용량:**

```sh
rake get_released_versions
```

**출력:** 릴리스 태그 이름과 날짜를 사용하여 `tmp/core-release.txt`을(를) 생성합니다.

### `first_merge_date`

지정된 분기에 첫 번째 병합의 날짜를 가져옵니다. 설치 및 인증을 위해 [GitHub CLI](https://cli.github.com/)가 필요합니다.

**사용량:**

```sh
rake first_merge_date base=develop
```

**인수:**

- `base`(필수): 병합을 검사할 대상 분기 이름입니다.

### `includes:maintain_relationships`

`include-relationships.yml` 패턴을 사용하여 `help` 디렉터리의 모든 Markdown 파일에서 include 문을 검사하여 `{{$include /help/_includes/filename.md}}` 파일을 검색하고 업데이트합니다. 이 작업은 기본 컨텐츠 파일과 포함된 파일 간의 관계를 자동으로 유지합니다.

**사용량:**

```sh
rake includes:maintain_relationships
```

**기능:**
- `help/_includes` 디렉터리에서 기존 포함 파일 목록을 읽습니다.
- 모든 기본 Markdown 파일을 검색하여 각 파일에 포함된 참조 파일을 찾습니다.
- `{{$include /help/_includes/filename.md}}` 패턴을 사용하여 참조 식별
- 검색된 관계로 `include-relationships.yml` 파일을 업데이트합니다.
- 변경 사항에 대한 요약을 제공하고 참조되지 않은 포함 항목을 식별합니다.

### `includes:maintain_timestamps`

최신 포함 파일 변경 타임스탬프를 기본 파일에 추가하여 포함 타임스탬프를 유지 관리합니다. 이 작업은 `include-relationships.yml` 파일을 읽고, 각 포함 파일에 대한 git 기록을 확인하고, 기본 파일의 끝에 타임스탬프를 추가하거나 업데이트합니다.

**사용량:**

```sh
rake includes:maintain_timestamps
```

**기능:**
- `include-relationships.yml`의 관계가 로드됩니다.
- 각 기본 파일에 대해 는 포함 파일 중에서 최신 git 커밋 날짜를 찾습니다
- 기본 파일 끝에 타임스탬프가 있는 HTML 주석을 추가하거나 업데이트합니다.
- 다음 형식을 사용합니다. `<!-- Last updated from includes: YYYY-MM-DD HH:MM:SS -->`
- 검사된 파일과 해당 타임스탬프를 포함하는 자세한 출력을 제공합니다.

**출력 예:**

```console
Processing installation/advanced.md...
  Latest include change: 2024-04-16 09:42:31
  Include files checked: help/_includes/cli-consumers.md (2022-09-12 09:38:25), help/_includes/secure-install.md (2022-09-08 11:33:05), help/_includes/sensitive-data.md (2024-04-16 09:42:31)
  Added new timestamp
```

### `includes:maintain_all`

`includes:maintain_relationships`과(와) `includes:maintain_timestamps`을(를) 순서대로 실행하는 편의 작업입니다. 관계와 타임스탬프를 모두 포함하여 유지 관리하는 것이 좋습니다.

**사용량:**

```sh
rake includes:maintain_all
```

### `unused_includes`

Markdown 파일에서 참조하지 않는 `help/_includes` 디렉터리의 포함 파일을 찾습니다. 이렇게 하면 안전하게 제거할 수 있는 분리된 포함 파일을 식별하는 데 도움이 됩니다.

**사용량:**

```sh
rake unused_includes
```

## 사용 가능한 작업 나열

설명이 있는 사용 가능한 모든 레이크 작업을 보려면 다음을 사용합니다.

```sh
rake --tasks
```

특정 작업에 대한 자세한 내용은 다음을 참조하십시오.

```sh
rake -T [task_name]
```

## 관리 작업 포함

모든 포함 관련 작업은 더 나은 조직을 위해 `includes` 네임스페이스 아래에 구성됩니다.

```sh
# Discover and maintain include relationships
rake includes:maintain_relationships

# Add/update timestamps based on include file changes
rake includes:maintain_timestamps

# Do both operations in sequence (recommended)
rake includes:maintain_all
```

## 관계 파일 형식 포함

`include-relationships.yml` 파일은 기본 콘텐츠 파일과 포함된 파일 간의 관계를 추적합니다. 이 파일은 기존 포함 파일을 읽고 이를 참조하는 기본 파일을 찾아 관계를 검색하는 `maintain_include_relationships` 레이크 작업에 의해 자동으로 관리됩니다.

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
- Gemfile에 지정된 필수 GEMS(핵심 종속성은 `adobe-comdox-exl-rake-tasks`에서 제공됨)입니다.
- [ 및 ](https://cli.github.com/) 작업에 대한 `get_released_versions`GitHub CLI`first_merge_date`.
- [ 작업에 대한 Python, ](https://www.pygmt.org/latest/install.html)PyGMT[ 및 ](https://formulae.brew.sh/formula/pdf2svg)pdf2svg`azure_regions`.

## 설정

1. 필요한 Gems 설치:

   ```sh
   bundle install
   ```

2. `azure_regions` 작업에 대해 Python, PyGMT 및 pdf2svg가 설치되어 있는지 확인합니다. 설정에 대한 자세한 내용은 [_scripts/azure_regions.py](_scripts/azure_regions.py)의 댓글에서 설명서를 참조하세요.
