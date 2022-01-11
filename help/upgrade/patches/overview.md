---
title: 패치 작동 방식
description: Adobe Commerce 및 Magento Open Source의 다양한 패치 유형과 패치 작동 방식에 대해 알아봅니다.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 0%

---


# 패치 작동 방식

>[!WARNING]
>
>프로덕션에 배포하기 전에 스테이징 또는 개발 환경에서 모든 패치를 테스트하는 것이 좋습니다. 패치를 적용하기 전에 데이터를 백업하는 것이 좋습니다. 자세한 내용은 [파일 시스템 백업 및 롤백](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

패치(또는 diff) 파일은 다음에 참하는 텍스트 파일입니다.

- The file(s) to be changed.
- 변경을 시작할 라인 번호와 변경할 라인 수
- The new code to swap in.

When the [patch](https://en.wikipedia.org/wiki/Patch_(Unix)) program is run, this file is read in and the specified changes are made to the file(s).

There are three types of patches:

- **핫픽스**—Adobe이 [보안 센터](https://magento.com/security/patches).
- **개별 패치**—Adobe Commerce 지원 센터에서 개별 단위로 생성 및 배포하는 패치
- **Custom patches**—Unofficial patches that you can create from a git commit.

## 핫픽스

핫픽스는 많은 판매자에게 영향을 주는 보안 또는 품질 수정 사항이 포함된 패치입니다. These fixes are applied to the next patch release for the applicable minor version. 필요에 따라 Adobe 릴리스 핫픽스.

에서 핫픽스를 찾을 수 있습니다. [보안 센터](https://magento.com/security/patches). 페이지의 지침에 따라 버전 및 설치 유형에 따라 패치 파일을 다운로드합니다. 를 사용하십시오 [명령줄](../patches/apply.md#) 또는 [작성기](../patches/apply.md) 핫픽스 패치를 적용하려면

>[!NOTE]
>
>Hot fixes can contain backward incompatible changes.

## 개별 패치

Individual patches contain low-impact quality fixes for a specific issue. These fixes are applied to the most recently supported minor version (for example, 2.4.x), but could be missing from the previous supported minor version (for example, 2.3.x). Adobe releases individual patches as needed.

를 사용하십시오 [품질 패치 도구](https://devdocs.magento.com/quality-patches/tool.html) 개별 패치를 적용하려면

>[!NOTE]
>
>개별 패치에는 호환되지 않는 변경 사항이 포함되어 있지 않습니다.

## 사용자 정의 패치

Adobe 엔지니어링 팀이 Adobe Commerce 또는 Magento Open Source 작성기 릴리스에서 GitHub에 수행된 버그 수정을 포함시키는 데 시간이 오래 걸리는 경우가 있습니다. 그 동안에는 GitHub에서 패치를 만들고 [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) 플러그인을 사용하여 Composer 기반 설치에 적용할 수 있습니다.

를 사용하십시오 [명령줄] 또는 [작성기] 사용자 정의 패치를 적용하려면

사용자 정의 패치 파일을 만드는 방법에는 여러 가지가 있습니다. 다음 예제는 알려진 Git 커밋에서 패치를 만드는 데 중점을 둡니다.

사용자 정의 패치를 생성하려면

1. Create a `patches/composer` directory in your local project.
1. Identify the GitHub commit or pull request to use for the patch. This example uses the [`2d31571`](https://github.com/magento/magento2/commit/) commit, linked to GitHub issue [#6474](https://github.com/magento/magento2/issues/6474).
1. 추가 `.patch` 또는 `.diff` 확장: 커밋 URL에 대한 . Use `.diff` for a smaller file size. 예: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. 페이지를 `patches/composer` 디렉토리. 예, `github-issue-6474.diff`.
1. 파일 편집 및 제거 `app/code/<VENDOR>/<PACKAGE>` 모든 경로에 있는 모든 경로에 있는 모든 경로에 있는 `vendor/<VENDOR>/<PACKAGE>` 디렉토리.

   >[!NOTE]
   >
   >Text editors that automatically remove trailing whitespace or add new lines can break the patch. Use a simple text editor to make these changes.

The following example shows the previously mentioned DIFF file after removing all instances of `app/code/Magento/Payment`:

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
              clearTimeout: function () {
                  clearTimeout(this.timeoutId);
                  this.fail();
                  return this;
            },
```

## Applying patches

You can apply patches using any of the following methods:

- [Quality Patches Tool](https://devdocs.magento.com/quality-patches/tool.html)
- [Command line](../patches/apply.md#command-line)
- [Composer](../patches/apply.md#composer)

>[!NOTE]
>
>클라우드 인프라 프로젝트에서 Adobe Commerce에 패치를 적용하려면 다음을 참조하십시오 [패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 에서 _클라우드 안내서_.
