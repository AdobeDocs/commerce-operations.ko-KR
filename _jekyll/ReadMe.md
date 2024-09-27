---
source-git-commit: ca9e04d50e69b8a51ec4a6fbcf1d35f0fb363fab
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---
# 개요

이 프로젝트에는 뉴스 다이제스트에 대한 데이터 생성, 템플릿 파일 렌더링, 이미지 최적화 및 맵 생성과 같은 워크플로의 다양한 측면을 자동화하는 여러 가지 Rake 작업이 포함되어 있습니다. 아래는 Rakefile에 정의된 각 Rake 작업에 대한 설명과 사용 지침이다.

## 레이크 작업

### `render`

`_jekyll/_data/`의 데이터를 사용하여 `_jekyll/templates` 디렉터리에 있는 템플릿화된 파일을 렌더링합니다. 결과는 `help/includes/templated` 디렉터리에 있습니다.

**사용량:**

```sh
rake render
```

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

## 전제 조건

- Ruby와 Bundler가 설치되었습니다.
- Gemfile에 지정된 필수 gems.
- `azure_regions` 작업에 대한 Python, [PyGMT](https://www.pygmt.org/latest/install.html) 및 [pdf2svg](https://formulae.brew.sh/formula/pdf2svg).

## 설정

1. 필요한 Gems 설치:

   ```sh
   bundle install
   ```

2. `azure_regions` 작업에 대해 Python, PyGMT 및 pdf2svg가 설치되어 있는지 확인합니다. 설정에 대한 자세한 내용은 [_scripts/azure_regions.py](_scripts/azure_regions.py)의 댓글에서 설명서를 참조하세요.
