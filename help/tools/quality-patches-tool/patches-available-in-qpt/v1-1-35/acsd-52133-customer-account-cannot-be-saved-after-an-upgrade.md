---
title: 'ACSD-52133: 업그레이드 후 고객 계정을 저장할 수 없음'
description: 업그레이드 후 고객 계정을 저장할 수 없는 Adobe Commerce 문제를 해결하려면 ACSD-52133 패치를 적용합니다.
feature: Customers, Upgrade
role: Admin
exl-id: 4a0e6ed8-3e35-40ce-bb49-8ccfcde437a0
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-52133: 업그레이드 후 고객 계정을 저장할 수 없음

>[!NOTE]
>
>보안 패치 [APSB25-08](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08)과(와) 충돌하여 이 패치는 더 이상 사용되지 않습니다.

ACSD-52133 패치는 업그레이드 후 고객 계정을 저장할 수 없는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-52133입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

업그레이드 후에는 고객 계정을 저장할 수 없습니다.

<u>재현 단계</u>:

1. Adobe Commerce 버전 2.4.4를 설치합니다.
1. 고객을 만듭니다.
1. 고객이 이미 생성된 이전 버전의 2.4.4에서 Adobe Commerce을 2.4.6으로 업그레이드하십시오.
1. 암호화 키를 `env.php`에서 아래와 같이 설정합니다.

   `d337b914e91ff703b1e94ba4156aadf0`

1. `customer_entity` 테이블 아래의 고객에 대해 데이터베이스에 아래 값을 설정합니다.

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**(으)로 이동합니다.
1. 위의 값이 업데이트된 고객을 편집합니다.
1. **[!UICONTROL Save Customer]** 또는 **[!UICONTROL Save and Continue Edit]** 클릭

<u>예상 결과</u>:

고객이 오류 없이 정상적으로 저장되었습니다.

<u>실제 결과</u>:

* 고객 레코드가 저장되지 않습니다.
* 관리자에게 다음 오류 메시지가 표시됩니다. *고객을 저장하는 동안 문제가 발생했습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 관련 읽기

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대해 패치를 사용할 수 있는지 확인[
* Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
