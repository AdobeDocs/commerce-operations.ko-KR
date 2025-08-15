---
title: 'ACSD-61622: [!DNL FedEx] 계정 특정 요금이 REST API 응답에 없습니다.'
description: ACSD-61622 패치를 적용하여  [!DNL FedEx] 계정별 비율이 REST API 응답에서 누락된 Adobe Commerce 문제를 해결합니다.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 59e33dc4-3f9b-4590-95b6-e98c77e750ee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-61622: [!DNL FedEx] 계정 특정 요금이 REST API 응답에 없습니다.

ACSD-61622 패치는 REST API 응답에서 [!DNL FedEx's] 계정별 비율이 누락된 문제를 해결합니다. `ACCOUNT` 속도 요청 유형을 Adobe Commerce에서 [!DNL FedEx]&#x200B;(으)로 보낸 REST API 요청에 추가하며, 이는 SOAP API 응답과 유사한 응답을 반환합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-61622입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1 - 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

REST API 응답에서 [!DNL FedEx's] 계정별 요금이 누락되었습니다.

<u>재현 단계</u>:

1. 깨끗한 Adobe Commerce 인스턴스를 설치합니다.
1. 무게가 5파운드에 불과한 간단한 제품을 만들 수 있습니다.
1. REST API에 대해 [!DNL FedEx]을(를) 구성합니다.
1. [!DNL FedEx] 전달 메서드를 사용하도록 설정하고 캐시를 지웁니다.
1. 로그 파일 관찰 시작: `var/log/shipping.log`
1. 간단한 제품을 장바구니에 추가하고 체크아웃 시 배송 페이지로 이동합니다. 고객 데이터의 예:

   * 우편 번호: 58601
   * 이름: John Do
   * 주소: 196 Eulalia Burg
   * 국가: 미국
   * 주: 노스다코타
   * 전화 번호: 187-563-3627

<u>예상 결과</u>:

SOAP API 응답과 유사한 `PAYOR_ACCOUNT_PACKAGE` 비율은 REST API 응답에서 사용할 수 있습니다.

<u>실제 결과</u>:

응답에서 `PAYOR_LIST_PACKAGE` 비율만 사용할 수 있습니다. 즉, [!DNL FedEx]에서 협상된(계정) 비율이 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
