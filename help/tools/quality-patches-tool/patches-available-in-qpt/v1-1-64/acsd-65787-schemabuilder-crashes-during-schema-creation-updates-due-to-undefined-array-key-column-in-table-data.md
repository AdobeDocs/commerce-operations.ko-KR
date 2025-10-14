---
title: 'ACSD-65787: 테이블 데이터에 정의되지 않은 배열 키 "column" 때문에 스키마 생성 또는 업데이트 중 SchemaBuilder가 충돌합니다'
description: ACSD-65787 패치를 적용하여 테이블 데이터를 처리할 때 정의되지 않은 배열 키 "열"로 인해 스키마 생성 또는 업데이트 중에 SchemaBuilder 클래스가 충돌하는 Adobe Commerce 문제를 해결합니다.
feature: Backend Development, Deploy
role: Admin, Developer
exl-id: c01d1799-13fe-4657-a480-698efbe45a30
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-65787: 테이블 데이터에 정의되지 않은 배열 키 &quot;column&quot; 때문에 스키마 생성 또는 업데이트 중 `SchemaBuilder`이(가) 충돌합니다.

ACSD-65787 패치는 테이블 데이터를 처리할 때 정의되지 않은 배열 키 &quot;열&quot;로 인해 스키마를 만들거나 업데이트하는 동안 `SchemaBuilder` 클래스가 충돌하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-65787입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

테이블 데이터를 처리할 때 정의되지 않은 배열 키 &quot;column&quot; 때문에 스키마를 만들거나 업데이트하는 동안 `SchemaBuilder` 클래스가 충돌합니다.

<u>재현 단계</u>:

1. 다음 명령을 실행합니다.

```
bin/magento setup:upgrade
```

<u>예상 결과</u>:

오류 없음.

<u>실제 결과</u>:

```
Error "Warning: Undefined array key "column" in SchemaBuilder.php on line 90
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
