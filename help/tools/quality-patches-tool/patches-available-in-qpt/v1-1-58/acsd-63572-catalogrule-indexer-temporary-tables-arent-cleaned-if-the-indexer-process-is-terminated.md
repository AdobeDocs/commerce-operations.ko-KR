---
title: 'ACSD-63572: 인덱서 프로세스가 종료되면 ''catalogrule'' 인덱서 임시 테이블이 정리되지 않음'
description: ACSD-63572 패치를 적용하여 [!UICONTROL CLI]의 시스템 업그레이드 또는 중지로 인해 프로세스가 종료될 때 인덱서 테이블이 정리되지 않는 Adobe Commerce 문제를 해결합니다.
feature: System
Role: Admin, Developers
exl-id: 1cab7058-ca20-4d43-bfca-9b0e3ad35f42
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-63572: 인덱서 프로세스가 종료되면 인덱서 임시 테이블 `catalogrule`개가 정리되지 않습니다.

ACSD-63572 패치는 시스템/업그레이드 또는 [!UICONTROL CLI]의 중지로 인해 프로세스가 종료되었을 때 인덱서 임시 테이블이 정리되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63572입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

시스템 업그레이드 또는 [!UICONTROL CLI]의 중지로 인해 프로세스가 종료되면 인덱서 임시 테이블이 정리되지 않습니다.

<u>재현 단계</u>:

1. [!UICONTROL CLI] 열기
1. 명령 실행: `bin/magento indexer:reindex catalogrule_rule`.
1. `^C` 사용을 완료하기 전에 프로세스를 취소하십시오.
1. `bin/magento indexer:reset catalogrule_rule catalogrule_product`을(를) 사용하여 인덱서를 다시 설정합니다.
1. 이전 단계를 여러 번 반복합니다.
1. 데이터베이스에 생성된 다음 임시 테이블을 확인합니다.

   ```
   catalogrule_product__temp*
   catalogrule_product_price__temp*
   ```

<u>예상 결과</u>:

이전 임시 테이블은 필요하지 않으면 삭제됩니다.

<u>실제 결과</u>:

이전 임시 테이블은 제거되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
