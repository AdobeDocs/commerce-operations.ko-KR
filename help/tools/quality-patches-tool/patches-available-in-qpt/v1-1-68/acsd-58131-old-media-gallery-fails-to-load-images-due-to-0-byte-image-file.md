---
title: 'ACSD-58131: 이전 미디어 갤러리가 0바이트 이미지 파일로 인해 이미지를 로드하지 못함'
description: ACSD-58131 패치를 적용하여 디렉터리에 0바이트 이미지가 있을 때 이전 미디어 갤러리에서 이미지를 렌더링하지 못하는 Adobe Commerce 문제를 해결합니다.
feature: Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: b09749a1e56ab6a7b613135ca252fd69757669d0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-58131: 이전 미디어 갤러리가 0바이트 이미지 파일로 인해 이미지를 로드하지 못함

ACSD-58131 패치는 디렉터리에 0바이트 이미지가 있을 때 이전 미디어 갤러리에서 이미지를 렌더링하지 못하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-58131입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

0바이트 이미지가 미디어 갤러리 디렉터리에 배치되면 이전 미디어 갤러리는 이미지를 렌더링하지 못합니다. 업데이트된 시스템은 이제 잘못된 0바이트 파일을 건너뛰고, 올바른 이미지를 예상대로 표시하고, 잘못된 각 파일에 대한 경고를 기록합니다.

```
[2024-05-02T14:00:39.616459+00:00] report.WARNING: The image empty2.jpg is invalid and cannot be displayed in the gallery. [] []
```

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]**(으)로 이동합니다.
1. **[!UICONTROL Enable Old Media Gallery]**&#x200B;을(를) *예*(으)로 설정합니다.
1. `pub/media/wysiwyg` 디렉터리에 이미지 몇 개를 배치합니다.
1. `touch pub/media/wysiwyg/empty_image.png`을(를) 사용하여 동일한 디렉터리에 0바이트 이미지를 만듭니다.
1. 콘텐츠(예: CMS 블록) 아래에 있는 페이지 빌더를 통해 `wysiwyg` 디렉터리의 이미지를 추가합니다.
   1. 새 블록을 만듭니다. **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Blocks]**(으)로 이동한 다음 **[!UICONTROL Add New Block]**&#x200B;을(를) 클릭합니다.
   1. 페이지 빌더를 사용하여 콘텐츠 섹션을 편집합니다.
   1. **[!UICONTROL Layout]**&#x200B;에서 새 **[!UICONTROL Row]**&#x200B;을(를) 스테이지로 드래그합니다.
   1. **[!UICONTROL Media]**&#x200B;을(를) 확장하고 **[!UICONTROL Image]** 자리 표시자를 행으로 드래그합니다.
   1. **[!UICONTROL Select from Gallery]**&#x200B;을(를) 클릭합니다.
   1. 기본적으로 선택되지 않은 경우 `wysiwyg` 디렉터리를 선택하십시오.

<u>예상 결과</u>:

미디어 갤러리는 0바이트 이미지(또는 다른 파일)가 있는 경우에도 계속 작동합니다.

<u>실제 결과</u>:

`wysiwyg`에 로그인한 중대 오류로 인해 미디어 갤러리가 `var/log/system.log` 디렉터리에서 이미지를 로드하지 못했습니다.

```
[2024-03-22T05:00:55.100934+00:00] report.CRITICAL: Exception: Notice: getimagesizefromstring(): Error reading from ! in /app/project/vendor/magento/module-cms/Model/Wysiwyg/Images/Storage.php on line 426 in /app/project/vendor/magento/framework/App/ErrorHandler.php:62
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
