---
title: 'AC-14985: TLS를 사용하여 SMTP 전자 메일을 전송할 때 오류 발생'
description: AC-14985 패치를 적용하여 TLS(전송 계층 보안)를 사용하여 SMTP(Simple Mail Transfer Protocol) 이메일을 보낼 때 오류가 발생하는 Adobe Commerce 문제를 수정합니다.
feature: Configuration
role: Admin, Developer
type: Troubleshooting
exl-id: 98d91421-ebfd-4414-ade3-f25d29541874
source-git-commit: 515e6d1f00c910455a2ffddf70c4a450184e7e81
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# AC-14985: TLS를 사용하여 SMTP 전자 메일을 전송할 때 오류 발생

AC-14985 패치는 TLS(전송 계층 보안)를 사용하여 SMTP(Simple Mail Transfer Protocol) 이메일을 보낼 때 오류가 발생하는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 AC-14985입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

TLS가 활성화된 SMTP를 통해 전자 메일을 전송할 때 오류가 발생합니다.

<u>재현 단계</u>:

1. 다음과 같이 SMTP 구성을 설정합니다.
* 전송: SMTP
* 호스트: url.to.smtp.host
* 포트: 587
* SSL: TLS

<u>예상 결과</u>:

이메일이 오류 없이 정상적으로 전송되었습니다.

<u>실제 결과</u>:

다음 오류가 나타납니다.

```
error:1408F10B:SSL routines:ssl3_get_record:wrong version number [] []
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
