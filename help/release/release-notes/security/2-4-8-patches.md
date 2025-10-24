---
title: Adobe Commerce 2.4.8 보안 패치 릴리스 노트
description: Adobe Commerce 버전 2.4.7의 보안 패치 릴리스에 포함된 보안 버그 수정, 보안 개선 사항 및 기타 보안 관련 업데이트에 대해 알아봅니다.
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: e625670e741c0669050ab758d4f87c5ca06fe3df
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Adobe Commerce 2.4.8 보안 패치 릴리스 노트

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p3

Adobe Commerce 2.4.8-p3 보안 릴리스는 이전 릴리스 2.4.8에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* ACP2E-3874에 대한 수정: 동일한 여러 항목을 주문한 경우 주문 세부 사항에 대한 REST API 응답에 `base_row_total` 및 `row_total` 특성에 대한 올바른 값이 포함되어 있습니다.

* AC-15446 수정: `Magento\Framework\Mail\EmailMessage`이(가) `getBodyText()`에서 존재하지 않는 `getTextBody()` 메서드를 호출하려고 시도하여 Magento 2.4.8-p2 및 `Symfony\Component\Mime\Message` 103.0.8-p2와의 호환성을 보장하는 `magento/framework`의 오류가 수정되었습니다.

{{oct-2025-backports}}

### 알려진 문제

#### 체크아웃 페이지가 static.min.js 및 mixins.min.js를 로드하지 못했습니다.

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.8-p2

Adobe Commerce 2.4.8-p2 보안 릴리스는 이전 릴리스 2.4.8에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html)을 참조하십시오.

{{b2b-patches}}

## 2.4.8-p1

Adobe Commerce 2.4.8-p1 보안 릴리스는 이전 릴리스 2.4.8에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

* **API 성능 향상**—이전 보안 패치 이후에 도입된 일괄 비동기 웹 API 끝점의 성능 저하를 해결합니다.<!-- AC-14078 -->

* **CMS 차단 액세스 수정**—머천다이징 전용 액세스와 같이 권한이 제한된 관리자가 [!UICONTROL CMS Blocks] 목록 페이지를 볼 수 없는 문제를 해결합니다.

  이전에는 이러한 사용자가 이전 보안 패치를 설치한 후 구성 매개 변수가 누락되어 오류가 발생했습니다.<!-- AC-14087 -->

* **쿠키 제한 호환성**—프레임워크에서 `MAX_NUM_COOKIES` 상수와 관련된 이전 버전과 호환되지 않는 변경 내용을 해결합니다. 이 업데이트는 예상되는 동작을 복원하고 쿠키 제한과 상호 작용하는 확장 또는 사용자 지정에 대한 호환성을 보장합니다.<!-- AC-14475 -->

* **비동기 작업**—이전 고객의 주문을 재정의하기 위한 제한된 비동기 작업입니다.<!-- AC-13917 -->

* **CVE-2025-47110에 대한 수정**—전자 메일 템플릿 취약점을 해결합니다.<!-- AC-14695 -->

* **VULN-31547에 대한 수정**—범주 표준 링크 취약성을 해결합니다.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

CVE-2025-47110 및 VULN-31547에 대한 수정 사항은 격리된 패치로도 사용할 수 있습니다. 자세한 내용은 [기술 자료 문서](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)를 참조하세요.

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2025-10-22 11:16:25 -->
