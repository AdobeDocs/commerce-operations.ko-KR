---
title: 'ACSD-65848: 관리자의 범주 로드 속도가 매우 느립니다.'
description: ACSD-65848 패치를 적용하여 카테고리의 총 제품 수가 하위 선택을 사용하여 계산되어 카테고리 로드 시간이 지연되는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a614c40a1c0134a0528b74cbd434e7ca96c933a
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# ACSD-65848: 관리자의 범주 로드 속도가 매우 느립니다.

ACSD-65848 패치는 하위 선택을 사용하여 범주의 총 제품 수가 계산되었고 이로 인해 범주 로드 시간이 지연되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-65848입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

로드 시 관리자 범주 보기/편집 페이지에 상당한 지연이 발생합니다. 지연은 하위 선택 쿼리에 의존하는 범주의 총 제품 수를 계산하는 데 사용되는 메서드에 의해 발생합니다. 대신 조인을 사용하도록 이 논리를 리팩터링하면 성능이 향상되고 로드 시간이 줄어듭니다.

<u>재현 단계</u>:

1. 버전 2.4.8을 사용하여 새 Adobe Commerce Cloud 인스턴스를 만듭니다.
1. 2,500개의 카테고리와 최소 10,000개의 제품을 만들 수 있습니다.
   1. 프로필을 편집할 수 있도록 `setup/performance-toolkit` 디렉터리를 `./var`에 복사합니다.
   1. `small.xml` 프로필을 열고 2,500개의 범주와 250,000개의 제품을 포함하도록 업데이트하십시오(판매자의 설정에 맞게).
   1. 다음 명령을 실행하여 고정장치를 생성합니다.

      ```bash
      bin/magento 
      setup:performance:generate-fixtures var/setup/performance-toolkit/profiles/ce/small.xml
      ```

1. 제품 및 카테고리가 만들어지면 모든 카테고리가 앵커로 설정되었는지 확인합니다. 이 SQL 쿼리 실행:

   ```sql
   UPDATE catalog_category_entity_int 
   SET value = 1 
   WHERE attribute_id = (
   SELECT attribute_id 
   FROM eav_attribute 
   WHERE attribute_code = 'is_anchor'
   );
   ```

1. 관리 패널에서 더 심층적인 범주 구조를 만듭니다.
   * 범주 2를 범주 1 아래로 이동하여 트리 깊숙이 중첩합니다.
1. 다음과 같은 URL을 사용하여 관리 패널에서 카테고리 페이지를 열어 보십시오.
   ```/admin/catalog/category/edit/id/xx/```

<u>예상 결과</u>:

각 카테고리 페이지는 몇 초 내에 첫 번째 시도에서 열립니다.

<u>실제 결과</u>:

카테고리 페이지를 여는 데 1분 이상 걸립니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
