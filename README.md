---
source-git-commit: 4589c405bab743001e967a9825d578ee1a03c216
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 3%

---
# Adobe Commerce 운영 기술 설명서

커뮤니티의 콘텐츠 제공과 설명서 팀 외부 Adobe 직원의 콘텐츠 제공도 환영합니다.

## 이미지 최적화를 위한 사전 커밋 후크

이 저장소에는 커밋하기 전에 이미지를 최적화하는 자동화된 사전 커밋 후크가 포함됩니다. **일관된 이미지 최적화와 저장소 크기를 줄이려면 모든 기여자가 이러한 후크를 사용하도록 설정해야 합니다**.

### 빠른 설정

저장소를 복제한 후 다음을 실행합니다.

```bash
.githooks/setup-hooks.sh
```

### 후크가 수행하는 작업

- 스테이징된 이미지 파일(PNG, JPG, JPEG, GIF, SVG) 자동 감지
- `image_optim`을(를) 실행하여 이미지 압축 및 최적화
- 최적화된 이미지 자동 재스테이지
- 커밋된 모든 이미지가 올바르게 최적화되었는지 확인

### 이점

- 저장소 크기 감소
- 설명서를 위한 빠른 페이지 로드
- 모든 기여자에서 일관된 이미지 품질
- 수동 최적화 불필요

자세한 설정 지침, 문제 해결 및 구성은 [`.githooks/README.md`](.githooks/README.md)을(를) 참조하십시오.

## Adobe Open Source 행동 수칙

이 프로젝트에서는 [Adobe OOCT(Open Source Code of Conduct)](code-of-conduct.md) 또는 [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct)가 채택되었습니다. 자세한 내용은 [기여](contributing.md) 문서를 참조하십시오.

## Adobe 콘텐츠에 대한 귀하의 기여 관련 정보

[Adobe 문서 기여자 안내서](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)를 참조하세요.

기여 방식은 기여자 및 기여 하고자 하는 변경 사항의 종류에 따라 다릅니다.

### 사소한 변경 사항

부분 업데이트에 기여하는 경우 문서를 방문하여 문서 하단에 나타나는 피드백 영역을 클릭하고 **자세한 피드백 옵션**&#x200B;을 클릭한 다음 **편집 제안**&#x200B;을 클릭하여 GitHub의 Markdown 소스 파일로 이동하십시오. GitHub UI를 사용하여 업데이트를 만듭니다. 자세한 내용은 일반 [Adobe 문서 기여자 안내서](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)를 참조하십시오.

이 저장소의 설명서 및 코드 샘플에 대해 사용자가 제출하는 부분 수정 또는 설명은 Adobe 사용 약관의 적용을 받습니다.

### 커뮤니티 구성원의 주요 변경 사항 또는 새 문서

Adobe 커뮤니티에 소속되어 있고 새 문서를 만들거나 주요 변경 사항을 제출하려는 경우 Git 리포지토리의 문제 탭을 사용하여 문제를 제출하면 설명서 팀과 대화를 시작할 수 있습니다. 플랜에 동의하면 직원과 협력하여 공용 및 개인 리포지토리에서 작업을 결합하여 새로운 콘텐츠를 제공할 수 있습니다.

### Adobe 직원의 주요 변경 사항

Adobe Experience Cloud 솔루션에 대한 제품 팀의 테크니컬 라이터, 프로그램 관리자 또는 개발자이고 기술 문서에 기여하거나 기술 문서를 작성하는 것이 본인의 직무인 경우 개인 리포지토리(`https://git.corp.adobe.com/AdobeDocs`)를 사용해야 합니다.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## 도구 및 설정

커뮤니티 기여자는 기본 편집에 GitHub UI를 사용하거나 리포지토리를 포크하여 크게 기여할 수 있습니다.

자세한 내용은 [Adobe 문서 기여자 안내서](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)를 참조하십시오.

## Markdown을 사용하여 주제 서식을 지정하는 방법

이 저장소의 모든 문서는 GitHub 버전의 Markdown을 사용합니다. Markdown에 익숙하지 않은 경우 다음을 참조하십시오.

- [Markdown 기본 사항](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
- [인쇄 가능한 Markdown 치트시트](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## 템플릿

일부 항목의 경우 데이터 파일 및 템플릿을 사용하여 게시된 콘텐츠를 생성합니다. 이 접근 방식의 사용 사례는 다음과 같습니다.

- 프로그래밍 방식으로 생성된 대용량 콘텐츠 세트 게시
- 통합을 위해 YAML과 같이 기계가 읽을 수 있는 파일 형식을 필요로 하는 여러 시스템(예: 사이트 전체 분석 도구)에서 고객을 위한 단일 소스 제공

템플릿 컨텐츠의 예로는 다음이 포함됩니다(이에 제한되지 않음).

- [CLI 도구 참조](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
- [제품 가용성 테이블](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
- [시스템 요구 사항 테이블](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### 템플릿 콘텐츠 생성

일반적으로 대부분의 작성자는 제품 가용성 및 시스템 요구 사항 테이블에 릴리스 버전만 추가하면 됩니다. 기타 모든 템플릿 콘텐츠에 대한 유지 관리는 전담 팀원이 자동화하거나 관리합니다. 이러한 지침은 대부분의 작성자를 대상으로 합니다.

>**참고:**
>
>- 템플릿화된 콘텐츠를 생성하려면 터미널의 명령줄에서 작업해야 합니다.
>- 렌더링 스크립트를 실행하려면 루비가 설치되어 있어야 합니다. 필요한 버전은 [_jekyll/.ruby-version] (_jekyll/.ruby-version)을(를) 참조하십시오.

템플릿 컨텐츠의 파일 구조에 대한 설명은 다음을 참조하십시오.

- `_jekyll` - 템플릿화된 주제 및 필수 자산을 포함합니다.
- `_jekyll/_data` - 템플릿을 렌더링하는 데 사용되는 컴퓨터에서 읽을 수 있는 파일 형식을 포함합니다.
- `_jekyll/templated` - Liquid 템플릿 언어를 사용하는 HTML 기반 템플릿 파일이 포함되어 있습니다.
- `help/_includes/templated` - 템플릿화된 콘텐츠에 대해 생성된 출력을 `.md` 파일 형식으로 포함하므로 Experience League 주제에 게시할 수 있습니다. 렌더링 스크립트는 생성된 출력을 자동으로 이 디렉터리에 기록합니다

템플릿 컨텐츠를 업데이트하려면 다음을 수행합니다.

1. 텍스트 편집기에서 `/jekyll/_data` 디렉터리에서 데이터 파일을 엽니다. For example:

   - [제품 가용성 테이블](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   - [시스템 요구 사항 테이블](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. 기존 YAML 구조를 사용하여 엔트리를 작성합니다.

   예를 들어, 제품 가용성 테이블에 Adobe Commerce 버전을 추가하려면 `extensions` 파일의 `services` 및 `/jekyll/_data/product-availability.yml` 섹션의 각 항목에 다음을 추가하십시오(필요에 따라 버전 번호를 수정하십시오).

   ```yaml
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. `_jekyll` 디렉터리로 이동합니다.

   ```bash
   cd _jekyll
   ```

1. 템플릿화된 콘텐츠를 생성하고 출력을 `help/_includes/templated` 디렉터리에 씁니다.

   ```bash
   bundle exec rake render
   ```

   >**참고:** `_jekyll` 디렉터리에서 스크립트를 실행해야 합니다. 스크립트를 처음 실행하는 경우에는 먼저 `bundle install` 명령을 사용하여 Ruby 종속성을 설치해야 합니다. `adobe-comdox-exl-rake-tasks` gem에서 핵심 레이크 작업 및 종속성(Jekyll, Rake, 이미지 최적화)을 제공하여 Adobe Commerce 설명서 저장소 전반에서 유지 관리를 향상시킵니다. 이 리포지토리와 관련된 사용자 지정 작업은 `Rakefile`에서 구현됩니다.

1. `root` 디렉터리로 다시 이동합니다.

   ```bash
   cd ..
   ```

1. 필요한 `help/_includes/templated`개의 파일이 수정되었는지 확인합니다.

   ```bash
   git status
   ```

   다음과 유사한 출력이 표시됩니다.

   ```bash
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. 변경 사항을 푸시합니다.

   ```bash
   git add .
   git commit -m "descriptive message of the intended commit"
   git push
   ```

[데이터 파일](https://jekyllrb.com/docs/datafiles), [액체 필터](https://jekyllrb.com/docs/liquid/filters/) 및 기타 기능에 대한 자세한 내용은 Jekyll 설명서를 참조하세요.

## 사용 가능한 레이크 작업

이 리포지토리는 `adobe-comdox-exl-rake-tasks` gem에서 제공하는 레이크 작업을 사용합니다. 사용 가능한 모든 작업을 보려면 다음을 실행합니다.

```bash
cd _jekyll
bundle exec rake --tasks
```
