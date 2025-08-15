---
title: 'ACSD-66093: 게스트 고객 이름 필드에서 잘못된 주문 이메일을 유발하는 이메일 입력을 허용합니다.'
description: ACSD-66093 패치를 적용하여 게스트 고객 **[!UICONTROL First Name]** 및 **[!UICONTROL Last Name]** 필드에 이메일 주소를 입력하고 잘못된 주문 확인 이메일을 보낼 수 있는 Adobe Commerce 문제를 해결합니다.
feature: Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 30790492-330e-4810-8069-fce87b40ebb2
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-66093: 게스트 고객 이름 필드에서 잘못된 주문 이메일을 유발하는 이메일 입력을 허용합니다.

ACSD-66093 패치는 게스트 고객의 **[!UICONTROL First Name]** 및 **[!UICONTROL Last Name]** 필드에 이메일 주소를 입력할 수 있어 잘못된 주문 확인 이메일이 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-66093입니다. 이 문제는 Adobe Commerce 2.4.8에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p11

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

게스트 고객의 **[!UICONTROL First Name]** 및 **[!UICONTROL Last Name]** 필드에 전자 메일 주소를 입력할 수 있으므로 주문 확인 전자 메일이 잘못되었습니다.

<u>재현 단계</u>:

1. 장바구니에 제품을 게스트 고객으로 추가합니다.
2. 체크아웃으로 이동합니다.
3. &quot;test1@gmail.co&quot;으로 이메일 주소를 입력합니다.
4. **[!UICONTROL First Name]**&#x200B;을(를) &quot;<test2@gmail.co>&quot;(으)로 채웁니다.
5. **[!UICONTROL Last Name]**&#x200B;을(를) &quot;<test3@gmail.co>&quot;(으)로 채웁니다.
6. 다른 필수 필드를 채웁니다.
7. 주문.

<u>예상 결과</u>:

**[!UICONTROL First Name]**&#x200B;이름이 잘못된 것처럼 **[!UICONTROL Last Name]** 및 *필드가 올바르지 않음을 나타내는 유효성 검사 메시지가 표시됩니다. 성( )이 올바르지 않습니다.*&#x200B;과(와) 순서를 지정하면 안 됩니다.

<u>실제 결과</u>:

주문이 완료되었습니다.
**[!UICONTROL First Name]** 및 **[!UICONTROL Last Name]** 필드가 입력한 대로 저장됩니다.
주문 확인 이메일은 test1@gmail.co, test2@gmail.co 및 test3@gmail.co의 세 가지 이메일 모두로 전송됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
