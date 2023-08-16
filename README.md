---
source-git-commit: 8b82081057af7d134528988d3f9f7cf53f4d7525
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 5%

---
# Adobe Commerce 기술 설명서

커뮤니티의 콘텐츠 제공과 설명서 팀 외부 Adobe 직원의 콘텐츠 제공도 환영합니다.

## Adobe 오픈 소스 행동 수칙

이 프로젝트에서는 [Adobe OOCT(Open Source Code of Conduct)](code-of-conduct.md) 또는 [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct)가 채택되었습니다. 자세한 내용은 [기여](contributing.md) 문서를 참조하십시오.

## Adobe 콘텐츠에 대한 귀하의 기여에 대해

다음을 참조하십시오. [Adobe 문서 기여자 안내서](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

기여 방식은 기여자 및 기여 하고자 하는 변경 사항의 종류에 따라 다릅니다.

### 사소한 변경 사항

선의로 작은 업데이트를 제공하려면 문서를 방문하여 **편집** 문서에 해당하는 GitHub 소스로 이동하는 문서의 링크. 그런 다음 GitHub UI를 사용하여 업데이트를 만들면 됩니다. 일반 참조 [Adobe 문서 기여자 안내서](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) 추가 정보.

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

다음 `_jekyll` 디렉터리에는 템플릿화된 주제 및 필수 에셋이 포함되어 있습니다.
Liquid 템플릿 언어를 사용하는 템플릿은 `_jekyll/templated` 디렉터리를 HTML 파일로 지정합니다.
다음 `_jekyll/_data` 디렉터리에는 템플릿을 렌더링하는 데 사용되는 데이터가 있는 파일이 포함되어 있습니다.

모든 템플릿을 렌더링하려면 다음을 수행하십시오.

1. 다음 위치로 이동 `_jekyll` 디렉토리.

   cd _jekyll

1. 렌더링 스크립트를 실행합니다.

```
_scripts/render
```

> **참고:** 다음에서 스크립트를 실행해야 합니다. `_jekyll` 디렉토리.
> **참고:** 이 스크립트를 실행하려면 루비가 설치되어 있어야 합니다.

스크립트는 렌더링을 실행하고 렌더링된 템플릿을 `help/_includes/templated` 디렉토리.

에 대한 자세한 내용은 Jekyll 설명서 를 참조하십시오. [데이터 파일](https://jekyllrb.com/docs/datafiles), [액체 필터](https://jekyllrb.com/docs/liquid/filters/)및 기타 기능.
