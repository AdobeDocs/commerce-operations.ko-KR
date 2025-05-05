---
title: 'ACSD-48570: URL의 스토어 코드에서 관리자 재설정 암호 링크 문제 해결'
description: ACSD-48570 패치를 적용하여 [!UICONTROL Add Store Code to URLs] 구성이 활성화되었을 때 관리자 암호 재설정 링크를 통해 암호 재설정 페이지에 액세스할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Security, User Account
role: Admin, Developer
source-git-commit: a9d7f4f4c2f2e27ff9571de08bcec918b4605b03
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48570: URL의 스토어 코드에서 관리자 재설정 암호 링크 문제 해결

*[!UICONTROL Add Store Code to URLs]* 구성이 활성화되었을 때 관리자 암호 재설정 링크를 통해 암호 재설정 페이지에 액세스할 수 없었던 Adobe Commerce 문제를 해결하기 위한 ACSD-48570 패치입니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48570입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Add Store Code to URLs]** 설정을 사용하면 관리자 암호 재설정 기능이 제대로 작동하지 않습니다.
관리자 사용자가 암호 재설정을 요청하고 이메일의 복구 링크를 클릭하면 암호 재설정 양식으로 이동하지 않고 로그인 페이지로 리디렉션되거나 404 오류가 수신됩니다. 따라서 관리자는 수동 작업 없이 계정을 복구할 수 없습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL URL Options]**&#x200B;에서 **[!UICONTROL Add Store Code to URLs]** 구성을 사용하도록 설정합니다.
1. [관리] 패널에서 로그아웃하고 [관리] 로그인 페이지에서 **[!UICONTROL Forgot your password?]** 링크를 클릭합니다.
1. 관리자 전자 메일을 입력하고 CAPTCHA를 전달하고 **[!UICONTROL Retrieve Password]**&#x200B;을(를) 클릭합니다.
1. 암호 재설정 이메일을 열고 암호 복구 링크를 클릭합니다.

<u>예상 결과</u>:

암호 재설정 양식이 표시됩니다.

<u>실제 결과</u>:

암호 재설정 양식 대신 로그인 페이지 또는 404 오류 페이지가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
