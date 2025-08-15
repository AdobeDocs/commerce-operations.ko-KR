---
title: 'ACSD-67039: rp_token 시스템 특성 유효성 검사로 인해 고객 레코드가 저장되지 않았습니다.'
description: ACSD-67039 패치를 적용하여 인코딩 분음 부호로 인해 rp_token에 유효성 검사가 중단되는 Adobe Commerce 문제를 해결합니다.
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 231555e071ebc5edb36182f6b8d4f60acee4f61e
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-67039: `rp_token` 시스템 특성 유효성 검사로 인해 고객 레코드가 저장되지 않았습니다.

ACSD-67039 패치는 `rp_token` 시스템 특성의 유효성 검사로 인해 고객 레코드가 저장되지 않고 분음 부호 유효성 검사가 결과 고객 이메일에만 적용되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-67039입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p9

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6-p9 - 2.4.6-p11

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

인코딩 분음 부호로 인해 `rp_token`에 유효성 검사 오류가 발생하여 유효성 검사에서 제외됩니다. 분음 부호는 의도한 대로 이메일 주소에만 허용됩니다.

<u>재현 단계</u>:

1. Adobe Commerce 2.4.4 버전을 설치합니다.
1. 고객을 만듭니다.
1. 고객이 이미 생성된 2.4.4 이전 버전에서 Adobe Commerce을 버전 2.4.6으로 업그레이드합니다.
1. 암호화 키를 `env.php`(으)로 설정 =
   *d337b914e91ff703b1e94ba4156aadf0*
1. `customer_entity` 테이블 아래의 고객에 대해 데이터베이스에 아래 값을 설정합니다.
*`rp_token` = *incr4869*
*`rp_token_created_at` = *2021-04-29 20:06:14*
1. [관리] 패널에서 **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**(으)로 이동합니다.
1. 위의 값을 업데이트한 고객을 편집합니다.
1. **[!UICONTROL Save Customer]** 또는 **[!UICONTROL Save and Continue Edit]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

고객 값이 저장되었습니다.

<u>실제 결과</u>:

고객 레코드가 저장되지 않으며 관리자 사용자에게 고객을 저장하는 동안 *문제가 발생했습니다. 오류 메시지가 표시됩니다.*
`system.log`에 다음 오류가 있습니다.

```
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko)

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
