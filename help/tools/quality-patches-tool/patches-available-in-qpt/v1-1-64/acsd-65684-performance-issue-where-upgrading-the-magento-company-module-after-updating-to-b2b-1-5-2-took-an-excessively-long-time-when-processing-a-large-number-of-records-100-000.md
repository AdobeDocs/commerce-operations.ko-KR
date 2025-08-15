---
title: 'ACSD-65684: B2B 1.5.2에서 Magento_Company를 업그레이드하는 작업은 company_structure에 100,000개 이상의 레코드가 있을 만큼 느립니다.'
description: B2B 1.5.2에서 Magento_Company 모듈을 업그레이드하는 경우 company_structure 테이블의 많은 레코드(~100,000+)를 처리하므로 시간이 너무 오래 걸리는 Adobe Commerce 문제를 해결하려면 ACSD-65684 패치를 적용합니다.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: 1b45ebe4-4fb4-4fb5-b107-a2d44ec784e0
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-65684: `Magento_Company` 1.5.2의 [!DNL B2B] 업그레이드가 느려지고 `company_structure`에 100,000개 이상의 레코드가 있습니다.

ACSD-65684 패치는 `Magento_Company` 테이블에서 100,000개 이상의 레코드를 처리할 때 [!DNL B2B] 1.5.2의 `company_structure` 모듈을 업그레이드하는 데 시간이 너무 오래 걸리는 성능 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-65684입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce B2B(모든 배포 방법) 1.5.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce B2B(모든 배포 방법) 1.5.2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`Magento_Company` 테이블에서 100,000개 이상의 레코드를 처리할 때 [!DNL B2B] 1.5.2의 `company_structure` 모듈을 업그레이드하는 데 시간이 너무 오래 걸립니다.

<u>재현 단계</u>:

1. [!DNL B2B]&#x200B;(으)로 Adobe Commerce 2.4.7-p4를 설치합니다.
1. `company_structure` 테이블에 100,000개의 레코드를 추가합니다.
1. Adobe Commerce 2.4.7-p5 및 최신 [!DNL B2B] 모듈(1.5.2)로 업그레이드하십시오.
1. 패치 ACSD-65540을 적용합니다.
1. 실행:

```
bin/magento setup:upgrade
```

<u>예상 결과</u>:

`setup:upgrade`이(가) 적절한 시간 내에 완료됩니다.

<u>실제 결과</u>:

`setup:upgrade`을(를) 완료하는 데 시간이 너무 오래 걸립니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
