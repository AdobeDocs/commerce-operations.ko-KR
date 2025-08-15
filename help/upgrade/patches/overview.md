---
title: 패치 작동 방식
description: Adobe Commerce에 대한 다양한 유형의 패치와 그 작동 방식에 대해 알아봅니다.
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# 패치 작동 방식

>[!WARNING]
>
>프로덕션에 배포하기 전에 스테이징 또는 개발 환경에서 모든 패치를 테스트하는 것이 좋습니다. 또한 패치를 적용하기 전에 데이터를 백업하는 것이 좋습니다. [파일 시스템 백업 및 롤백](../../installation/tutorials/backup.md)을 참조하십시오.

패치(또는 diff) 파일은 다음을 참고하는 텍스트 파일입니다.

- 변경할 파일입니다.
- 변경을 시작할 줄 번호와 변경할 줄 수입니다.
- 스왑할 새 코드.

패치 프로그램이 실행되면 이 파일을 읽고 지정된 변경 사항이 파일에 적용됩니다.

세 가지 유형의 패치가 있습니다.

- **핫픽스**—Adobe이 [보안 센터](https://magento.com/security/patches)에 게시하는 패치입니다.
- **개별 패치** - Adobe Commerce에서 개별적으로 만들고 배포하는 패치입니다.
- **사용자 지정 패치**—git 커밋에서 생성할 수 있는 비공식 패치입니다.

## 핫픽스

핫픽스는 많은 판매자에게 영향을 미치는 높은 수준의 보안 또는 품질 수정 사항이 포함된 패치입니다. 이러한 수정 사항은 적용 가능한 부 버전에 대한 다음 패치 릴리스에 적용됩니다. Adobe은 필요에 따라 핫픽스를 릴리스합니다.

[보안 센터](https://magento.com/security/patches)에서 핫픽스를 찾을 수 있습니다. 버전과 설치 유형에 따라 페이지의 지침에 따라 패치 파일을 다운로드합니다. 핫픽스 패치를 적용하려면 [명령줄](../patches/apply.md#) 또는 [작성기](../patches/apply.md)를 사용하십시오.

>[!NOTE]
>
>핫픽스에는 이전 버전과 호환 불가능한 변경 사항이 포함될 수 있습니다.

## 개별 패치

개별 패치에는 특정 문제에 대한 영향이 적은 품질 수정 사항이 포함되어 있습니다. 이러한 수정 사항은 가장 최근에 지원되는 부 버전(예: 2.4.x)에 적용되지만 이전에 지원되는 부 버전(예: 2.3.x)에서 누락될 수 있습니다. Adobe은 필요에 따라 개별 패치를 릴리스합니다.

[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}을(를) 사용하여 개별 패치를 적용하십시오.

>[!NOTE]
>
>개별 패치에는 이전 버전과 호환 불가능한 변경 사항이 포함되어 있지 않습니다.

## 사용자 지정 패치

Adobe 엔지니어링 팀이 Adobe Commerce Composer 릴리스의 GitHub에서 버그 수정을 포함하는 데 시간이 조금 걸릴 수 있습니다. 그동안 GitHub에서 패치를 만들고 [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) 플러그인을 사용하여 작성기 기반 설치에 적용할 수 있습니다.

사용자 지정 패치를 적용하려면 [명령줄](apply.md#command-line) 또는 [작성기](apply.md#composer)를 사용하십시오.

사용자 지정 패치 파일을 만드는 방법은 여러 가지가 있습니다. 다음 예제는 알려진 git 커밋에서 패치를 만드는 데 중점을 둡니다.

사용자 지정 패치를 만들려면 다음 작업을 수행하십시오.

1. 로컬 프로젝트에 `patches/composer` 디렉터리를 만듭니다.
1. 패치에 사용할 GitHub 커밋 또는 가져오기 요청을 식별합니다. 이 예제에서는 GitHub 문제 [`2d31571`#6474](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede)에 연결된 [&#128279;](https://github.com/magento/magento2/issues/6474) 커밋을 사용합니다.
1. `.patch` 또는 `.diff` 확장을 커밋 URL에 추가합니다. 파일 크기가 더 작은 경우 `.diff`을(를) 사용하십시오. 예: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. 페이지를 `patches/composer` 디렉터리에 파일로 저장합니다. 예: `github-issue-6474.diff`.
1. 파일을 편집하고 `app/code/<VENDOR>/<PACKAGE>` 디렉터리에 상대적이 되도록 모든 경로에서 `vendor/<VENDOR>/<PACKAGE>`을(를) 제거합니다.

   >[!NOTE]
   >
   >후행 공백을 자동으로 제거하거나 새 줄을 추가하는 텍스트 편집기로 패치가 손상될 수 있습니다. 간단한 텍스트 편집기를 사용하여 이러한 변경 작업을 수행합니다.

다음 예제에서는 `app/code/Magento/Payment`의 모든 인스턴스를 제거한 후 앞에서 언급한 DIFF 파일을 보여 줍니다.

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

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [명령줄](/help/upgrade/patches/apply.md#command-line)
- [작성기](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>클라우드 인프라 프로젝트의 Adobe Commerce에 패치를 적용하려면 [Cloud의 Commerce 안내서](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)에서 _패치 적용_&#x200B;을 참조하십시오.
