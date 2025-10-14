---
title: 'ACSD-62485: 회사 생성 시 ''async.operations.all'' 소비자 작동 중지'
description: ACSD-62485 패치를 적용하여 B2B 회사가 생성되면 'async.operations.all' 소비자가 작동을 중지하는 Adobe Commerce 문제를 해결합니다.
feature: B2B, Companies
role: Admin, Developer
exl-id: 99d20555-fe55-4a04-a067-5a2b104811f5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-62485: 회사가 만들어지면 `async.operations.all` 소비자가 작동을 중지합니다.

ACSD-62485 패치는 B2B 회사가 만들어질 때 `async.operations.all` 소비자가 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-62485입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p7

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p7, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

소비자가 여전히 실행 중인 동안 B2B 회사가 비동기적으로 만들어지는 경우 `async.operations.all` 소비자가 메시지 처리를 중지합니다.

<u>필수 구성 요소</u>:

B2B 모듈이 설치되고 활성화됩니다.

<u>재현 단계</u>:

1. 두 개의 고객을 만듭니다.
1. 두 회사를 만들려면 REST 벌크 요청을 보내고 만들어진 고객을 회사 관리자로 할당합니다.
1. 다음 명령을 사용하여 소비자를 시작합니다.

   ``` bin/magento queue:consumer:start async.operations.all --max-messages=20000 ```

<u>예상 결과</u>:

소비자는 20,000개의 메시지를 처리하고 성공적으로 종료됩니다.

<u>실제 결과</u>:

소비자는 실행 즉시 작업을 중지합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
