---
title: 'ACSD-56226: 읽기 쿼리가 ''synchronous_replication''이 활성화된 오래된 데이터를 반환함'
description: ACSD-56226 패치를 적용하여 Cloud의 슬레이브 연결에 대해 'synchronous_replication' 플래그가 활성화되어 있을 때 READ 쿼리가 오래된 데이터를 반환하는 Adobe Commerce 문제를 수정합니다.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: a45cef14b7b37f1112d2ef82adf29b09d63b8e2b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# ACSD-56226: READ 쿼리가 `synchronous_replication`이(가) 활성화된 오래된 데이터를 반환합니다.

ACSD-56226 패치는 클라우드에서 슬레이브 연결에 대해 `synchronous_replication` 플래그가 활성화되어 있을 때 READ 쿼리가 오래된 데이터를 반환하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-56226입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`synchronous_replication` 플래그를 사용하도록 설정하면 READ 쿼리가 오래된 데이터를 반환합니다. 이로 인해 슬레이브 연결이 비활성화되어 데이터베이스가 오버로드됩니다.

<u>재현 단계</u>:

1. 클라우드 인프라의 Adobe Commerce에 있는 환경 변수에서 `MYSQL_USE_SLAVE_CONNECTION`을(를) *true*(으)로 설정합니다.
1. `.magento.env.yaml`을(를) `synchronous_replication`false *(으)로 설정하려면*&#x200B;에 다음 구성을 추가하십시오.

   ```
   DATABASE_CONFIGURATION:
     _merge: true
     slave_connection:
       default:
         synchronous_replication: false
   ```

1. 재배포하고 로그인, 장바구니에 추가 또는 주문과 같은 프론트엔드 작업을 수행합니다.

<u>예상 결과</u>:

`synchronous_replication`이(가) *false*(으)로 설정되어 있으면 슬레이브 연결이 사용 가능한 상태로 유지됩니다.

<u>실제 결과</u>:

`synchronous_replication`이(가) *false*(으)로 설정되어 있으면 슬레이브 연결이 비활성화되어 데이터베이스 오버로드가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
