---
title: 'ACSD-56741: 사용자 지정 MySQL 트리거로 데이터베이스 설정 오류 문제 해결'
description: ACSD-56741 패치를 적용하여 인덱싱과 관련 없는 데이터베이스의 사용자 지정 MySQL 트리거 및  [!DNL MView] (으)로 인해 'setup:upgrade' 동안 null* 유형의 값에 대한 배열 오프셋에 액세스하려고 함*이라는 오류 메시지가 표시되는 Adobe Commerce 문제를 수정하십시오.
feature: Install
role: Admin, Developer
exl-id: 93a1c75f-8a45-49df-9fa4-6ba1234c822d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56741: 사용자 지정 MySQL 트리거로 데이터베이스 설정 오류 문제 해결

ACSD-56741 패치는 인덱싱과 [!DNL MView]과(와) 관련 없는 데이터베이스의 사용자 지정 MySQL 트리거로 인해 `setup:upgrade` 동안 null *형식의 값에 대한 배열 오프셋에 액세스하려고 시도한다는 오류 메시지*&#x200B;이(가) 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-56741입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

인덱싱과 [!DNL MView]과(와) 관련 없는 데이터베이스의 사용자 지정 MySQL 트리거로 인해 `setup:upgrade` 동안 null *형식의 값에 대한 배열 오프셋에 액세스하려고 시도한다는 오류 메시지*&#x200B;이(가) 나타납니다.

<u>재현 단계</u>:

1. `php bin/magento indexer:set-mode schedule` 실행.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. `php bin/magento c:f` 실행.
1. `php bin/magento setup:upgrade` 실행.

<u>예상 결과</u>:

설치 업그레이드가 오류 없이 완료됩니다.

<u>실제 결과</u>:

설치 업그레이드가 종료되고 다음 오류 메시지가 표시됩니다.

*경고: null* 형식의 값에 대한 배열 오프셋에 액세스하려고 합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
