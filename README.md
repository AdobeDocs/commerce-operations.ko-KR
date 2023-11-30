---
source-git-commit: 580a15c908fc8ac4ef5d62582dfdd87d75dde994
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 3%

---
# Adobe Commerce 기술 설명서

커뮤니티의 콘텐츠 제공과 설명서 팀 외부 Adobe 직원의 콘텐츠 제공도 환영합니다.

## Adobe 오픈 소스 행동 수칙

이 프로젝트에서는 [Adobe OOCT(Open Source Code of Conduct)](code-of-conduct.md) 또는 [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct)가 채택되었습니다. 자세한 내용은 [기여](contributing.md) 문서를 참조하십시오.

## Adobe 콘텐츠에 대한 귀하의 기여에 대해

다음을 참조하십시오. [Adobe 문서 기여자 안내서](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

기여 방식은 기여자 및 기여 하고자 하는 변경 사항의 종류에 따라 다릅니다.

### 사소한 변경 사항

부분 업데이트에 기여하는 경우 문서를 방문하여 문서 하단에 나타나는 피드백 영역을 클릭하고 **자세한 피드백 옵션**&#x200B;을 클릭한 다음 을 클릭합니다 **편집 제안** GitHub의 Markdown 소스 파일로 이동합니다. GitHub UI를 사용하여 업데이트를 만듭니다. 일반 참조 [Adobe 문서 기여자 안내서](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) 추가 정보.

이 저장소의 설명서 및 코드 샘플에 대해 사용자가 제출하는 부분 수정 또는 설명은 Adobe 사용 약관의 적용을 받습니다.

### 커뮤니티 구성원의 주요 변경 사항 또는 새 문서

Adobe 커뮤니티에 소속되어 있고 새 문서를 만들거나 주요 변경 사항을 제출하려는 경우 Git 리포지토리의 문제 탭을 사용하여 문제를 제출하면 설명서 팀과 대화를 시작할 수 있습니다. 플랜에 동의하면 직원과 협력하여 공용 및 개인 리포지토리에서 작업을 결합하여 새로운 콘텐츠를 제공할 수 있습니다.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Adobe 직원의 주요 변경 사항

Adobe Experience Cloud 솔루션에 대한 제품 팀의 테크니컬 라이터, 프로그램 관리자 또는 개발자이고 기술 문서에 기여하거나 기술 문서를 작성하는 것이 본인의 직무인 경우 개인 리포지토리( )를 사용해야 합니다. `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## 도구 및 설정

커뮤니티 기여자는 기본 편집에 GitHub UI를 사용하거나 리포지토리를 포크하여 크게 기여할 수 있습니다.

다음을 참조하십시오. [Adobe 문서 기여자 안내서](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) 을 참조하십시오.

## Markdown을 사용하여 주제 서식을 지정하는 방법

이 저장소의 모든 문서는 GitHub 버전의 Markdown을 사용합니다. Markdown에 익숙하지 않은 경우 다음을 참조하십시오.

* [Markdown 기본 사항](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [인쇄 가능한 Markdown 치트시트](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## 템플릿

일부 항목의 경우 데이터 파일 및 템플릿을 사용하여 게시된 콘텐츠를 생성합니다. 이 접근 방식의 사용 사례는 다음과 같습니다.

* 프로그래밍 방식으로 생성된 대용량 콘텐츠 세트 게시
* 통합을 위해 YAML과 같이 기계가 읽을 수 있는 파일 형식을 필요로 하는 여러 시스템(예: 사이트 전체 분석 도구)에서 고객을 위한 단일 소스 제공

템플릿 컨텐츠의 예로는 다음이 포함됩니다(이에 제한되지 않음).

* [CLI 툴 참조](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
* [제품 가용성 테이블](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
* [시스템 요구 사항 테이블](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### 템플릿 콘텐츠 생성

일반적으로 대부분의 작성자는 제품 가용성 및 시스템 요구 사항 테이블에 릴리스 버전만 추가하면 됩니다. 기타 모든 템플릿 콘텐츠에 대한 유지 관리는 전담 팀원이 자동화하거나 관리합니다. 이러한 지침은 &quot;대부분의&quot; 작성자를 대상으로 합니다.

>**참고:**
>
>* 템플릿화된 콘텐츠를 생성하려면 터미널의 명령줄에서 작업해야 합니다.
>* 렌더링 스크립트를 실행하려면 루비가 설치되어 있어야 합니다. 다음을 참조하십시오 [_jekyll/.ruby-version](_jekyll/.ruby-version) 필요한 버전용입니다.

템플릿 컨텐츠의 파일 구조에 대한 설명은 다음을 참조하십시오.

* `_jekyll`- 템플릿화된 주제 및 필수 에셋을 포함합니다.
* `_jekyll/_data`- 템플릿을 렌더링하는 데 사용되는 시스템에서 읽을 수 있는 파일 형식을 포함합니다.
* `_jekyll/templated`- Liquid 템플릿 언어를 사용하는 HTML 기반 템플릿 파일이 포함됩니다.
* `help/_includes/templated`- 템플릿으로 만들어진 콘텐츠에 대해 생성된 출력을 포함합니다. `.md` 파일 형식이므로 Experience League 주제에 게시할 수 있습니다. 렌더링 스크립트는 생성된 출력을 자동으로 이 디렉터리에 기록합니다

템플릿 컨텐츠를 업데이트하려면 다음을 수행합니다.

1. 텍스트 편집기에서 `/jekyll/_data` 디렉토리. For example:

   * [제품 가용성 테이블](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   * [시스템 요구 사항 테이블](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. 기존 YAML 구조를 사용하여 엔트리를 작성합니다.

   예를 들어 제품 가용성 테이블에 Adobe Commerce 버전을 추가하려면 의 각 항목에 다음을 추가합니다. `extensions` 및 `services` 의 섹션 `/jekyll/_data/product-availability.yml` 파일(필요에 따라 버전 번호 수정):

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. 다음 위치로 이동 `_jekyll` 디렉토리.

   ```
   cd _jekyll
   ```

1. 템플릿화된 콘텐츠를 생성하고 출력을 `help/_includes/templated` 디렉토리.

   ```
   rake render
   ```

   >**참고:** 다음에서 스크립트를 실행해야 합니다. `_jekyll` 디렉토리. 스크립트를 처음 실행하는 경우 먼저 Ruby 종속성을 `bundle install` 명령입니다.

1. 예상 값 확인 `help/_includes/templated` 파일이 수정되었습니다.

   ```
   git status
   ```

   다음과 유사한 출력이 표시됩니다.

   ```
   modified:   _data/product-availability.yml
   modified:   ../help/_includes/templated/product-availability-extensions.md
   ```

에 대한 자세한 내용은 Jekyll 설명서 를 참조하십시오. [데이터 파일](https://jekyllrb.com/docs/datafiles), [액체 필터](https://jekyllrb.com/docs/liquid/filters/)및 기타 기능.
