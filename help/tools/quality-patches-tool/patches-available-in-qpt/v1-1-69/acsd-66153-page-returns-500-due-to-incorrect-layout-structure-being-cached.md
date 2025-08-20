---
title: 'ACSD-66153: 캐시된 잘못된 레이아웃 구조로 인해 페이지가 500 오류를 반환함'
description: ACSD-66153 패치를 적용하여 캐시된 잘못된 레이아웃 구조로 인해 페이지가 500 오류 코드를 반환하는 Adobe Commerce 문제를 해결합니다.
feature: Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: 70c7255e369ef366407d539488f0d815eb93f48a
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACSD-66153: 캐시된 잘못된 레이아웃 구조로 인해 페이지가 500 오류를 반환함

ACSD-66153 패치는 캐시된 잘못된 레이아웃 구조로 인해 페이지가 500 오류 코드를 반환하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66153입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p10

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

캐시된 잘못된 레이아웃 구조로 인해 페이지에서 500 오류가 반환됩니다.

<u>재현 단계</u>:

1. `2.4-develop` 설치.
1. 사용자 정의 모듈을 만들고 설치합니다.
1.1 `catalog_category_view` 레이아웃에 사용자 지정 블록을 추가합니다.
1.1 생성자를 통해 사용자 지정 블록에 `Magento\Framework\View\Result\Layout`을(를) 삽입합니다.
1. **[!UICONTROL shop]** 범주를 만듭니다.
1. **[!UICONTROL two terminal windows]** 열기:
   1. **터미널 1**: 레이아웃 캐시를 계속 정리합니다.

      ```
      for i in {1..200}; do
        bin/magento cache:clean layout
      done
      ```

   1. **터미널 2**: 범주 페이지에 대한 동시 요청 시뮬레이션:

      ```
      for i in {1..200}; do
        curl -s -o /dev/null -w "Request $i: HTTP %{http_code}\n""http://your_magento_base_url/shop.html?req=$i"
      done
      ```

1. 500 상태 코드로 인해 일부 요청이 임의로 실패하고 `var/log/support_report.log`에 다음 오류가 표시됩니다.

   ```
   report.CRITICAL: The element with the "root" ID wasn't found. Verify the ID and try again. [] []
   ```

<u>예상 결과</u>:

모든 요청은 200 OK를 반환합니다.

<u>실제 결과</u>:

일부 요청은 간헐적으로 500 내부 서버 오류를 반환합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
