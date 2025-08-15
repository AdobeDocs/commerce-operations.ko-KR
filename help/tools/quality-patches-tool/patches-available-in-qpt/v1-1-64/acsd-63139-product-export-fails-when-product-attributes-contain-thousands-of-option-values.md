---
title: 'ACSD-63139: 제품 속성에 수천 개의 옵션 값이 포함된 경우 제품 내보내기가 실패합니다'
description: ACSD-63139 패치를 적용하여 제품 속성에 수천 개의 옵션 값이 포함된 경우 제품 내보내기가 실패하는 Adobe Commerce 문제를 해결합니다.
feature: Data Import/Export
role: Admin, Developer
exl-id: 785907dc-aa3f-49e2-bd52-c3afe4393456
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63139: 제품 속성에 수천 개의 옵션 값이 포함된 경우 제품 내보내기가 실패합니다

ACSD-63139 패치는 제품 속성에 수천 개의 옵션 값이 포함된 경우 제품 내보내기가 실패하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-63139입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p10

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 속성에 수천 개의 옵션 값이 포함되어 있으면 제품 내보내기가 실패합니다.

<u>재현 단계</u>:

1. B2B 모듈로 Adobe Commerce을 설치합니다.
1. 다음을 사용하여 큰 데이터베이스 덤프 가져오기:
   &#x200B;- 7,000개 제품
   &#x200B;- ~450개 제품 특성
   &#x200B;- 일부 속성에 100개 이상의 옵션 포함
1. 다음 명령을 실행하여 cron 을 설치합니다(아직 설치되지 않은 경우).

   ```
   bin/magento cron:install
   ```

1. [!DNL RabbitMQ]필수 구성 요소[[!DNL RabbitMQ] 의 지침에 따라 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/rabbitmq)을(를) 구성합니다.
1. `php.ini` 파일을 열고 메모리 제한을 4G로 설정하고 PHP 서비스를 다시 시작합니다.
1. 관리 패널에서 **[!UICONTROL System]** > *[!UICONTROL Data Transfer]* > **[!UICONTROL Export]**(으)로 이동합니다.
1. *[!UICONTROL Export Settings]* 섹션에서 **[!UICONTROL Entity Type]**&#x200B;을(를) *제품*(으)로 설정하고 맨 아래로 스크롤한 다음 **[!UICONTROL Continue]**&#x200B;을(를) 클릭합니다.
1. 다음 명령을 실행하여 내보내기 프로세서를 시작합니다.

   ```
   bin/magento queue:consumers:start exportProcessor --max-messages=1
   ```

<u>예상 결과</u>:

제품 내보내기를 성공적으로 완료해야 합니다.

<u>실제 결과</u>:

제품 내보내기 프로세스가 실패하고 다음과 같은 치명적인 오류가 반환됩니다.

```
Fatal error: Allowed memory size of 4294967296 bytes exhausted (tried to allocate 12288 bytes) in /var/www/html/app/code/Magento/Catalog/Model/ResourceModel/Product/Collection.php on line 597
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
