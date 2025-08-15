---
title: 'ACSD-62212: [!UICONTROL Forgot Password] 전자 메일이 저장소 보기 언어로 번역되지 않음'
description: ACSD-62212 패치를 적용하여 *[!UICONTROL Forgot Password]* 전자 메일의 콘텐츠가 스토어 보기의 언어로 번역되지 않는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL
role: Admin, Developer
exl-id: 29e6f2fa-574f-4ab1-82f5-88e1eb1de83e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-62212: *[!UICONTROL Forgot Password]* 전자 메일이 저장소 보기 언어로 번역되지 않음

ACSD-62212 패치는 *[!UICONTROL Forgot Password]* 전자 메일의 콘텐츠가 스토어 보기 언어로 번역되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62212입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

등록된 저장소 보기가 아닌 저장소 보기에서 GraphQL을 통해 암호를 재설정하는 동안 암호 재설정 링크가 시작된 저장소 보기와 일치하지 않습니다.

<u>재현 단계</u>:

1. *[!UICONTROL Main Website Store]* 아래에 보조 저장소 보기를 만듭니다.
1. 보조 저장소 보기 범위에서 *[!UICONTROL Locale]*&#x200B;을(를) *[!UICONTROL French (France)]*(으)로 전환합니다.
1. 번역을 위한 프랑스어 언어 팩을 설치합니다.
1. 고객 계정을 만듭니다.
1. 보조 저장소 보기 코드와 함께 *store* 헤더에 다음 GraphQL 돌연변이를 사용하십시오.

   ```
   mutation {
       requestPasswordResetEmail(
           email: "test@gmail.com"
       )
   }
   ```

1. 이메일을 확인합니다.

<u>예상 결과</u>:

* 이메일 제목, 링크 및 콘텐츠의 언어는 스토어 보기 로케일과 일치합니다.
* 암호 재설정 요청은 요청의 스토어 헤더에 관계없이 고객의 계정이 실제로 등록된 스토어에서 발송됩니다.

<u>실제 결과</u>:

이메일에서 다음을 관찰할 수 있습니다.

* 암호 재설정 링크에는 &quot;기본&quot; 스토어 코드가 있습니다.
* 그 과목은 영어로 되어 있다.
* 내용은 프랑스어로 되어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
