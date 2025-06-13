---
title: 'MDVA-43824: "항목을 취소하지 않았습니다."라는 오류가 발생하여 주문 취소 작업이 실패했습니다.'
description: MDVA-43824 패치는 다음 오류로 인해 주문 취소 작업이 실패했던 문제를 해결합니다. *항목을 취소하지 않았습니다*. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43824입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Orders
role: Admin
exl-id: 8c2d15a0-2f53-4583-bdf2-86746f61160f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-43824: &quot;항목을 취소하지 않았습니다.&quot;라는 오류가 발생하여 주문 취소 작업이 실패했습니다.

MDVA-43824 패치는 다음 오류로 인해 주문 취소 작업이 실패했던 문제를 해결합니다. *항목을 취소하지 않았습니다*. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43824입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.6 - 2.3.7-p3, 2.4.1 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

로그인한 고객이 주문한 주문은 취소할 수 없습니다. 다음 오류로 인해 주문 취소 작업이 실패했습니다.

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>재현 단계</u>:

1. 판매 규칙을 생성합니다(쿠폰 유형은 &quot;특정 쿠폰&quot; 또는 &quot;쿠폰 없음&quot;).
1. 상점으로 이동하여 고객으로 로그인하고 장바구니에 제품을 추가합니다.
1. 장바구니로 이동하여 장바구니 가격 규칙에 &quot;특정 쿠폰&quot;이라는 쿠폰이 있는 경우 장바구니 가격 규칙을 적용합니다. 장바구니 가격 규칙을 성공적으로 적용해야 합니다.
1. 계산대로 가서 결제 수단을 가지고 주문하세요.
1. Commerce 관리자 > **판매** > **주문**(으)로 이동합니다.
1. 4단계에서 수행한 주문을 엽니다.
1. **취소** 단추를 클릭합니다.

<u>예상 결과</u>:

주문이 오류 없이 성공적으로 취소되었습니다.

<u>실제 결과</u>:

다음 오류로 인해 주문 취소 작업이 실패했습니다. *항목을 취소하지 않았습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
