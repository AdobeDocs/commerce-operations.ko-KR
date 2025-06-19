---
title: 'ACSD-63244:  [!DNL Google Maps] 렌더링 및 콘솔 오류를 포함한 관리 패널 JavaScript 문제를 해결합니다.'
description: ACSD-63244 패치는 관리 패널에서  [!DNL Google Maps] 렌더링 및 되풀이되는 '발견되지 않은 유형' 오류와 관련된 문제를 포함하여 여러 JavaScript 문제를 수정합니다._each는 브라우저 콘솔에서 함수 오류가 아닙니다.
feature: Admin Workspace
role: Admin, Developer
exl-id: 1985c845-219e-4af4-8f70-62dd57722494
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-63244: [!DNL Google Maps] 렌더링 및 콘솔 오류를 포함한 관리 패널 JavaScript 문제를 해결합니다.

ACSD-63244 패치는 브라우저 콘솔에서 [!DNL Google Maps] 렌더링 및 `Uncaught TypeError: this._each is not a function` 반복 오류와 관련된 문제를 포함하여 관리 패널의 여러 JavaScript 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56에서 사용할 수 있습니다. 패치 ID는 ACSD-63244입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.4, 2.4.4-p9, 2.4.6-p7, 2.4.7

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

* `Uncaught TypeError: this._each is not a function` 오류가 브라우저 콘솔에 표시되어 관리 UI 기능을 중단합니다.
* JavaScript 오류로 인해 [!DNL Google Maps]이(가) 올바르게 렌더링되지 않습니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리 UI를 로드합니다.
1. 브라우저 콘솔을 열고 다음 스크립트를 실행합니다.

   ```
   Object.values([] || {}).forEach((function(e) {  
   e("dd")  
   }));  
   ```

<u>예상 결과</u>:

기본 JS 라이브러리에서 사용할 수 있는 JavaScript 함수는 오류 없이 올바르게 실행됩니다.

<u>실제 결과</u>:

브라우저 콘솔에 JavaScript 오류가 표시됩니다.

```
Uncaught TypeError: this._each is not a function
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
