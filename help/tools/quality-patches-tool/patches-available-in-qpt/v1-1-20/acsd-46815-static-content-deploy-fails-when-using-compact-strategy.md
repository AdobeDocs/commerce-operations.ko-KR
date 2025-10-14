---
title: 'ACSD-46815: 컴팩트 전략을 사용하여 정적 콘텐츠 배포가 실패합니다'
description: ACSD-46815 패치를 적용하여 컴팩트 전략을 사용할 때 정적 콘텐츠 배포가 실패하는 Adobe Commerce 문제를 해결합니다.
feature: Deploy, Page Content, SCD
role: Admin
exl-id: 66941a83-daf8-4bb2-a575-b615e1c5dc7c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-46815: 컴팩트 전략을 사용할 때 정적 콘텐츠 배포가 실패합니다

ACSD-46815 패치는 컴팩트 전략을 사용할 때 정적 콘텐츠 배포가 실패하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-46815입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

소규모 전략으로 배포할 때 정적 콘텐츠 배포가 실패합니다.

<u>재현 단계</u>:

1. 다음 명령을 실행하여 간단한 전략으로 정적 콘텐츠를 배포합니다.

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>예상 결과</u>:

정적 콘텐츠 배포가 오류 없이 완료되었습니다.

<u>실제 결과</u>:

간단한 전략으로 정적 콘텐츠 배포에 실패합니다. 배포 프로세스 중에 다음 오류가 발생했습니다. */app/pub/static/adminhtml/Magento/base/default/의 내용입니다./node_modules/@spectrum-css/vars/dist/spectrum-global.css 파일을 읽을 수 없습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
