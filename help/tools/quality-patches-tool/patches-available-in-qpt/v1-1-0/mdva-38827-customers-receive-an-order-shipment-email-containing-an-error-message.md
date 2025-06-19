---
title: 'MDVA-38827: 고객이 이메일을 통해 주문 배송 오류 수신'
description: MDVA-38827 패치는 다음과 같은 오류 메시지가 포함된 주문 배송 이메일을 고객이 받는 문제를 해결합니다. *죄송합니다. 이 콘텐츠를 생성하는 동안 오류가 발생했습니다.* 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38827입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ab522c9c-2983-4c2f-b341-4487bdbee34d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-38827: 고객이 이메일을 통해 주문 배송 오류 수신

MDVA-38827 패치를 사용하면 고객이 다음 오류 메시지가 포함된 주문 배송 전자 메일을 받는 문제가 해결됩니다. *죄송합니다. 이 콘텐츠를 생성하는 동안 오류가 발생했습니다*. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-38827입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.4.2-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객에게 이메일로 발송 알림 옵션을 선택하면 고객에게 다음과 같은 오류 메시지가 포함된 이메일을 받게 됩니다. *죄송합니다. 이 콘텐츠를 생성하는 동안 오류가 발생했습니다*.

<u>재현 단계</u>:

1. **마케팅** > **커뮤니케이션** > **전자 메일 템플릿**(으)로 이동한 다음 **새 템플릿 추가**&#x200B;를 선택합니다.
   * **Magento 판매** > **새 배송**&#x200B;을 선택합니다.
   * **템플릿 로드**&#x200B;를 클릭합니다.
   * 템플릿 이름(예: 핵심 전달 템플릿)을 추가하고 **저장**&#x200B;을 클릭합니다.
1. **스토어** > 설정 > **구성** > **판매** > **판매 전자 메일**(으)로 이동:
   * **배송 댓글**&#x200B;을 사용하도록 설정합니다.
   * 게스트용 메일 설명 전자 메일 서식 파일 및 메일 설명 전자 메일 서식 파일에서 **핵심 메일 서식 파일**(1단계의 &quot;서식 파일 이름 추가&quot; 부분 참조)을 선택합니다.
1. 주문하십시오. 관리 패널 > **판매** > **주문**(으)로 이동하여 **보기**&#x200B;를 클릭한 다음 주문을 배달합니다.
1. 주문 상태가 보류 중에서 처리로 변경됩니다.
1. 왼쪽 사이드바 메뉴에서 **배송**&#x200B;을 클릭한 다음 **보기**&#x200B;를 클릭하여 주문을 확인합니다.
1. **배송 내역** 아래의 **댓글 텍스트**&#x200B;에 댓글을 추가하고 **이메일로 고객에게 알림** 확인란을 선택합니다.
1. **댓글 제출**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

배송 의견이 포함된 판매 이메일이 생성됩니다.

<u>실제 결과</u>:

전자 메일에 다음 오류 메시지가 수신됩니다. *죄송합니다. 이 콘텐츠를 생성하는 동안 오류가 발생했습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
