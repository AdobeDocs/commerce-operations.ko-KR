---
title: 'ACSD-61534: bin/magento config:set을 사용하여 디자인 구성을 설정할 수 없으며 잠긴 값은 양식 조작을 통해 변경할 수 있습니다'
description: ACSD-61534 패치를 적용하여 'bin/magento config:set' 명령을 사용하여 디자인 구성을 설정할 수 없고 양식 조작을 통해 잠긴 값을 변경할 수 있는 Adobe Commerce 문제를 해결합니다.
feature: Configuration
role: Admin, Developer
exl-id: 5bba3f05-e017-42b2-8a89-5471afb84ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534: `bin/magento config:set`을(를) 사용하여 디자인 구성을 설정할 수 없으며 잠긴 값은 양식 조작을 통해 변경할 수 있습니다.

ACSD-61534 패치는 `bin/magento config:set` 명령을 사용하여 디자인 구성을 설정할 수 없고 잠긴 값은 양식 조작을 통해 변경할 수 있는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-61534입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

디자인 구성은 `bin/magento config:set` 명령을 사용하여 설정할 수 없으며, 잠긴 값은 양식 조작을 통해 변경할 수 있습니다. 이 패치를 사용하면 명령줄 도구(CLI)에서 `--lock-env` 또는 `--lock-conf`(으)로 설정된 잠긴 값을 업데이트할 수 없습니다.

<u>재현 단계</u>:

1. `CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES`과(와) 같은 클라우드 환경 변수를 사용하여 구성 값을 잠그십시오.
1. *[!UICONTROL Admin]* 패널로 이동합니다.
1. **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**(으)로 이동합니다.
1. 두 번째 행에서 **[!UICONTROL Global/Main website]** 근처에 있는 **[!UICONTROL Edit]**&#x200B;을(를) 클릭합니다.
1. 스토어 보기에 대한 테마를 편집합니다.
1. HTML 헤드를 엽니다.
1. 개발자 도구를 사용하여 비활성화된 **[!UICONTROL Scripts and Style Sheets]** 필드를 사용하도록 설정합니다.
1. 값을 변경하고 저장합니다.

<u>예상 결과</u>:

잠긴 값을 저장할 수 없습니다.

<u>실제 결과</u>:

테이블 `core_config_data`에 `design/head/includes`에 대해 업데이트된 값이 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
