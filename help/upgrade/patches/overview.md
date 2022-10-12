---
title: 패치 작동 방식
description: Adobe Commerce 및 Magento Open Source의 다양한 패치 유형과 패치 작동 방식에 대해 알아봅니다.
source-git-commit: 1a18a445cb104420dd9b853b7c4d42ce3bddf2ac
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 패치 작동 방식

>[!WARNING]
>
>프로덕션에 배포하기 전에 스테이징 또는 개발 환경에서 모든 패치를 테스트하는 것이 좋습니다. 패치를 적용하기 전에 데이터를 백업하는 것이 좋습니다. 자세한 내용은 [파일 시스템 백업 및 롤백](../../installation/tutorials/backup.md).

패치(또는 diff) 파일은 다음에 참하는 텍스트 파일입니다.

- 변경할 파일입니다.
- 변경을 시작할 라인 번호와 변경할 라인 수
- 바꿀 새 코드입니다.

패치 프로그램이 실행되면 이 파일이 읽히고 지정된 변경 사항이 파일에 적용됩니다.

패치 유형은 다음과 같습니다.

- **핫픽스**—Adobe이 [보안 센터](https://magento.com/security/patches).
- **개별 패치**—Adobe Commerce 지원 센터에서 개별 단위로 생성 및 배포하는 패치
- **사용자 정의 패치**- Git 커밋에서 만들 수 있는 비공식적인 패치

## 핫픽스

핫픽스는 많은 판매자에게 영향을 주는 보안 또는 품질 수정 사항이 포함된 패치입니다. 이러한 수정 사항은 적용 가능한 부 버전에 대한 다음 패치 릴리스에 적용됩니다. 필요에 따라 Adobe 릴리스 핫픽스.

에서 핫픽스를 찾을 수 있습니다. [보안 센터](https://magento.com/security/patches). 페이지의 지침에 따라 버전 및 설치 유형에 따라 패치 파일을 다운로드합니다. 를 사용하십시오 [명령줄](../patches/apply.md#) 또는 [작성기](../patches/apply.md) 핫픽스 패치를 적용하려면

>[!NOTE]
>
>핫픽스에는 호환되지 않는 변경 사항이 포함될 수 있습니다.

## 개별 패치

개별 패치에는 특정 문제에 대한 저충격 품질 수정 사항이 포함되어 있습니다. 이러한 수정 사항은 가장 최근에 지원되는 부 버전(예: 2.4.x)에 적용되지만, 이전에 지원되는 부 버전(예: 2.3.x)에서 누락될 수 있습니다. Adobe은 필요에 따라 개별 패치를 릴리스합니다.

를 사용하십시오 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)개별 패치를 적용할 {target=&quot;_blank&quot;}.

>[!NOTE]
>
>개별 패치에는 호환되지 않는 변경 사항이 포함되어 있지 않습니다.

## 사용자 정의 패치

Adobe 엔지니어링 팀이 Adobe Commerce 또는 Magento Open Source 작성기 릴리스에서 GitHub에 수행된 버그 수정을 포함시키는 데 시간이 오래 걸리는 경우가 있습니다. 그 동안에는 GitHub에서 패치를 만들고 [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) 플러그인을 사용하여 Composer 기반 설치에 적용할 수 있습니다.

를 사용하십시오 [명령줄] 또는 [작성기] 사용자 정의 패치를 적용하려면

사용자 정의 패치 파일을 만드는 방법에는 여러 가지가 있습니다. 다음 예제는 알려진 Git 커밋에서 패치를 만드는 데 중점을 둡니다.

사용자 정의 패치를 생성하려면

1. 만들기 `patches/composer` 로컬 프로젝트의 디렉터리입니다.
1. 패치에 사용할 GitHub 커밋 또는 가져오기 요청을 식별합니다. 이 예제에서는 [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) 커밋, GitHub 문제에 연결 [#6474](https://github.com/magento/magento2/issues/6474).
1. 추가 `.patch` 또는 `.diff` 확장: 커밋 URL에 대한 . 사용 `.diff` 더 작은 파일 크기로 예: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. 페이지를 `patches/composer` 디렉토리. For example, `github-issue-6474.diff`.
1. 파일 편집 및 제거 `app/code/<VENDOR>/<PACKAGE>` 모든 경로에 있는 모든 경로에 있는 모든 경로에 있는 `vendor/<VENDOR>/<PACKAGE>` 디렉토리.

   >[!NOTE]
   >
   >후행 공백을 자동으로 제거하거나 새 줄을 추가하는 텍스트 편집기에 의해 패치가 중단됩니다. 간단한 텍스트 편집기를 사용하여 이러한 변경 작업을 수행합니다.

다음 예제에서는 모든 인스턴스를 제거한 후 이전에 언급된 DIFF 파일을 보여 줍니다 `app/code/Magento/Payment`:

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
             clearTimeout: function () {
                 clearTimeout(this.timeoutId);
+                this.fail();

                 return this;
             },
```

## 패치 적용

다음 방법 중 하나를 사용하여 패치를 적용할 수 있습니다.

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}
- [명령줄](/help/upgrade/patches/apply.md#command-line)
- [작성기](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>클라우드 인프라 프로젝트에서 Adobe Commerce에 패치를 적용하려면 다음을 참조하십시오 [패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 에서 _클라우드 안내서_.
