---
title: 'ACSD-64532: *false*로 설정된 ENV 변수는 부울 *FALSE* 대신 문자열 *false*로 처리됩니다.'
description: ACSD-64532 패치를 적용하여 'ENV' 변수가 *false*로 설정된 'BOOLEAN' *FALSE* 대신 문자열 *false*로 처리되는 Adobe Commerce 문제를 해결합니다.
feature: Variables
role: Admin, Developer
source-git-commit: 603b4f92ab3bbf4702d5373bd02dfdd770f57d5b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# ACSD-64532: &quot;false&quot;로 설정된 ENV 변수는 부울 FALSE 대신 문자열 &quot;false&quot;로 처리됩니다.

ACSD-64532 패치는 *false*(으)로 설정된 `ENV` 변수가 `BOOLEAN` *FALSE* 대신 문자열 *false*(으)로 처리되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-64532입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
Adobe Commerce(모든 배포 방법) 2.4.6-p8

**Adobe Commerce 버전과 호환:**
Adobe Commerce(모든 배포 방법) 2.4.6-p2 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*false*(으)로 설정된 `ENV` 변수가 `BOOLEAN` *FALSE* 대신 문자열 *false*(으)로 처리됩니다.

<u>재현 단계</u>:
1. 값이 *false*&#x200B;인 `env:MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK`을(를) 클라우드 인프라의 Adobe Commerce에 있는 환경 변수에 추가하십시오.
1. 재배포를 기다립니다.
1. 값을 확인하는 스크립트를 실행합니다.

   ```php
   <?php
   require '../app/bootstrap.php';
   $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
   $objectManager = $bootstrap->getObjectManager();
   $deploymentConfig = $objectManager->get('Magento\Framework\App\DeploymentConfig');
   $useAppLock = $deploymentConfig->get('indexer/use_application_lock');
   
   var_dump($useAppLock);
   
   $configParsedValue = $deploymentConfig->get('indexer/use_application_lock') ?: false;
   
   var_dump($configParsedValue); 
   ```

<u>예상 결과</u>:
`isUseApplicationLock()` 메서드의 결과인 `$configParsedValue`은(는) `\Magento\Indexer\Model\Mview\View\State::getStatus()` 메서드 내에서 올바르게 해석되려면 음수 값을 반환해야 합니다.

<u>실제 결과</u>:
`$configParsedValue`의 값은 *`string(5) false`*&#x200B;입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.
* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
