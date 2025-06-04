---
title: 'ACSD-65100: [!UICONTROL Media Gallery Image Optimization] 구성에서 [!UICONTROL Maximum Width] 및 [!UICONTROL Maximum Height] 값을 제거하면 오류가 발생합니다'
description: ACSD-65100 패치를 적용하여 [!UICONTROL Media Gallery Image Optimization] 구성에서 [!UICONTROL Maximum Width] 및 [!UICONTROL Maximum Height] 값을 제거하면 이미지 최적화 프로세스 중에 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Media
role: Admin, Developer
source-git-commit: 97ffcd84b760962e1ad7290343f81860ca6568c7
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# ACSD-65100: [!UICONTROL Media Gallery Image Optimization] 구성에서 [!UICONTROL Maximum Width] 및 [!UICONTROL Maximum Height] 값을 제거하면 오류가 발생합니다

ACSD-65100 패치는 **[!UICONTROL Media Gallery Image Optimization]** 구성에서 **[!UICONTROL Maximum Width]** 및 **[!UICONTROL Maximum Height]** 값을 제거하면 이미지 최적화 프로세스 중에 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-65100입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-P5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Media Gallery Image Optimization]** 구성에서 **[!UICONTROL Maximum Width]** 및 **[!UICONTROL Maximum Height]**&#x200B;의 값을 제거하는 동안 이미지 최적화 프로세스 중에 오류가 발생했습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery Image Optimization]**(으)로 이동합니다.
1. **[!UICONTROL Maximum Width]** 및 **[!UICONTROL Maximum Height]**&#x200B;의 값을 제거합니다.
1. 구성 캐시를 정리합니다.
1. **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**(으)로 이동합니다.
1. 편집할 페이지를 엽니다.
1. 컨텐츠 영역에서:
   1. **[!UICONTROL Add Layout]** > **[!UICONTROL Row]**&#x200B;을(를) 선택합니다.
   1. **[!UICONTROL Add Elements]** > **[!UICONTROL Text]**&#x200B;을(를) 선택합니다.
   1. WYSIWYG 편집기에서 **[!UICONTROL Add Image]**&#x200B;을(를) 클릭합니다.
   1. 이미지를 업로드하고 **[!UICONTROL Add Selected]**&#x200B;을(를) 선택합니다.
1. `var/log/exception.log` 파일을 확인하십시오.

<u>예상 결과</u>:

오류 없음.

<u>실제 결과</u>:

다음과 유사한 오류가 기록됩니다.

```
report.ERROR: InvalidArgumentException: Invalid image dimensions. in /var/www/html/vendor/magento/framework/Image/Adapter/AbstractAdapter.php:630
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
