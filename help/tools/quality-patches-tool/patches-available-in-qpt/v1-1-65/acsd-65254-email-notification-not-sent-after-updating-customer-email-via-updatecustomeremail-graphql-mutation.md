---
title: 'ACSD-65254: updateCustomerEmail [!DNL GraphQL] mutation을 통해 고객 이메일을 업데이트한 후 이메일 알림이 전송되지 않음'
description: updateCustomerEmail [!DNL GraphQL] mutation을 사용하여 계정의 이메일 주소를 성공적으로 업데이트한 후 고객에게 이메일 알림이 전송되지 않았던 Adobe Commerce 문제를 해결하려면 ACSD-65254 패치를 적용합니다.
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: a97daceb-98f6-4bb8-9847-692af700c0fd
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-65254: `updateCustomerEmail` [!DNL GraphQL] 돌연변이를 통해 고객 이메일을 업데이트한 후 이메일 알림이 전송되지 않음

ACSD-65254 패치는 `updateCustomerEmail` [!DNL GraphQL] 돌연변이를 사용하여 계정의 이메일 주소를 업데이트한 후 고객에게 이메일 알림이 전송되지 않은 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-65254입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`updateCustomerEmail` [!DNL GraphQL] 돌연변이를 사용하여 이메일 주소를 업데이트한 후 고객에게 이메일 알림이 전송되지 않았습니다.

<u>재현 단계</u>:

1. 아래 돌연변이를 사용하여 사용자 생성:

   ```
   mutation {
   	    createCustomer(
   		    input: {
   			    firstname: "Test"
   			    lastname: "User"
   			    email: "test@test.com"
   			    password: "Admin@123"
   			    is_subscribed: true
   		    }
   	    ) {
   		    customer {
   			    created_at
   		    }
   	    }
   }
   ```

1. 이전에 만든 사용자에 대한 토큰을 생성하고 전달자 토큰으로 사용합니다.

   ```
   mutation {
   generateCustomerToken(email: "test@test.com", password: "Admin@123") {
   	    token
   }
   }
   ```

1. 마지막으로 만든 전달자 토큰을 사용하여 이전에 만든 사용자에 대한 이메일을 업데이트해 보십시오.

   ```
   mutation {
   	    updateCustomerEmail(email: "test+updated@test.com", password: "Admin@123") {
   		    customer {
   			    email
   		    }
   	    }
   }
   ```

<u>예상 결과</u>:

고객은 계정의 이메일 주소를 업데이트한 후 이메일 알림을 받아야 합니다.

<u>실제 결과</u>:

새 주소로 구독 이메일만 전송됩니다. 이메일 주소 변경에 대한 확인 이메일은 전송되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
