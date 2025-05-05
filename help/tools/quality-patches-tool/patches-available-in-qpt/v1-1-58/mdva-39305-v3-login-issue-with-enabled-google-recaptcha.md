---
title: 'MDVA-39305-V3:  [!DNL Google reCAPTCHA]이(가) 활성화된 로그인 문제'
description: ' [!DNL Google reCAPTCHA] 이(가) 활성화된 경우 등록된 고객이 로그인할 수 없는 Adobe Commerce 문제를 해결하려면 MDVA-39305-V3 패치를 적용합니다. 또한 이 패치는  [!DNL Google reCAPTCHA] 완전히 로드되기 전에 양식을 제출할 수 있는 문제도 해결합니다. 또한 CMS 페이지에서 블록이 기본값이 아닌 위치에 사용될 때 null*에서 멤버 함수 isDisabled()에 대한 *호출 오류가 수정됩니다.'
feature: Console
role: Admin
source-git-commit: 7846079987d2b7c0e9fdd0485bb3aae4f09cd6f9
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-39305-V3: [!DNL Google reCAPTCHA]이(가) 활성화된 로그인 문제

>[!NOTE]
>
>이 패치는 [MDVA-39305](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-1/mdva-39305-login-issues-with-enabled-google-recaptcha.md) 패치의 업데이트입니다.

MDVA-39305-V3 패치에서는 [!DNL Google reCAPTCHA]을(를) 사용할 수 있을 때 등록된 고객이 로그인할 수 없는 문제가 해결되었습니다. 또한 이 패치는 [!DNL Google reCAPTCHA]이(가) 완전히 로드되기 전에 양식을 제출할 수 있는 문제를 해결합니다. 또한 CMS 페이지의 기본값이 아닌 위치에서 블록을 사용할 때 null *에서 멤버 함수 isDisabled()에 대한*&#x200B;호출 오류가 수정됩니다.

이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48 릴리스에 추가되었습니다. 새로운 Adobe Commerce 버전 2.4.7 - 2.4.7-p4를 포함하도록 QPT 1.1.58 릴리스에서 업데이트되었습니다. 패치 ID는 MDVA-39305-V3입니다. 이 문제는 Adobe Commerce 버전 2.4.4, 2.4.5-p2 및 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4, 2.4.5-p2, 2.4.7

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4-p1 - 2.4.7-p4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

### 사례 I

1. 등록된 고객은 활성화된 [!DNL Google reCAPTCHA]을(를) 사용하여 로그인할 수 없습니다.
1. [!DNL Google reCAPTCHA]이(가) 완전히 로드되기 전에 양식을 제출할 수 있습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]** > **[!DNL Google reCAPTCHA Storefront]**(으)로 이동하여 ***[!DNL Google reCAPTCHA]***&#x200B;을(를) 사용하도록 설정합니다.
1. 프론트엔드로 가세요
1. 브라우저에서 **[!UICONTROL Developer Tool Console]** 열기

<u>예상 결과</u>:

콘솔에 CSP 경고가 없습니다.

<u>실제 결과</u>:

콘솔의 CSP 경고.

### 사례 II

CMS 페이지의 기본값이 아닌 위치에서 블록을 사용할 때 null *에서 멤버 함수 isDisabled()에 대한*&#x200B;호출 오류가 발생합니다.

<u>재현 단계</u>:

1. 아래 콘텐츠로 정적 블록을 만듭니다.

   ```
   {{block class="Magento\Newsletter\Block\Subscribe" name="home.form.subscribe"
   template="Magento_Newsletter::subscribe.phtml"}}
   ```

1. **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Add/Edit CMS page]** > **[!UICONTROL Content]**&#x200B;에서 CMS 페이지에 정적 블록을 추가합니다.
1. 페이지를 저장합니다.

<u>예상 결과</u>:

페이지가 오류 없이 로드됩니다.

<u>실제 결과</u>:

상점 첫 화면의 페이지에 500 오류가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).


