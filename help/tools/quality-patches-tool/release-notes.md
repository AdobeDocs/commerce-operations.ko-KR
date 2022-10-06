---
title: 릴리스 노트
description: Adobe Commerce에 사용할 수 있는 패치와 해결된 문제에 대해 알아봅니다.
source-git-commit: bb1cb17b75a799409336068967c9d0facefeaf41
workflow-type: tm+mt
source-wordcount: '9467'
ht-degree: 0%

---

# 릴리스 노트

다음 [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) 는 Adobe 및 Magento Open Source 커뮤니티에서 개발한 개별 패치를 제공합니다. 설치된 Adobe Commerce 또는 Magento Open Source 버전에서 사용할 수 있는 모든 개별 패치에 대한 일반 정보를 적용, 되돌리고 볼 수 있습니다. 패치를 개발한 사람에 관계없이 Adobe Commerce 및 Magento Open Source 프로젝트에 패치를 적용할 수 있습니다. 예를 들어 커뮤니티에서 개발한 패치를 Adobe Commerce 프로젝트에 적용할 수 있습니다.

>[!INFO]
>
>자세한 내용은 [패치 적용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) Adobe Commerce 또는 Magento Open Source 프로젝트에 패치를 적용하는 방법에 대한 지침을 참조하십시오. 자세한 내용은 [사용 가능한 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 소프트웨어 업데이트 가이드에서 릴리즈된 패치의 전체 목록을 검토합니다.

>[!INFO]
>
>에 대한 자세한 정보 [!DNL quality patches] 커뮤니티에서 만든 Magento Open Source은 [릴리스 노트](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6)에 대해) - 많은 수의 제품 소스를 할당할 때 사용자가 오류가 발생하는 문제를 수정합니다.
* **ACSD-46856** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6)의 경우) - 시스템 > 구성 > 가져오기 > 고급 가격을 통해 성능 업데이트 계층 가격을 개선합니다.
* **ACSD-46541** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4)에 대해) - 주문 항목이 삭제될 경우 관리자가 대변 메모를 만들 수 없는 문제를 수정합니다.
* **ACSD-46581** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6)에 대해) - 장바구니에서 국가를 선택한 후 예상 세금 합계가 업데이트되지 않는 문제를 수정합니다.
* **ACSD-46618** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6)에 대해) - 제품 목록 위젯에 로그인한 고객에 대해 캐시된 잘못된 가격이 표시되는 문제를 수정합니다.
* **ACSD-46674** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6)의 경우 - 이미지 유형의 사용자 지정 옵션이 고객 이메일에서 HTML으로 표시되는 문제를 수정합니다.
* **ACSD-46988** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6)에 대해 GraphQL &#39;통화&#39; API 요청이 사용자 지정 통화에 대해 NULL 값을 반환하는 문제가 수정되었습니다.
* **ACSD-47076** (Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5)의 경우 - Vimeo 비디오를 스토어에 재생할 수 없는 문제가 해결되었습니다.
* **ACSD-45071** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4)에 대해) - 가져오는 동안 기본 소스가 제품에 추가되는 문제를 수정합니다.
* **AC-3023** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6)의 경우 - DHL 스키마를 최신 버전 10.0으로 업데이트합니다.
* 업데이트된 패치: MDVA-42584.
* 교체된 패치: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.5*) - 사용자가 스토어 크레딧을 사용하여 환급할 때 잘못된 주문 상태가 발생하는 문제를 수정합니다.
* **ACSD-46703** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.4 &lt;2.4.6*) - 제품 편집 페이지에서 사용자 지정 옵션을 드래그 앤 드롭할 수 없는 문제를 수정했습니다.
* **ACSD-44851** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.6*) - 하위 카테고리가 있는 카테고리가 열거나 확장할 수 없는 문제를 수정합니다.
* **ACSD-46815** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.5 &lt;2.4.6*) - 카테고리 트리 요청이 20개의 카테고리로 제한되는 문제를 수정합니다.
* **ACSD-45675** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.6*) - 제품 내보내기에서 의 카테고리 이름을 사용하는 문제를 수정합니다 *기본 저장소 보기* 범위.
* **ACSD-46869** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.4 &lt;2.4.6*) - 장바구니의 구성 가능한 제품이 를 통해 업데이트되지 않는 문제를 수정합니다 *PUT REST API* 제품 수량을 변경하지 않고 요청합니다.
* **MDVA-42768-V2** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.3*) - 구성 가능한 제품에 정규 가격이 표시되는 문제를 수정합니다. *0* when *재고 부족 표시* is *예*.
* 업데이트된 패치: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* 사용되지 않는 패치: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.3*) - 카테고리 트리 요청이 20개의 카테고리로 제한되는 문제를 수정합니다.
* **ACSD-45781** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.2*) - 모바일에 스토어 전면 검색 필드가 표시되지 않는 문제를 수정합니다.
* **ACSD-46192** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.6 &lt;2.4.5*) - 을 사용할 때의 문제를 수정합니다 `async/bulk/V1/configurable-products/bySku/options` 엔드포인트.
* **ACSD-46404** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.4 &lt;2.4.5*) - 2.4.4로 업그레이드한 후 관리자가 로그인할 수 없는 문제가 수정되었습니다.
* 업데이트된 패치: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.4*) - 특정 저장소에 대한 GraphQL 제품 돌연변이가 요청된 스토어에 할당되지 않은 변형을 포함하여 구성 가능한 모든 변형을 반환하는 문제를 수정합니다.
* **ACSD-46146** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.6*) - 관리자의 주문을 받은 후 두 주문 확인 이메일이 전송되는 문제를 수정합니다.
* **ACSD-45255** (*Adobe Commerce >=2.4.3 &lt;2.4.6>*) - 제한된 관리자 사용자에 대한 낮은 재고 보고서 페이지의 예외를 수정합니다.
* **ACSD-45488** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.6*) - 여러 소스가 있는 구성 가능한 제품이 자동으로 In Stock으로 반환되지 않는 문제를 수정합니다.
* **ACSD-45754** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.1 &lt;2.4.6*) - 장바구니에 쿠폰을 적용한 후 보상 점수가 추가되지 않는 문제를 수정합니다.
* **ACSD-45849** (*Adobe Commerce >=2.4.3 &lt;2.4.4>*) - 스테이징 업데이트가 적용된 후 비디오 메타데이터가 손실되는 문제를 수정합니다.
* **ACSD-45257** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.4*) - GraphQL에서 장바구니 할인을 올바르게 표시하지 않는 문제가 수정되었습니다.
* **ACSD-44938** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.4*) - 다음 위치의 문제를 수정합니다. `VAT_ID` 게스트 사용자에 대한 GraphQL 요청에 적용할 수 없습니다.
* 업데이트된 패치: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.5 &lt;2.4.4*) - 대변 메모를 작성한 후 가상 제품에 대한 재고 수량이 잘못 계산되는 문제를 수정합니다.
* **ACSD-43887** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.5*) - 회사에 대한 구매 발주가 활성화될 때 체크아웃 결제 페이지에 잘못된 세부 사항이 표시되는 문제를 수정합니다.
* **ACSD-45143** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.5*) - `setShippingAddressesOnCart` 돌연변이는 숫자 영역 코드를 *지역*.
* **ACSD-44591** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.6*) - CAPTCHA 확인 없이 주문을 할 때 발생하는 오류를 수정합니다.
* **ACSD-45520** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.6*) - 사용자가 장바구니에서 구성 가능한 제품을 편집할 때 제품 세부 사항 페이지에서 견본 옵션이 사전 선택되지 않는 문제를 수정합니다.
* **ACSD-45169** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.6*) - 다음 위치의 문제를 수정합니다. [!DNL Visual Merchandiser] 스테이징 업데이트가 적용된 후 구성 가능한 제품에 대한 정확한 재고 및 가격이 표시되지 않습니다.
* **ACSD-45424** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.6*) - 부분 환불(대변 메모) 후에 잘못된 예약 보상이 생성된 문제를 수정합니다.
* **MDVA-42807** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.1 &lt;2.4.6*) - 스토어 맨 앞에 사용자 지정 통화 기호가 표시되지 않는 문제를 수정합니다.
* 업데이트된 패치: MDVA-42689, AC-3022

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.4*) - 주문 보고서의 주문 합계가 제한된 관리자 사용자에 대해 잘못 계산되는 문제를 수정합니다.
* **MDVA-44940** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.4*) - 관리자에서 카테고리를 저장하는 동안 발생하는 SQL 오류를 수정합니다.
* **MDVA-44562** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.2-p2*) - GraphQL 요청이 기본이 아닌 저장소 보기에서 시작되었음에도 불구하고 견적 항목에 대한 기본이 아닌 저장소 ID가 기본 저장소 ID로 대체되는 문제를 수정합니다.
* **MDVA-43167** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.4*) - 관리자 사용자가 모든 주문을 선택할 때 관리자 주문 그리드 일괄 작업이 다중 페이지에 적용되지 않는 문제를 수정합니다.
* **MDVA-44044** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.2-p2*) - 새 웹 사이트에 제품이 지정된 후 카테고리 페이지에 표시되지 않는 문제를 수정합니다.
* **MDVA-42509** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.3 &lt;2.4.4*) - 빠른 순서로 인해 *쿠키를 보낼 수 없습니다.* 오류가 발생했습니다.
* 업데이트된 패치: MDVA-41061, MDVA-42584.
* 새 [!DNL Quality Patches Tool] 패치는 *MDVA* to *ACSD* 내부 프로세스 변경 사항으로 인해

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.4*) - 항목의 최소 수량이 이미 장바구니에 있을 때 추가 항목을 장바구니에 추가할 수 없는 문제를 수정합니다.
* **MDVA-44887** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.4 &lt;2.4.5*) - 수정 사항 *처리할 수 없는 구문 오류: 예기치 않은 토큰 &#39;const&#39;입니다.* 오류가 발생했습니다.
* **MDVA-43718** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.5*) - 수정 사항 *소비자가 %resources에 액세스할 권한이 없습니다.* 사용자 지정 통합에서 공유 카탈로그에 액세스할 때 표시되는 오류입니다.
* **MDVA-44660** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2-p1 &lt;2.4.5*) - 액센트 문자가 ``` ` ``` 고객의 이름과 성에 사용할 수 없습니다.
* **MDVA-40896** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.4*) - 수정 사항 *오류: 유형 오류: Magento에 전달된 인수 3* 비동기 제품 벌크 API에 오류가 발생했습니다.
* **MDVA-38559** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.3*) - 수정 사항 */V1/customers/search API* 둘 이상의 구독이 있는 고객에 대한 오류입니다.
* **MDVA-44533** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.1 &lt;2.4.4*) - 번들 하위 제품에 할인이 잘못 적용되는 문제를 수정합니다.
* 업데이트된 패치: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.5*) - 제품이 *개별적으로 표시되지 않음* 여전히 카탈로그 고급 검색 결과에 나타납니다.
* **MDVA-44100** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.5*) - 모든 PPT가 장바구니의 마지막 제품에 할당되고 다른 제품에 대해 재설정되는 문제를 수정합니다.
* **MDVA-43605** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.1 &lt;2.4.5*) - Rest API를 사용할 때 주문 데이터가 행 합계에 대한 음수 값을 반환하는 문제를 수정합니다.
* **MDVA-43102** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.1 &lt;2.4.5*) - REST API를 통해 환급을 수행할 때 판매 가능한 수량이 올바르게 업데이트되지 않는 문제를 수정합니다.
* **MDVA-43178** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3-p2 &lt;2.4.5*) - GraphQL에서 사용자 지정 스토어에 대한 고객 토큰을 검색할 수 없는 문제를 해결했습니다.
* **MDVA-43859** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.5*) - 오류가 발생하는 문제를 수정합니다. *customerId = 인 해당 엔티티가 없음* 은 삭제된 고객이 로그인하려고 하면 기록됩니다.
* **MDVA-44147** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.5*) - GraphQL 요청이 구매요청 목록을 반환하지 않는 문제를 수정합니다.
* **MDVA-44505** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.3*) - GraphQL 보상 포인트 적용 이 총계를 업데이트하지 않고, 주문 배치 중에 스토어 크레딧이 여러 번 적용되는 문제를 수정합니다.
* 업데이트된 패치: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.3*) - 고객 세그먼트가 *모두*.
* **MDVA-39605** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.5*) - Redis 캐시 TTL(만료 날짜)에 잘못된 값이 있는 문제를 수정합니다.
* **MDVA-43862** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.3 &lt;2.4.5*) - GraphQL로 인해 고객이 장바구니 항목을 업데이트할 수 없는 문제가 수정되었습니다 *UpdateCartItems 변형* 오류가 발생했습니다.
* **MDVA-43824** (*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - 할인이 있는 주문 취소 시 오류가 표시되는 문제를 수정합니다.
* **MDVA-43451** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.5*) - 오류가 발생하는 문제를 수정합니다. *요청한 가게를 찾을 수 없습니다. 스토어를 확인하고 다시 시도하십시오.* 특정 웹 사이트에 대한 공유 카탈로그를 구성하는 동안 나타납니다.
* **MDVA-43491** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.5 &lt;2.4.5*) - 다중 저장소 웹 사이트에 대한 제품을 가져올 때 기본 이미지 레이블이 업데이트되지 않는 문제를 수정합니다.
* **MDVA-43601** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.5*) - 전체 재색인화 후 누락된 트리거와 관련된 문제를 수정합니다.
* **MDVA-42046** (*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - 제품을 업데이트하는 동안 날짜 입력 필드가 있는 제품 속성에 잘못된 값이 할당되는 문제를 수정했습니다.
* **MDVA-43935** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.5*) - 업셀 제품이 두 번 표시되는 문제를 수정합니다.
* **MDVA-44188** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.5*) - 시스템에서 발행한 이메일이 있는 문제를 수정합니다 `.-` 에서 주소는 전송되지 않습니다.
* **MDVA-42283** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.5*) - 프랑스어 로캘의 관리자 순서 그리드의 날짜 시간 형식이 잘못된 문제를 해결했습니다.
* 업데이트된 패치: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* 에 대한 패치 메타데이터가 추가되었습니다. [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.3.6*) - 사용자가 활성 예약된 업데이트에 대한 시작 시간을 편집할 수 있는 문제를 수정했습니다.
* **MDVA-42410** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.5*) - 쿠폰 보고서에 기본 통화만 표시되는 문제를 수정합니다.
* **MDVA-41136** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.5*) - 의 만료 날짜가 `mage-cache-sessid` 가 확장되지 않아 고객 데이터가 정리됩니다.
* **MDVA-39993** (*Adobe Commerce 및 Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - API를 통해 수행된 인벤토리 변경 사항이 프런트 엔드 의 제품 페이지에 반영되지 않는 문제를 수정했습니다.
* **MDVA-42855** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.5*) - 체크아웃 중에 새 고객 주소가 주소록에 저장되지 않는 문제를 수정합니다.
* **MDVA-42645** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.5*) - 스토어 신용 기능이 비활성화된 경우 관리자가 보상 점수를 환불할 수 없는 문제를 수정합니다.
* **MDVA-43414** (*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - 실행 시 발생하는 PHP 치명적인 오류를 수정합니다 `inventory.reservations.updateSalabilityStatus` 숫자 SKU에서 소비자를 큐에 추가합니다.
* **MDVA-41628** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.5*) - 새 모듈이 추가되면 기존의 제한된 관리자 사용자가 새 리소스에 액세스할 수 있는 문제를 수정합니다.
* **MDVA-43348** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.5*) - 기프트 카드 GraphQL 요청에 오류가 표시되는 문제를 수정합니다. `gift_card_options` contain *uid*.
* **MDVA-39546** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.5*) - 스테이징 업데이트의 시작 날짜를 편집 중 현재 날짜보다 이전 날짜로 설정할 수 있는 문제를 해결했습니다.
* **MDVA-42950** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.5*) - 비디오가 제품 페이지에서 재생되지 않는 문제를 수정합니다.
* **MDVA-42689** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.4*) - Adobe Commerce에서 *무결성 제약 조건 위반* 가져오는 동안 제품 카테고리를 업데이트하는 동안 오류가 발생했습니다.
* **MDVA-41229** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.5*) - 구성 가능한 제품을 가져온 후 백엔드에서 사용할 수 있는 이미지가 프론트먼트에 표시되지 않는 문제를 수정합니다.
* **MDVA-43731** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.4*) - 다음 위치의 문제를 수정합니다. *검색 동의어* 에 값이 추가되면 더 이상 작동하지 않습니다. *일치하는 최소 용어*.
* **MDVA-43232** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.5*) - 에서 제품을 정렬하는 문제가 해결되었습니다. [!DNL Visual Merchandiser] 특별 가격 기준 하위/맨위별 범주를 저장하는 동안 오류가 발생합니다.
* **MDVA-43726** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.3 &lt;2.4.3*) - 부분 재색인화 후 저장소 수준 속성 일치를 기반으로 한 카탈로그 가격 규칙이 적용되지 않는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-36464, MDVA-37478, MDVA-38608.
* 에 대한 패치 메타데이터가 추가되었습니다. [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.5*) - REST API를 통해 특정 웹 사이트에 대해 제품 가격 속성을 업데이트할 수 없는 문제를 수정했습니다.
* **MDVA-41350** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.5*) - 액세스가 제한된 관리자가 SKU별로 순서대로 역할 범위 밖의 제품을 추가할 때 예외가 발생하는 문제를 수정합니다.
* **MDVA-42269** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3-p1 &lt;2.4.5*) - 관리자가 *유형 오류: strtotime()에는 매개 변수 1이 문자열이어야 하며, null이면 null입니다.* 오류가 발생했습니다.
* **MDVA-40830** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.5*) - 주문 배치 중에 스토어 크레딧이 여러 번 적용되는 문제를 수정합니다.
* **MDVA-42237** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.5*) - 구성 가능한 제품 특별 가격이 하위 제품 가격의 변경 후 업데이트되지 않는 문제를 수정합니다.
* **MDVA-42520** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.4*) - 다음의 경우 세율이 두 번 적용되는 문제를 수정합니다 *국외 거래 활성화* 이 사용됩니다.
* 업데이트된 패치: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* 사용되지 않는 패치: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.2 &lt;2.4.5*) - 일괄 속성 업데이트로 인해 변경 후에만 기본 스토어에 대한 URL 재작성이 발생하는 문제를 수정합니다 *제품 가시성*.
* **MDVA-43091** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.4*) - 백엔드의 관리자에서 번들 제품을 주문하면 오류가 발생하는 문제를 수정합니다 *이 제품에 소수점 수량을 사용할 수 없습니다*.
* **MDVA-40816** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.5*) - 관련 제품 규칙에 규칙 조건에 정의되지 않은 카테고리의 제품이 표시되는 문제를 수정했습니다.
* **MDVA-41305** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.5*) - GraphQL 돌연변이가 구성 가능한 제품 옵션을 희망 목록에 추가한 후 반환하지 않는 문제가 수정되었습니다.
* **MDVA-39181** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.5*) - 관련 제품 규칙에 규칙 조건에 정의되지 않은 카테고리의 제품이 표시되는 문제를 수정했습니다.
* **MDVA-42584** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.3*) - 가져오기 또는 API를 통해 수량 및 재고 상태를 변경한 후 백엔드의 구성 가능한 재고 상태가 업데이트되지 않는 문제를 수정합니다.
* **MDVA-40175** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.3*) - 다음 위치의 문제를 수정합니다. *운송 방법을 변경하려면 클릭하십시오.* 는 재정렬 중에 관리자에서 배송 방법을 선택할 라디오 단추를 표시하지 않습니다.
* **MDVA-42768** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.5*) - 구성 가능한 제품이 *재고 부족 표시* 예.
* **MDVA-43201** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.4*) - 특정 로케일과 함께 DOB 속성을 사용할 때 고객 로그인에서 오류가 발생하는 문제를 수정했습니다.
* 업데이트된 패치: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.5*) - Adobe Commerce 시간대가 로컬 환경 시간대와 다를 때 날짜 필터가 제대로 작동하지 않는 문제를 수정했습니다.
* **MDVA-42657** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.5*) - 관리자 사용자가 고객 세그먼트 조건에서 카테고리를 선택할 수 없는 문제가 수정되었습니다.
* **MDVA-42806** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.4*) - *새 회사 등록* 기존 회사가 REST API를 통해 업데이트될 때마다 이메일이 전송됩니다.
* **MDVA-37984** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.5*) - [!DNL Visual Merchandiser] *규칙별 제품 일치* 기능이 스테이징 업데이트로 제품을 올바르게 필터링하지 않습니다.
* **MDVA-40488** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.4*) - 재고 부족 하위 제품이 있는 구성 가능한 제품이 올바른 가격 범위에 표시되지 않는 문제를 수정합니다.
* **MDVA-42507** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.5*) - 장바구니 규칙에 대한 스테이징 업데이트를 적용한 후 전체 페이지 캐시가 정리되는 문제를 수정합니다.
* **MDVA-39163** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.5 &lt;2.4.5*) - 새 사용자가 등록되고 장바구니에 있는 제품이 게스트 세션의 제품에서 배송 방법을 사용할 수 없는 문제를 해결했습니다.
* **MDVA-38626** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.3 &lt;2.4.5*) - 관리자 사용자가 를 사용하여 백엔드에 주문을 할 수 없는 문제를 수정합니다 [!DNL PayPal Payflow Pro] 결제.
* **MDVA-38666** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.2 &lt;2.3.6*) - 관리자가 고객 장바구니에서 구성 가능한 제품 옵션을 변경할 수 없는 문제를 해결했습니다.
* **MDVA-38526** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.4*) - 관리자 사용자가 [!DNL Site-Wide Analysis tool].
* 업데이트된 패치: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.4*) - 사용자가 를 설정한 후 500 오류가 발생하는 문제를 수정합니다 *이미지 메시지* 쿠키가 이미 존재하는 경우 쿠키에 사용할 수 있지만 새 메시지가 없습니다.
* **MDVA-41139** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.3 &lt;2.4.4*) - 간단한 제품의 수량=0 이 소스 중 하나에 대해 제품 가져오기 후 구성 가능한 제품이 재고 부족이 되는 문제를 수정합니다.
* **MDVA-42326** (*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - 영구 장바구니가 활성화되어 있어도 세션 시간 초과 후 고객이 체크아웃에 오류가 발생하는 문제를 수정했습니다.
* **MDVA-42341** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.4*) - `categoryList` GraphQL 쿼리에 저장소 헤더가 있는 경우 결과를 필터링하지 않습니다.
* **MDVA-38393** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.4*) - 간단한 제품의 이름을 다시 지정하는 경우 구성 가능한 제품에 대해 카탈로그 규칙이 작동하지 않는 문제를 수정합니다.
* **MDVA-39153** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.4*) - 관리자에서 재배치하는 동안 할인 금액이 잘못 계산되는 문제를 수정합니다.
* 업데이트된 패치: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.3*) - 관리 사용자가 웹 사이트를 삭제한 후 고객 그리드에 액세스할 수 없는 문제를 수정했습니다.
* **MDVA-40311** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2-p2 &lt;2.4.4*) - 관리자가 오류 메시지를 표시하는 문제를 해결했습니다 *보안 또는 양식 키가 잘못되었습니다. 페이지를 새로 고치십시오* 사용자 지정 관리자 경로가 구성되고 암호 키가 활성화되어 있는 경우 관리자에 로그인한 후 .
* **MDVA-41631** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.4*) - 옵션 없이 주문 정보를 검색하려고 할 때 오류가 발생하는 문제를 수정합니다 *전화* GraphQL을 통해 값을 생성할 수 있습니다.
* **MDVA-27239** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.3.6*) - 크로스셀 제품이 표시되지 않는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.5 &lt;2.4.4*) - 재색인화 중에 프론트먼트에서 제품이 누락되는 문제를 수정합니다.
* **MDVA-40120** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.4*) - DESC/ASC로 GraphQL 정렬이 관련성 또는 가격이 동일한 제품에서 작동하지 않는 문제를 수정합니다.
* **MDVA-41399** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.3 &lt;2.4.2*) - 관리자가 액세스할 수 없는 문제가 수정되었습니다 *장바구니 관리* 고객이 원하는 목록에 제품을 추가할 경우 페이지를 지정합니다.
* **MDVA-40609** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.3*) - 비활성화된 제품 데이터가 `cataloginventory_stock_status` 인덱스 테이블, 잘못 비활성화된 제품 수량을 표시합니다.
* **MDVA-39031** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.4*) - GraphQL을 통해 타겟 웹 사이트에 할당되지 않은 경우에도 장바구니에 제품을 추가할 수 있는 문제를 수정합니다.
* **MDVA-41597** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.4*) - GraphQL을 사용하여 장바구니에 구성 가능한 제품을 두 개 이상 추가할 때 오류가 발생하는 문제를 수정합니다.
* **MDVA-27456** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.5 &lt;2.3.7*) - 사용자가 로드하려고 할 때 오류가 발생하는 문제를 수정합니다 [!DNL Swagger].
* **MDVA-32776** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.2*) - 주문이 배치되었지만 출하되지 않은 경우 재고 상태가 업데이트되지 않는 문제를 수정합니다.
* **MDVA-30862** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.0*) - 인쇄된 PDF 송장에 잘못된 주문 일자가 있는 문제를 수정합니다.
* 에 대한 인덱스 페이지가 개선되었습니다. [!DNL Quality Patch Tool]. 에 대한 편리한 검색 및 필터링이 추가되었습니다. [!DNL quality patches] 최신 버전의 도구.
* 업데이트된 패치: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.4*) - 종료로 인해 제거된 경우 제품에 대해 새로 만들거나 기존 예약된 업데이트를 편집할 수 없는 문제가 해결되었습니다.
* **MDVA-41046** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.4*) - 구성 가능/그룹화된 제품에 지정하기 위해 사용자 지정 옵션이 있는 간단한 제품을 사용할 수 있는 문제를 수정합니다.
* **MDVA-40545** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.4*) - 동일한 페이지에 대해 노드가 두 개 이상 있어도 페이지에 대한 첫 번째 노드만 검색되는 문제를 수정합니다.
* **MDVA-41164** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.3-p1*) - 관리자 사용자가 파일 또는 이미지 유형 사용자 지정 고객 특성을 사용하여 회사를 저장하거나 편집할 수 없는 문제를 수정합니다.
* **MDVA-39229** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.4*) - 카탈로그 규칙 스테이징 업데이트 시작 시간을 업데이트한 후 다음 오류가 표시되는 문제를 수정합니다. *Cron 작업 staging_synchronize_entities_period에 오류가 있습니다. 활성 업데이트를 삭제할 수 없습니다.*
* **MDVA-40619** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.4*) - CMS 페이지에서 인라인 편집을 시도할 때 CMS 페이지 계층 구조에 대한 변경 사항이 500 오류를 발생하는 문제를 수정합니다.
* **MDVA-41061** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.3*) - 제품이 관리자로부터 저장될 때 재고 상태가 판매 가능으로 재설정되는 문제를 수정합니다.
* **MDVA-31763** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.4*) - 수동 재색인화가 완료될 때까지 카탈로그 가격 규칙이 귀속(또는 적용되지 않음)되는 문제를 수정합니다.
* **MDVA-37748** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.3*) - GraphQL 쿼리에서 공유 카탈로그에 할당되지 않은 제품을 반환하는 문제를 수정했습니다.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.4*) - 동일한 주문에 대한 부분 송장을 REST API를 통해 동시에 만들 수 없는 문제를 수정합니다.
* **MDVA-40101** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.2 &lt;2.4.0*) - 를 사용하여 주문 배치에 성공한 후 미니 카트에서 항목이 제거되지 않는 문제를 수정합니다 [!DNL PayPal Express] 체크아웃.
* **MDVA-40401** (*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - 주문이 실패하는 경우에도 쿠폰 사용 값이 변경되는 문제를 수정합니다.
* **MDVA-40537** (*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - 동일한 URL 키를 가진 여러 CMS 페이지가 있는 경우, 스토어 보기를 만들 때 오류가 발생하는 문제를 수정합니다.
* **MDVA-37725** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;=2.4.3-p1*) - 기본이 아닌 웹 사이트에서 보낸 비동기 주문 이메일에 기본 웹 사이트의 로고 URL이 포함되는 문제를 수정합니다.
* **MDVA-39482** (*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - 미납주문이 활성화되었을 때 &quot;0&quot; 수량과 함께 가져오는 경우 제품 재고가 떨어지는 문제를 수정합니다.
* **MDVA-40435** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.4*) - GraphQL을 통해 적용할 때 동적 가격이 있는 번들 제품에서 잘못된 할인이 발생하는 문제를 수정합니다.
* **MC-42528** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - `categoryList` GraphQL 쿼리는 할당된 카테고리와 지정되지 않은 카테고리를 모두 반환합니다.
* **MDVA-29400** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - [!DNL PayPal Express Checkout].
* **MDVA-26005** (*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - 장바구니 가격 규칙 조건에 대한 카테고리에서 카테고리를 선택할 수 없는 문제를 수정합니다.
* **MDVA-25631** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.3 &lt;=2.3.5-p2*) - 많은 고객이 포함된 고객 세그먼트를 편집하고 저장하는 성능을 개선합니다.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.4*) - GraphQL 검색 쿼리가 관리에서 인기 있는 검색어에 표시되지 않는 문제가 해결되었습니다.
* **MDVA-40601** (*Adobe Commerce 및 Magento Open Source >=2.3.1의 경우 &lt;=2.4.2-p2*) - GraphQL을 통해 예약된 업데이트로 변경된 카테고리에 대한 정보를 가져오려고 하면 오류가 발생하는 문제를 수정합니다.
* **MDVA-37234** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - 동일한 SKU에 대해 항목을 장바구니에 여러 번(병렬 요청)추가하면 동일한 장바구니 ID에 대한 중복 라인 항목이 만들어지는 문제를 해결했습니다.
* **MDVA-33606** (*Adobe Commerce 및 Magento Open Source >=2.4.1의 경우 &lt;=2.4.2-p2*) - 사용자가 *고유 제약 조건 위반* 계층에 지정된 CMS 페이지를 저장할 때 오류가 발생합니다.
* **MDVA-31590** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - 사용자가 MySQL 비동기 큐를 사용하여 속성을 벌크로 업데이트할 수 없는 문제를 수정했습니다.
* **MDVA-36309** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - 속성별 제품 검색이 관리자 그리드에서 느려지는 문제를 수정합니다.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.4*) - 주문이 스토어 크레딧에서 지급될 때 FPT가 있는 송장에 잘못된 총계가 표시되는 문제를 수정합니다.
* **MDVA-37364** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;=2.4.3*) - 날짜 유형의 사용자 지정 고객 속성이 고객의 그리드 UI를 차단하는 문제를 수정합니다.
* **MDVA-39195** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - 다음 위치의 문제를 수정합니다. *장바구니에 추가* 장바구니에 대한 리디렉션이 활성화되었을 때 카테고리 페이지에서 단추가 비활성 상태였습니다.
* **MDVA-37115** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - 불필요하게 *0개만 남음* 구성 가능한 제품 페이지에 알림이 표시됩니다.
* **MDVA-39521** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.4*) - 사용자가 GraphQL을 통해 빈 전화 번호로 장바구니에서 배송 주소를 설정할 수 없는 문제를 해결했습니다.
* **MDVA-39384** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - 회사 사용자에 대한 사용자 지정 고객 속성이 저장되지 않는 문제를 수정합니다.
* **MDVA-39043** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;=2.4.3*) - 관리자 액세스 권한이 제한된 사용자가 를 추가하려고 할 때 오류가 발생하는 문제를 수정했습니다 *제품* 위젯을 CMS 페이지에 추가합니다.
* **MDVA-39966** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - 잘못된 로케일 배포 문제를 해결했습니다.
* **MDVA-38852** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;=2.3.5-p2*) - 설계별 카탈로그 인벤토리가 몇 개의 병렬 주문이 있는 경우 성능이 크게 저하되는 업데이트에 대한 테이블을 잠그는 문제를 해결했습니다.
* **MDVA-39986** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.3*) - 사용자가 Safari 브라우저를 사용하여 MacOS의 관리자에게 주문을 할 수 없는 문제를 수정합니다.
* **MDVA-38447** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.4*) - 다음 두 가지 문제가 해결되었습니다. 여기서 *개별적으로 표시되지 않음* 구성 가능한 하위 제품은 GraphQL 응답에서 반환되고 범주 필터를 사용하여 GraphQL 제품 쿼리에 대한 MySQL 쿼리를 최적화합니다.
* **MDVA-40134** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.3*) - 공유 카탈로그가 활성화되어 있을 때 GraphQL이 관련 제품을 반환하지 않는 문제를 수정했습니다.
* **MDVA-39935** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.1 &lt;2.4.4*) - GraphQL에서 웹 사이트 수준에서 비활성화된 구성 가능한 하위 제품을 반환하는 문제를 수정합니다.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.4*) - *멤버 함수 getId() 호출* 오류가 관리자의 주문 세부 사항 페이지에 표시됩니다.
* **MDVA-34948** (*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - 처럼 오래 실행되는 쿼리의 문제를 수정합니다. `GET_LOCK`.
* **MDVA-39305** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - 등록된 고객이 Google ReCaptcha를 사용하여 로그인할 수 없는 문제가 수정되었습니다.
* **MDVA-37897** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.4*) - 고객이 최근에 본 위젯의 옵션이 있는 제품을 추가하려고 할 때 잘못된 리디렉션이 발생하는 문제를 수정합니다.

## v1.1.0 {#v1-1-0}

* 사용자 경험을 향상시키고 고객이 필요한 패치를 쉽게 검색할 수 있도록 패치 카테고리가 도입되었습니다.
* 다음 `patches.json` 파일 이름이 `support-patches.json`.
* **MDVA-38799** (*Adobe Commerce >=2.3.0 &lt;2.4.3>*) - 스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않은 문제를 해결했습니다.
* **MDVA-37592** (*Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - 공유 카탈로그에 제로 가격이 할당된 제품에 대해 가격별 정렬이 제대로 작동하지 않는 문제를 수정했습니다.
* **MDVA-38827** (*Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - 고객이 오류 메시지가 포함된 주문 선적 이메일을 받는 문제를 수정합니다.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - CMS 페이지를 저장할 때 발생하는 오류를 수정합니다. *동일한 ID PAGE_ID의 항목이 이미 있습니다.*.
* **MDVA-34680** (*Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - 고객 계정에서 만든 시간이 고객 그리드에서 올바르게 필터링되지 않는 문제를 수정합니다.
* **MDVA-37068** (*Adobe Commerce >=2.3.1 &lt;2.4.4*) - 장바구니에 가상 제품만 있을 때 잘못된 세율이 표시되는 문제를 수정합니다.
* **MDVA-38608** (*Adobe Commerce >=2.3.0 &lt;2.4.3>*) - 재색인이 성공적으로 완료되지 않을 때 임시 테이블이 삭제되지 않는 문제를 수정합니다.
* **MDVA-38308** (*Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - 추가와 관련된 문제가 해결되었습니다. [!DNL Vimeo] 제품에 대한 비디오.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*Adobe Commerce >=2.3.6 &lt;2.4.3>*) - 을 사용할 때 고객이 지급 확인 페이지로 이동하지 않는 문제를 수정합니다 [!DNL Paypal Payment Advanced] 메서드를 사용합니다.
* **MDVA-37082** (*Adobe Commerce >=2.3.0 &lt;2.4.3>*) - 그룹화된 제품의 사용자 지정 재고를 저장할 때 문제가 해결되어 제품이 프론트런트에 재고가 없습니다.
* **MDVA-36572** (*Adobe Commerce >=2.3.5 &lt;2.4.3>*) - 대변 메모 업데이트로 인해 데이터베이스에서 중복 제품 예약 업데이트가 발생하지 않는 경우 문제를 수정합니다.
* **MDVA-38132** (*Adobe Commerce >=2.3.3 &lt;2.4.3>*) - Admin Console에 연결할 수 없는 *리디렉션이 너무 많음* 오류가 발생했습니다.
* **MDVA-38270** (*Adobe Commerce >=2.4.1 &lt;2.4.3>*) - GraphQL에서 총 주문 수에 기프트 카드 정보가 누락되는 문제를 수정했습니다.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*Adobe Commerce >=2.4.2 &lt;=2.4.4*) - 웹 사이트 ID가 스토어 ID와 일치하지 않는 경우 GraphQL을 통해 구성 가능한 제품을 장바구니에 추가할 때 발생하는 문제를 수정합니다.
* **MDVA-36832** (*Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - 보기 너비가 768px일 때 페이지에서 이미지가 중복되는 문제를 수정합니다.
* **MDVA-37874** (*Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - 다음 위치의 문제를 수정합니다. *전체 장바구니에 대한 고정 할인 금액* 둘 이상의 옵션이 포함된 번들 제품에 잘못 적용되었습니다.
* **MDVA-37913** (*Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - 다운로드 가능한 제품이 API를 통해 업데이트되는 경우 다운로드 가능한 링크가 사라지는 문제를 수정합니다.
* **MDVA-34330** (*Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Orders 그리드의 주문이 관리 시간대에 따라 필터링되지 않는 문제를 수정합니다.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*Adobe Commerce >=2.3.0 &lt;=2.3.7*) - 와 함께 배치된 주문에 대한 부분 송장을 만들 때 Adobe Commerce에 오류가 발생하는 문제를 수정합니다 *계정입금* REST API를 통한 결제 방법.
* **MDVA-37362** (*Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - 구성 가능한 제품 옵션 값과 변형 속성 값이 GraphQL 응답에서 비어 있는 문제를 수정합니다.
* **MDVA-37288** (*Adobe Commerce 2.4.2*) - GraphQL 요청 후 잘못된 계층 가격이 반환되는 문제를 수정합니다.
* **MDVA-37225** (*Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - 가져온 SKU에 정수 값이 있는 경우 빠른 주문 생성 중에 업로드 프로세스가 중단된 문제를 수정합니다.
* **MDVA-37224** (*Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - 고객이 협상 가능한 견적을 지불할 수 없는 문제를 수정합니다. [!DNL PayFlow Pro] 장바구니에 다른 제품을 포함합니다.
* **MDVA-36286** (*Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - 동일한 SKU가 하위 카테고리에서 다른 위치를 갖는 경우 Page Builder 제품 위젯 미리 보기가 중단되는 문제를 수정합니다.
* **MDVA-30186** (*Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - GraphQL 응답에서 속성 항목 수 대신 속성 옵션이 옵션 값별로 정렬되는 문제를 수정합니다.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*Adobe Commerce >=2.3.0 &lt;=2.4.2*) - API를 통해 변경한 후 이전 사용자 지정 옵션이 남아 있는 문제를 수정합니다.
* **MDVA-35773** (*Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - 100% 할인이 적용되는 주문에 대한 송장에 총계 가 0으로 표시되지 않는 문제를 수정합니다.
* **MDVA-36833** (*Adobe Commerce 2.4.2*) - 공유 카탈로그에서 일부 제품을 제외한 후 페이지당 임의 개수의 제품을 표시하는 검색 결과 문제를 수정합니다.
* **MDVA-37182** (*Adobe Commerce >=2.4.1 &lt;=2.4.2*) - 두 위치에서 잘못된 검색 결과를 가져오는 문제를 수정했습니다 [!DNL Elasticsearch] 버전 6 및 버전 7.
* **MDVA-36253** (*Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - 항목 삭제 후 미니 장바구니에 잘못된 소계가 표시되는 문제를 수정합니다.
* **MDVA-36853** (*Adobe Commerce 2.4.2*) - 큰 미디어 갤러리를 로드할 때 이미지가 없는 문제를 수정했습니다.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - 카테고리 페이지에서 번들 제품이 누락되는 문제를 수정했습니다.
* **MDVA-36615** (*Adobe Commerce 2.4.2*) - Admin Product Grid에서 잘못된 제품 카운트와 관련된 문제를 수정합니다.
* **MDVA-36464** (*Adobe Commerce >=2.4.0 &lt;=2.4.2*) - 이메일 알림 구성이 저장소 보기 수준에서 작동하지 않는 문제를 수정합니다.
* **MDVA-36138** (*Adobe Commerce ^2.3.2용*) - 장바구니의 모든 항목이 무료 배송 장바구니 규칙에 대한 자격이 없는 경우 배송 가격이 조정되지 않고 전체 배송 가격이 고객에게 표시되는 문제를 수정합니다.
* **MDVA-36424** (*Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - 백엔드 기본 URL이 storefront URL과 다른 경우 컨텐츠를 반복적으로 편집할 때 페이지 빌더 요소에 첨부된 미디어 이미지가 사라지는 문제를 수정합니다.
* **MDVA-35984** (*Adobe Commerce ^2.4.0*) - 동일한 제품에 대해 복수 동시작업 출하를 생성한 후 잘못된 제품 수량 및 선택 가능한 수량에 대한 문제를 수정합니다.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*Adobe Commerce >=2.3.4 &lt;2.4.2>*) - GraphQL 쿼리가 카테고리 캐시 태그를 사용하여 캐시되지 않는 문제가 해결되었습니다.
* **MDVA-33168** (*Adobe Commerce >=2.3.3 &lt;2.4.2>*) - API를 통해 제품 속성을 업데이트할 때 다른 모든 속성이 빈 값으로 변경되는 문제를 수정합니다.
* **MDVA-19640** (*Adobe Commerce >=2.3.0*) - 다음 위치의 문제를 수정합니다. [!DNL Advanced Reporting] 가 데이터를 표시하지 않습니다.
* **MDVA-11189** (*Adobe Commerce >=2.3.0 &lt;2.3.5>*) - CSV 파일을 가져온 후 제품 재고를 업데이트하기 위해 의 행을 수정할 때 발생하는 문제를 수정합니다 `cataloginventory_stock` 테이블이 삭제됩니다.
* **MDVA-26639** (*Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - 새 주문 확인 이메일 템플릿이 생성되면 주문 메일에 주문 항목이 누락되는 문제를 수정합니다.
* **MDVA-15546** (*Adobe Commerce >=2.3.0*) - 주문을 만든 후 다음 문제가 해결되었습니다. *Column entity_id where 절이 모호합니다.* 예외 로그에 오류가 표시됩니다.
* **MDVA-21095** (*Adobe Commerce >=2.3.0 &lt;2.3.5>*) - 쿼리 시 발생하는 문제를 수정합니다 `INSERT INTO search_tmp` 은 일괄 속성 값 업데이트 후 종료되지 않습니다.
* **MDVA-23845** (*Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - JavaScript 축소가 활성화된 후 이메일 템플릿을 미리 볼 수 없는 문제를 수정합니다.
* **MDVA-22026** (*Adobe Commerce >=2.3.2 &lt;2.3.4*) - 외부 URL의 이미지를 포함하여 CSV 파일에서 제품을 가져올 수 없는 문제를 해결했습니다.
* **MDVA-22383** (*Adobe Commerce >=2.3.0 &lt;2.3.4>*) - 제품을 저장하는 데 시간이 오래 걸려 페이지가 중단되는 문제를 해결했습니다.
* **MC-41359** (*Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3>*) - 잘못된 SameSite 쿠키 매개 변수 설정의 문제를 수정합니다.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*Adobe Commerce 2.4.1*) - 페이지 빌더에 다음 오류가 발생하는 문제를 수정합니다. *페이지 빌더를 시작하는 동안 오류가 발생했습니다. 기술 지원 담당자에게 문의하십시오.*
* **MDVA-35356** (*Adobe Commerce >=2.3.0 &lt;2.4.3>*) - 부분 송장 주문 취소 후 잘못된 스토어 신용 반납 문제가 수정되었습니다.
* **MDVA-33289** (*Adobe Commerce >=2.4.0 &lt;2.4.3>*) - 체크아웃 중에 원시 JavaScript 코드가 청구 주소 UI에 표시되는 문제를 수정합니다. [!DNL Google Tag Manager] 이 활성화되어 있습니다.
* **MDVA-35982** (*Adobe Commerce >=2.3.0 &lt;2.4.3>*) - 특정 웹 사이트로 제한된 관리 사용자가 동일한 웹 사이트에 배치된 주문에 대해 선적을 만들 수 없는 문제를 수정합니다.
* **MDVA-35155** (*Adobe Commerce >=2.3.0 &lt;2.3.6>*) - 옵션 제목이 변경된 경우 번들 제품을 구매할 수 없는 문제를 수정했습니다.
* **MDVA-35910** (*Adobe Commerce >=2.4.1 &lt;2.4.3>*) - 고객으로 로그인을 비활성화한 후 새 고객 계정을 만들 수 없는 문제를 수정합니다.
* **MDVA-34474** (*Adobe Commerce >=2.3.0 &lt;2.4.3>*) - API를 사용하여 구매요청 목록에 제품을 추가하는 문제를 수정합니다.
* **MDVA-34591** (*Adobe Commerce >=2.3.0 &lt;2.4.3>*) - 다음에 대한 잘못된 장바구니 규칙 할인 계산과 관련된 문제를 수정합니다 *최대 수량 할인이 적용됨* 및 *할인 수량 단계(구매 X)*.
* **MDVA-33704** (*Adobe Commerce >=2.4.0 &lt;2.4.3>*) - *매장 내 픽업* 배송 옵션을 사용할 수 있도록 구성되었지만 표시되지 않습니다.
* **MDVA-34928** (*Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - 스토어 크레딧을 지급에서 제거한 후 페이지 로더가 무기한 표시되는 문제를 수정합니다.
* **MDVA-35254** (*Adobe Commerce >=2.3.1 &lt;2.4.3>*) - 체크아웃 중 CAPTCHA와 관련된 문제를 수정합니다.
* **MDVA-35569** (*Adobe Commerce >=2.3.4 &lt;2.4.2>*) - *고정 제품세* 상태가 지정된 경우 GraphQL 응답에서 필드가 채워지지 않습니다.
* **MDVA-35847** (*Adobe Commerce >=2.4.1 &lt;2.4.3>*) - 사용자 지정 고객 속성이 사용되는 경우 회사 사용자가 형성하는 B2B 문제를 수정합니다.
* **MDVA-31307** (*Adobe Commerce >=2.4.0 &lt;2.4.2>*) - 가 있는 문제를 수정합니다. *메모리가 부족합니다.* 캐싱된 블록에 대해 dynamic CSP를 화이트리스트에 추가할 때 발생하는 문제로 인해 특정 카테고리의 오류가 발생합니다.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*Adobe Commerce >=2.3.0 &lt;2.4.3>*) - 잘못된 *진행 중* 올바른 메시지 상태 *complete* 소비자에게 보내는 메시지 `quoteItemCleaner` 여러 제품을 삭제한 후.
* **MDVA-34102** (*Adobe Commerce >=2.3.0 &lt;2.4.3>*) - Admin Area의 Product Grid 및 Edit Product 페이지에서 비활성화된 제품에 대한 Default Stock 수량이 0으로 수정되었습니다.
* **MDVA-35286** (*Adobe Commerce >=2.4.0 &lt;2.4.2>*) - 고객이 장바구니에 제품을 번들로 제공하고 여러 주소 체크아웃에서 Onepage 체크아웃으로 전환하는 경우 오류가 발생하는 문제를 수정합니다.
* **MDVA-35312** (*Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - 빈 GraphQL 요청이 있을 때 응답 코드 500을 수정합니다.
* **MDVA-34189** (*Adobe Commerce >=2.3.4 &lt;2.4.3>*) - 의 503 첫 번째 바이트 시간 초과가 수정되었습니다. [!DNL Visual Merchandiser] 관리 카테고리 페이지를 로드할 때 쿼리
* **MDVA-34695** (*Adobe Commerce >=2.3.0 &lt;2.4.1*) - 음수 수정 사항 `children_count` 카테고리를 삭제한 후.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*Adobe Commerce >=2.3.1 &lt;2.4.3>*) - *기본값 사용* 예약된 변경 사항이 적용된 후 확인란이 지워집니다. 예약된 변경 사항이 더 이상 적용되지 않으면 문제가 표시됩니다.
* **MDVA-35064** (*Adobe Commerce >=2.3.3 &lt;2.4.3>*) - API를 통해 작성된 구성 가능한 제품에 대해 URL 다시 쓰기가 생성되지 않는 문제가 수정되었습니다.
* **MDVA-34943** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 빠른 주문이 이전에 입력한 SKU를 캐시하는 문제를 수정합니다.
* **MDVA-35197** (*Adobe Commerce >=2.3.5 &lt;2.4.0>*) - 이전에 추가한 제품의 재고가 없는 경우 GraphQL을 사용하여 장바구니에 추가할 때 오류가 발생하는 문제를 수정합니다.
* **MDVA-34850** (*Adobe Commerce >=2.3.1 &lt;2.4.0>*) - 구성 가능한 제품의 재고 부족 옵션이 취소됨으로 표시되는 대신 표시되지 않는 문제를 수정합니다.
* **MDVA-34867** (*Adobe Commerce >=2.3.0 &lt;2.4.3>*) - 예약된 업데이트에 대해 설정된 조건 필드의 값이 저장되지 않는 문제를 해결했습니다.
* **MDVA-35092** (*Adobe Commerce >=2.3.5 &lt;2.4.3>*) - 사용자가 추가할 수 없는 문제를 수정했습니다 [!DNL Vimeo] 더 이상 사용되지 않는 비디오로 인해 [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*Adobe Commerce >=2.3.6 &lt;2.4.3>*) - 일치하는 제품에 각 웹 사이트에 대해 가격이 다른 경우 Page Builder 제품 컨텐츠 유형 미리 보기가 중단되는 문제를 수정합니다.
* **MDVA-32634** (*Adobe Commerce ^2.3.1*) - `url_path` 모든 저장소에 할당된 카테고리 중 는 계층에서 카테고리를 이동한 후 변경되지 않고 유지됩니다.
* **MDVA-33344** (*Adobe Commerce ^2.3.0*) - 하드 코딩된 문제가 해결되었습니다. `rma_item` 데이터베이스의 값 대신 엔티티 기본 속성 세트 ID가 사용됩니다.
* **MDVA-34192** (*Adobe Commerce >=2.3.4 &lt;2.4.3>*) - dd/mm/yyyy 형식을 사용하여 생년월일을 수정/지정할 수 없는 문제를 수정합니다.
* **MDVA-34847** (*Adobe Commerce ^2.3.0*) - 사용자 지정 권한이 있는 관리자 컬렉션의 SQL 조건에 대한 정수로 스토어 ID를 수정합니다.
* **MDVA-34886** (*Adobe Commerce ^2.3.2용*) - 다음의 경우 검색이 결과를 반환하지 않는 문제를 수정합니다 *가중치* 제품 속성은 검색할 수 있도록 구성됩니다.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*Adobe Commerce >=2.3.0 &lt;2.4.3>*) - 의 문제가 해결되었습니다. [!DNL PayPal Payflow Pro] 리디렉션 매개 변수 목록 형식 오류로 인해 지급이 실패했습니다.
* **MDVA-34023** (*Adobe Commerce >=2.3.0 &lt;2.4.3>*) - 오류가 발생하는 문제를 수정합니다. *addressId가 있는 해당 엔터티가 없습니다.* 방문자의 브라우저에 임의로 표시됩니다.
* **MDVA-32759** (*Adobe Commerce용 >=2.3.1 &lt;2.4.3(B2B 확장 포함)*) - 공유 카탈로그에서 기존 계층 가격을 삭제하는 문제를 수정합니다.
* **MDVA-33482** (*Adobe Commerce ^2.3.5용*) - 부분 송장에 대해 대변 메모를 생성하는 경우 해당 부분 송장에 대한 세금 대신 총 주문에 대한 세금이 부과되는 문제를 수정합니다.
* **MDVA-33393** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 오류를 수정합니다. *제공된 countryId가 없습니다.*.
* **MDVA-33632** (*Adobe Commerce >=2.3.0 &lt;2.3.7>*) - 예외 메시지가 표시되는 수정 사항을 제공합니다. *이 제품은 재고가 없습니다* 이제 재고 부족 제품을 다시 주문하려고 할 때 관리자 사용자에게 가 표시됩니다.
* **MDVA-34469** (*Adobe Commerce >=2.4.1 &lt;2.4.2>*) - 여러 저장소 보기를 사용할 때 고객의 장바구니에 대한 GraphQL 돌연변이가 실패하는 문제를 해결했습니다.
* **MDVA-33976** (*Adobe Commerce >=2.3.0 &lt;2.3.7>*) - 번들 제품에서 두 번째 옵션을 제거한 후 번들 제품이 상점 전면에 재고 부족이 표시되는 문제를 해결했습니다.
* **MDVA-33894** (*Adobe Commerce용 >=2.4.0 &lt;2.4.1(B2B 확장 포함)*) - 여러 제품 및 SKU 대/소문자 구분을 추가 및 제거하는 등 빠른 주문 기능에 대한 여러 문제를 수정합니다.
* **MDVA-27664** (*Adobe Commerce >=2.3.4 &lt;2.3.6>*) - 오류를 표시하는 고객 등록 양식의 문제를 수정합니다. *오류 - 생년월일이 오늘보다 크지 않아야 합니다.*
* **MDVA-33970** (*Adobe Commerce >=2.3.4 &lt;2.4.2>*) - 가격 속성의 범위가 웹 사이트로 설정된 경우 대변 메모에 잘못된 통화 기호가 있는 문제를 수정합니다.
* **MDVA-33992** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 체크아웃 중에 잘못 표시되는 B2B 특별 가격 책정 문제를 수정합니다.
* **MDVA-34100** (*Adobe Commerce용 >=2.3.4 &lt;2.4.2(B2B 확장 포함)*) - 회사 구조 페이지에서 회사 계정을 만들 수 없는 문제를 수정합니다.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2>*) - CSV 파일에서 제품을 가져온 후 중복된 이미지에 대한 문제를 수정합니다.
* **MDVA-33382** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 카테고리에서 제품을 제거한 후 인덱서 무효화에 대한 문제를 수정합니다.
* **MDVA-28511** (*Adobe Commerce >=2.3.5 &lt;2.3.6>*) - 완료할 수 없는 문제를 해결했습니다. [!DNL PayPal] 이름 필드에 특정 문자(예: 악센트 부호가 있는 대문자)가 포함되어 있는 경우 체크 아웃.
* **MDVA-31519** (*Adobe Commerce >=2.3.5 &lt;2.3.6>*) - 사이트 전체 판매 규칙이 사용 중일 때 게스트 체크아웃의 대기 시간 초과와 관련된 문제를 수정합니다.
* **MDVA-33281** (*Adobe Commerce >=2.3.4 &lt;2.3.6>*) - 에서 치명적인 오류가 발생하는 문제를 수정합니다 `inventory:reservation:list-inconsistencies` 잘못된 SKU 매개 변수 유형으로 인해
* **MDVA-24201** (*Adobe Commerce >=2.3.0 &lt;2.3.5>*) - 수동으로 다시 색인화할 때까지 가격이 예약된 장바구니 가격 규칙을 반영하지 않는 문제를 수정했습니다.
* **MDVA-32694** (*Adobe Commerce >=2.3.0 &lt;2.3.6> || >= 2.4.0 &lt;2.4.2*) - 관리자가 기본 저장소가 아닌 경우 협상가능한 견적에 제품을 추가할 수 없는 문제를 수정합니다.
* **MDVA-33516** (*Adobe Commerce >=2.3.0 &lt;2.3.6>*) - 구매요청 목록에서 번들 제품을 편집하면 오류가 발생하는 문제를 수정합니다.
* **MDVA-33975** (*Adobe Commerce >=2.3.4 &lt;2.4.2>*) - GraphQL 요청의 가격 계산과 관련된 여러 문제가 수정되었습니다.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 의 문제를 수정합니다. [!DNL PayPal] 결제 보고서를 사용할 수 없습니다. **보고서** > **영업** > **[!DNL PayPal]** 예상된 해결입니다.
* **MCP-87** (*Adobe Commerce >=2.3.1 &lt;2.4.2>*) - 큰 프로필에 대한 카테고리 제품 및 스톡 인덱서의 인덱스 시간이 개선되었습니다.
* **MDVA-33106** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 재조정된 제품 변경 사항이 충돌 후 삭제되는 문제를 수정합니다 `run` 명령이 실행됩니다.
* **MDVA-19391** (*Adobe Commerce >=2.3.0 &lt;2.3.5>*) - 다음 위치의 문제를 수정합니다. `analytics_collect_data` 에서 NULL 설명 레코드로 인해 오류가 발생합니다. `catalog_category_entity_text` 테이블.
* **MDVA-20376** (*Adobe Commerce >=2.3.2 &lt;2.3.4*) - 의 문제를 수정합니다. *customerId = 1인 해당 엔티티가 없음* 오류: `exception.log` 주문 배치 후 로그인한 고객.
* **MDVA-23764** (*Adobe Commerce >=2.3.2 &lt;2.3.5>*) - 의 버그를 수정합니다 `JsFooterPlugin.php` 동적 블록의 표시에 영향을 줍니다.
* **MDVA-13203** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - *무결성 제약 위반 search_tmp_ 테이블* 전체 재색인화 후 오류가 표시됩니다.
* **MDVA-23426** (*Adobe Commerce >=2.3.3 &lt;2.3.5>*) - Adobe Commerce에서 보낸 알림 이메일에 첨부 파일로 추가되는 컨텐츠가 있는 빈 본문이 포함되는 문제를 수정합니다.
* **MDVA-22150** (*Adobe Commerce >=2.3.1 &lt;2.3.4>*) - 장바구니에 구성 가능한 제품이 있고, 관리자가 구성 가능한 제품을 비활성화한 경우 쿠폰이 적용된 고객이 로그인할 수 없는 문제를 해결했습니다.
* **MDVA-32545** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 관리자로부터 주문을 생성할 때 송장이 자동으로 전송되지 않는 문제를 수정합니다.
* **MDVA-32714** (*Adobe Commerce >=2.3.4 &lt;2.4.1*) - GraphQL 제품 쿼리에서 고객 그룹 가격이 작동하지 않는 문제를 수정했습니다.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*Adobe Commerce >=2.3.2 &lt;2.4.2>*) - 를 추가합니다. *소계(Incr) 세금)* 가격 규칙 조건에 대한 옵션.
* **MDVA-31236** (*Adobe Commerce >=2.4.0 &lt;2.4.2>*) - 사용자 지정 리소스 액세스 권한이 있는 관리자가 2FA를 설정하거나 로그인할 수 없는 문제가 수정되었습니다.
* **MDVA-30845** (*Adobe Commerce >=2.3.5 &lt;2.3.7>*) - *죄송합니다. 현재 이 주문에 사용할 수 있는 견적이 없습니다* UPS XML/USPS/DHL에 연결하지 못할 경우 오류가 표시되고 다른 배송 방법이 없습니다.
* **MDVA-32133** (*Adobe Commerce >=2.4.0 &lt;2.4.1>*) - 특정 경우에 미디어 갤러리가 페이지 빌더에서 로드되지 않는 문제를 수정합니다.
* **MDVA-12304** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 최대 쿠키 수를 50개에서 200개로 늘립니다.
* **MDVA-32632** (*Adobe Commerce >=2.3.2 &lt;2.3.5>*) - 주문이 결제 시스템에 표시되지만 Adobe Commerce에는 표시되지 않는 문제를 수정합니다.
* **MDVA-32449** (*Adobe Commerce >=2.3.0 &lt;2.3.6> || 2.4.0 || >=2.4.1 &lt;2.4.2(B2B 확장 포함)*) - 주문 내역이 매우 느리게 로드되거나 전혀 로드되지 않는 문제를 수정합니다.
* **MDVA-32739** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 비동기 이메일 알림 을 활성화하면 이전 판매 이메일이 전송되는 문제를 수정합니다.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*Adobe Commerce 2.3.6의 경우, 2.4.1*) - *계정 만들기* 단추에서 잘못된 데이터를 수정한 후 계속 비활성화됩니다. *새 고객 계정 만들기* 양식.
* **MDVA-31006** (*Adobe Commerce 2.3.0용, 2.3.1용*) - [!DNL Paypal Express] 결제.
* **MDVA-25602** (*Adobe Commerce 2.3.0*) - 수정 사항 [!DNL PayPal Payflow Pro] 결제 방법 및 쿠키를 `SameSite=Lax` 기본적으로 Chrome 80 브라우저 및 API 응답에서 고객 로그인 페이지로 리디렉션됩니다.

## v1.0.10 {#v1-0-10}

패치 버전에 대한 사소한 수정 사항

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*Adobe Commerce >=2.3.2 &lt;2.4.2>*) - 쿠폰이 있는 장바구니 가격 규칙이 GraphQL을 통해 적용되지 않는 문제가 수정되었습니다 *전체 장바구니에 대한 고정 금액 할인* 작업이 사용됩니다.
* **MDVA-30889** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 가상 및 간단한 제품을 사용하여 번들을 옵션으로 발행하면 오류가 발생하는 문제를 수정합니다.
* **MDVA-31791** (*Adobe Commerce >=2.3.4 &lt;2.3.5>*) - Target 규칙 또는 연결된 제품을 사용할 때 제품 페이지의 성능을 향상시킵니다.
* **MDVA-31168** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 제품 내보내기 CSV 파일이 표시되지 않고 메모리 할당 오류가 발생하는 문제를 수정했습니다.
* **MDVA-32313** (*Adobe Commerce >=2.3.0 &lt;2.3.4>*) - 구성 가능한 제품을 잘못된 구성 옵션으로 위시목록에 추가할 수 있는 문제를 수정합니다.
* **MDVA-31759** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 제품이 *드롭다운* 및 *텍스트 영역* CSV 가져오기 중 속성 값을 표시합니다.
* **MDVA-32012** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 한국 및 아르헨티나의 우편 번호를 확인할 수 없는 문제를 수정합니다.
* **MDVA-31640** (*Adobe Commerce >=2.3.1 &lt;2.3.6> || >=2.4.0 &lt;2.4.1*) - REST API를 통해 특별 가격을 업데이트할 수 없는 문제를 수정했습니다.
* **MDVA-28651** (*Adobe Commerce >=2.3.0 &lt;2.3.6> || B2B 확장이 있는 2.4.0*) - REST API를 통해 협상 가능한 견적을 로드할 때 성능 문제가 발생하는 문제를 수정합니다.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*Adobe Commerce용 >=2.3.0 &lt;2.4.1(B2B 확장 포함)*) - 대변 메모 그리드에 잘못된 통화 기호가 표시되는 문제를 수정합니다.
* **MDVA-31295** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 부분 순서가 완료되고 항목에 세금이 부과될 때 보상 점수가 계산되지 않는 문제를 수정합니다.
* **MDVA-30112** (*Adobe Commerce >=2.3.4 &lt;2.4.2>*) - 주문 수가 *다발 크기* value, Adobe Commerce은 주문을 *보류 중* 상태는 일치하지 않습니다.
* **MDVA-31150** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - Rest API 호출에 의해 송장이 게시되고 저장 신용 및 기프트 카드 계정에 의해 주문이 부분적으로 지급된 경우, GET 송장 rest API 호출에 의해 스토어 신용 및 기프트 카드 잔액이 반환되지 않는 문제를 수정합니다.
* **MDVA-30963** (*Adobe Commerce >=2.3.2 &lt;2.4.2>*) - 제품 필터링 결과가 에 지정된 값만 포함하도록 설정된 문제를 수정합니다 *모든 스토어 보기* 관리자의 범위에서 저장소 보기 수준에서 재정의된 값이 있는 제품을 포함합니다.
* **MDVA-29954** (*Adobe Commerce >=2.3.0 &lt;2.3.6> || 2.4.0 || 2.4.2(B2B 확장 포함)*) - *새 회사 등록 요청* 및 *회사에 연결되었습니다.* 이메일이 잘못된 주소에서 전송됩니다.
* **MDVA-28357** (*Adobe Commerce >=2.3.2 &lt;2.3.6> || >=2.4.0 &lt;2.4.1*) - 표준 분석기를 사용자 정의 분석기로 대신하며 [!DNL ElasticSearch] 와일드카드 검색 쿼리가 하이픈(&quot;-&quot;)을 포함하는 SKU에서 작동되도록 하는 색인입니다.

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 사용자 지정 주문 상태가 (으)로 변경된 문제를 해결했습니다 *처리 중* WebApi를 사용하여 부분적 출하를 만든 후.
* **MDVA-30428** (*Adobe Commerce >=2.3.4 &lt;2.3.5>*) - 이 제품이 사용자 지정 인벤토리 소스에 지정된 경우 고객이 원하는 목록에 제품을 추가할 수 없는 문제를 수정했습니다.
* **MDVA-30594** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - FTP가 구성된 경우 체크아웃 중에 여러 주소가 있는 주문을 저장할 수 없는 문제가 수정되었습니다.
* **MDVA-29148** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - API 호출을 통해 제품을 만들 때 다음의 제품 사용자 지정 속성인 문제를 수정합니다 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (다중 선택과 마찬가지로) 페이로드에 값이 제공되지 않은 경우 해당 기본값이 사용되지 않습니다.
* **MDVA-30837** (*Adobe Commerce >=2.3.1 &lt;2.3.5>*) - 구성 설정을 추가했습니다. *금액에 세금 포함: 예/아니오* 사용 가능한 운송 방법 구성에서 사용할 수 있습니다. When *금액에 세금 포함* 가 로 설정되어 있습니다. *예*, 최소 주문 금액은 소계 + 세제로 계산됩니다. When *금액에 세금 포함* 가 로 설정되어 있습니다. *아니요*, 최소 주문 금액은 소계에 따라 계산됩니다
* **MDVA-25028** (*Adobe Commerce >=2.3.2 &lt;2.3.3> || >=2.3.5 &lt;2.3.6*) - 을 사용하여 주문이 이행되었을 때 발생하는 문제를 수정합니다 [!DNL PayPal Payflow Pro] 위조 필터가 트리거될 때 사기 혐의가 있는 상태로 설정되지 않습니다.
* **MDVA-31224** (*Adobe Commerce >=2.3.3 &lt;2.3.5>*) - 의 성능을 향상시킵니다. `catalog_product_price` 번들 제품에 대한 다시 색인화 작업.
* **MDVA-31321** (*Adobe Commerce >=2.3.2 &lt;2.3.5>*) - 다음의 경우 빈 페이지(오류)를 수정합니다. *모두 표시* 이 선택되어 있습니다. [!DNL Elasticsearch] 제품 id의 큰 목록을 반환합니다. 이 시나리오에서는 order by 절이 잘못된 SQL 형식으로 변환됩니다.
* **MDVA-30815** (*Adobe Commerce >=2.3.2 &lt;2.3.4*) - 검색 결과 페이지에 표시할 검색 결과 수를 변경하면 Adobe Commerce에 빈 페이지가 표시되는 문제를 수정합니다. [!DNL Elasticsearch] 이제 표시된 페이지당 검색 결과 수를 변경하면 카테고리 페이지의 결과가 올바르게 표시됩니다.
* **MDVA-30782** (*Adobe Commerce >=2.3.5 &lt;2.4.2>*) - 장바구니 규칙과 관계없이 다이내믹 블록이 표시되는 문제를 수정합니다.
* **MDVA-31021** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 에 성능 문제가 있는 문제를 수정합니다 `module-catalog-import-export/Model/Import/Product/Option.php`. 에 ~100k 이상의 레코드가 있는 경우 `catalog_product_option` 표의 경우, 단일 제품이 있는 새 CSV의 유효성을 검사하는 데 10초 미만의 시간이 소요됩니다.
* **MDVA-31007** (*Adobe Commerce >=2.4.0 &lt;2.4.1>*) - 사용자 지정 주소 속성이 내 계정 영역 및 백엔드의 주문 세부 사항 페이지에 올바르게 표시되지 않는 문제를 수정합니다.
* **MDVA-29389** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 다음 위치에서 고급 보고 문제를 해결했습니다. `analytics_collect_data` cronjob은 다음과 같이 말합니다. *포트는 호스트 매개 변수(예: localhost:3306)에서 구성해야 합니다.*.
* **MDVA-31343** (*Adobe Commerce >=2.3.4 &lt;2.3.6>*) - 제거된 본문 클래스의 문제를 수정합니다 `page-layout-category-full-width` 카테고리를 예약하는 경우.
* **MDVA-30945** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 장바구니를 업데이트할 때 치명적인 오류 메시지가 표시되는 문제를 수정합니다 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*Adobe Commerce >=2.3.4 &lt;2.4.0*) - 를 구현합니다 *최소값은 일치해야 함* 기능 및 부분 검색 [!DNL Elasticsearch] 엔진. 검색 쿼리에서 하이픈 문제를 해결합니다.
* **MDVA-30102** (*Adobe Commerce >=2.3.2 &lt;=2.4.0*) - 레이아웃 캐시에 TTL이 없으므로 Redis 캐시가 빠르게 증가하는 문제를 수정합니다.
* **MDVA-30599** (*Adobe Commerce >=2.3.4 &lt;=2.4.0*) - API를 사용하여 만든 고객 따옴표가 로그인한 고객에 대한 따옴표로 잘못 표시되는 문제를 해결했습니다.
* **MDVA-29446** (*Adobe Commerce >=2.3.3 &lt;=2.4.0*) - 적용 불가능한 배송 방법의 가격이 체크아웃 중에 0으로 표시되는 문제를 수정합니다.
* **MDVA-30357** (*Adobe Commerce >=2.3.2 &lt;=2.4.0*) - 크론별로 사이트 맵을 생성할 때 잘못된 이미지 URL이 생성되는 문제를 수정합니다.
* **MDVA-30565** (*Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - 다음 위치의 문제를 수정합니다. *Cartid = 0인 해당 엔티티가 없습니다.* 영구 장바구니가 활성화된 경우 storefront 체크아웃 시 게스트 고객에 대해 오류가 표시됩니다.
* **MDVA-29787** (*Adobe Commerce >=2.3.0 &lt;=2.4.0*) - 관련 제품에 대한 target 규칙이 작동하지 않는 문제를 수정했습니다 *다음 중 하나임* 조건은 표시할 제품을 정의하는 데 사용됩니다.
* **MDVA-30977** (*Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - 재색인화 후 카테고리에서 누락된 무작위 제품이 발생하는 문제를 수정합니다.
* **MDVA-28202** (*Adobe Commerce >=2.3.4 &lt;=2.4.2*) - MSI를 사용할 때 계층 구조 탐색이 구성 가능한 제품을 올바르게 필터링하지 않는 문제를 해결했습니다.
* **MDVA-28300** (*Adobe Commerce >=2.3.0 &lt;2.3.6>*) - GQL 요청이 카탈로그 가격 규칙의 가격 변경 사항을 반영하지 않는 문제를 수정합니다.
* **MDVA-31006** (*Adobe Commerce >=2.3.2 &lt;=2.4.2*) - [!DNL Paypal Express] 결제.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*Adobe Commerce >=2.3.4 &lt;2.3.6> || 2.4.0*) - 레이어 탐색과 관련된 문제를 수정합니다. 여기서 *아니요* 부울 유형 제품 속성에 대한 값이 [!DNL Elasticsearch] 은 검색 엔진으로 사용됩니다.
* **MDVA-28191** (*Adobe Commerce >=2.3.3 &lt;2.4.2>*) - 관리자를 통해 주문 생성 중에 결제 방법이 로드되지 않는 문제를 수정합니다.
* **MDVA-29959** (*Adobe Commerce >=2.3.0 &lt;=2.3.3-p1(B2B 확장 포함)*) - 제한된 관리자 사용자가 *회사* 회사 계정을 삭제할 수 있는 권한이 없습니다.
* **MDVA-30265** (*Adobe Commerce >=2.3.3 &lt;2.4.2>*) - 송장 생성 후 선적 추적 링크가 작동하지 않는 문제를 수정합니다.
* **MDVA-28409** (*Adobe Commerce >=2.3.4 &lt;2.3.6> || 2.4.0*) - `sales_clean_quotes` cron 작업이 *메모리 부족* 데이터베이스의 만료된 따옴표 수가 큰 경우 오류가 발생합니다.
* **MDVA-30593** (*Adobe Commerce >=2.3.0 &lt;2.3.4>*) - 견적 수명 설정에 따라 만료된 견적이 정리되지 않는 문제를 수정합니다.
* **MDVA-30107** (*Adobe Commerce >=2.3.0 &lt;2.3.6>*) - 저장소 보기에 다른 기본 URL을 사용하는 경우 저장소 전환기가 예상대로 작동하지 않는 문제를 해결했습니다.
* **MDVA-28763** (*Adobe Commerce >=2.3.2 &lt;2.3.4*) - REST API를 사용하여 제품 정보를 두 번 이상 업데이트한 후 제품 이미지가 복제되는 문제를 수정했습니다.
* **MDVA-30284** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 다음 이유로 인해 카탈로그 검색 색인이 실패하는 문제를 해결했습니다 *[!DNL Elasticsearch]오류: 인덱스의 총 필드 제한을 초과했습니다.*
* **MDVA-29042** (*Adobe Commerce >=2.3.3 &lt;=2.3.4-p2(B2B 확장 포함)*) - 카탈로그 권한이 *허용* 공유 카탈로그에 새 제품이 추가된 후 자동으로 적용됩니다.
* **MDVA-30428** (*Adobe Commerce >=2.3.3 &lt;2.4.2>*) - 이 제품이 사용자 지정 인벤토리 소스에 지정된 경우 고객이 원하는 목록에 제품을 추가할 수 없는 문제를 수정했습니다.
* **MDVA-28661** (*Adobe Commerce용 >=2.3.0 &lt;2.4.2(B2B 확장 포함)*) - 회사 관리자가 변경된 후 회사 사용자 회사 계정 섹션에서 오류가 발생하는 문제를 수정합니다.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*Adobe Commerce 2.3.1 - 2.3.4-p2*) - 데이터베이스 이름이 너무 길어 프런트 엔드에서 카테고리가 업데이트되지 않는 경우 로그온 작업이 실패하는 문제를 수정합니다.
* **MDVA-30106** (*Adobe Commerce ^2.3.0*) - 체크아웃 중에 *null의 &#39;length&#39; 속성을 읽을 수 없습니다.* 오류가 발생했습니다.
* **MDVA-28656** (*Adobe Commerce >=2.3.1 &lt;2.3.6> || >=2.4.0 &lt;2.4.2*) - 주문 시 지급 정보가 필요하지 않은 경우(예: 100% 할인 포함) 주문 시 송장이 생성되어 주문 상태가 *닫힘* 완료 대신.
* **MDVA-30209** (*Adobe Commerce 2.3.0 - 2.3.3-p1*) - 고객이 계정 정보를 업데이트한 경우 고객 그룹이 기본값으로 변경된 문제를 수정합니다.
* **MDVA-30123** (*Adobe Commerce >=2.3.4 &lt;2.4.2>*) - GraphQL 쿼리에 대해 속성 옵션 레이블이 올바르게 번역되지 않는 문제를 수정했습니다.
* **MDVA-29996** (*Adobe Commerce >=2.3.3 &lt;2.4.2>*) - 카테고리 권한을 활성화한 후 카테고리 페이지가 전체 페이지 캐시에 의해 캐시되지 않는 문제를 수정합니다.
* **MDVA-30164** (*Adobe Commerce >=2.3.1 &lt;2.4.2>*) - 사용자 지정 고객 특성이 있는 경우 고객 그리드에서 고객 레코드를 내보낼 수 없는 문제를 해결했습니다.
* **MDVA-30444** (*Adobe Commerce >=2.3.0 &lt;2.4.1*) - GraphQL을 사용하여 수행한 주문에 대해 확인 이메일이 전송되지 않는 문제를 수정합니다.
* **MDVA-30490** (*Adobe Commerce 2.3.4 - 2.3.5-p2*) - 제품 중 하나에 짧은 설명이 비어 있는 경우 제품 비교에서 500 오류 페이지를 표시하는 문제를 수정합니다.
* **MDVA-30232** (*Adobe Commerce >=2.3.1 &lt;2.4.1>*) - 원래 주문에 선물 카드가 포함된 경우 다시 주문할 수 없는 문제를 수정합니다.
* **MDVA-29965** (*Adobe Commerce >=2.3.3 &lt;2.4.0>*) - 장바구니에 제품을 추가할 때 고객이 잘못된 양식 키 오류를 발생하는 문제를 수정했습니다.
* **MDVA-30008** (*Adobe Commerce >=2.3.0 &lt;2.4.2>*) - 공개 카탈로그에 있는 제품에 대한 관리 API를 통해 주문을 할 수 없는 B2B 문제를 수정합니다.
* **MDVA-22469** (*Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Adobe Commerce 2.3.3으로 업그레이드한 후 관리 패널에서 페이지 빌더가 작동하지 않고 일부 JS 및 CSS 파일이 로드되지 않는 문제를 수정합니다.
* **MC-35984** (*Adobe Commerce >=2.4.0 &lt;2.4.1>*) - RMA(Return Products Authorization)에 대한 배송 레이블을 생성한 후 상인이 반품 페이지의 페이지 요소와 상호 작용할 수 없는 문제를 수정합니다.

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*Adobe Commerce 2.3.0용 - 2.3.4용*) - 의 문제를 수정합니다. [!DNL PayPal Payflow Pro] 결제 방법 및 쿠키를 `SameSite=Lax` 기본적으로 Chrome 80 브라우저 및 API 응답에서 고객 로그인 페이지로 리디렉션됩니다.
* **MDVA-26694** (*Adobe Commerce >=2.3.0 &lt;2.3.6> || 2.4.0*) - 다르게 만료되도록 예약되어 있지만 매일 만료되는 제품 및 카탈로그 캐시 문제를 수정합니다.
* **MDVA-27825** (*Adobe Commerce >=2.3.0 &lt;2.4.1*) - 메모리 누출로 인해 대량의 데이터를 내보내지 못하는 문제를 해결했습니다.
* **MDVA-29085** (*Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - 회사가 API로 만들어지는 경우 필수 새 회사 이메일이 전송되지 않는 B2B 문제를 수정합니다.
* **MDVA-29344** (*Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - 헤더 요소에서 텍스트 요소로 텍스트를 복사한 후 페이지 빌더가 중지되는 문제를 수정합니다.
* **MDVA-29835** (*Adobe Commerce >2.3.1 &lt;2.4.2>*) - 기프트 카드 주문에 하나의 코드가 아닌 두 개의 코드가 포함되어 있는 문제를 수정합니다.
* **MDVA-30052** (*Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - 개인 컨텐츠(로컬 저장소)를 올바르게 채우지 않아 성능 문제가 발생하는 문제를 수정합니다.
* **MDVA-30131** (*Adobe Commerce >=2.3.4 &lt;2.3.6> || 2.4.0*) - 레이어 탐색과 관련된 문제를 수정합니다. 여기서 *아니요* 부울 유형 제품 속성에 대한 값이 [!DNL Elasticsearch] 은 검색 엔진으로 사용됩니다.
* **MDVA-35514** (*Adobe Commerce >=2.4.0 &lt;2.4.1>*) - 배송 레이블을 만들고 패키지 만들기 모달 창에서 패키지에 순서가 지정된 제품을 추가하는 문제를 수정합니다.
