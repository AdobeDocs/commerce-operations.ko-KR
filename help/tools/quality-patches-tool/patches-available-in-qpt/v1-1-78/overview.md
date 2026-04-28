---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.78'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.78에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 55b1c830073eaa7bfacae9fb8e9190414d7a990c
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.78

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.78에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.78에는 다음 패치가 포함됩니다.
1. **ACP2E-4416**: 관리자에서 만들 때 고객 보상 지점이 초기화되지 않는 문제를 해결합니다.
1. **[ACP2E-4419](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419.md)**: 상점 전면에서 reCAPTCHA v2(&#39;나는 로봇이 아님&#39;) 유효성 검사를 성공한 후 체크아웃 시 기프트 카드가 올바르게 적용되지 않는 문제를 해결했습니다.
1. **ACP2E-4431**: 색인 재지정 프로세스 중에 대상 규칙과 일치하는 관련 제품이 삭제되는 문제를 해결했습니다.
1. **ACP2E-4448**: Redis가 복구된 후 Redis 중단 중에 수행된 구성 변경 내용이 반영되지 않아 오래된 값이 지속되는 문제를 해결했습니다.
1. **ACP2E-4452**: 빠른 주문 페이지의 제품 가격에 세금 표시 구성에 관계없이 세금이 포함되는 문제를 해결했습니다.
1. **ACP2E-4456**: GraphQL 돌연변이를 사용하여 주문을 취소하면 전적으로 기프트 카드로 지불된 주문이 [닫힘] 상태로 전환되지 않는 문제가 해결되었습니다.
1. **ACP2E-4507**: GraphQL 돌연변이를 통해 수행된 고객 암호 재설정 요청에 대해 암호 옵션 구성이 적용되지 않는 문제를 해결했습니다.
1. **ACP2E-4513**: 만료된 CAPTCHA 이미지가 시스템에서 삭제되지 않는 문제를 해결합니다.
1. **[ACP2E-4522](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522.md)**: 여러 장바구니 병합 또는 견적 저장 요청이 동시에 실행될 때 quote_coupins 테이블에서 간헐적인 중복 키 오류가 발생하는 문제를 해결합니다.
1. **ACP2E-4528**: 이제 슬래시(/) 문자를 허용하고 !, &quot;, # 및 ? 등의 잘못된 문자를 거부하는 고객 주소의 도시 유효성 검사 문제를 해결했습니다.
1. **ACP2E-4535**: 암호 분실 양식을 제출하면 세션이 파기 또는 재생성되며(PHPSESSID 변경) 게스트 카트가 지워지는 문제를 해결했습니다.
1. **[ACP2E-4540](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4540.md)**: Fotorama 라이브러리가 올바르게 로드되지 않아 첨부된 첫 번째 이미지만 표시되는 문제가 해결되었습니다.
1. **[ACP2E-4555](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4555.md)**: &quot;이 포함된 최신 전화 번호 문제를 해결했습니다.&quot; 또는 &quot;/&quot;의 유효성이 제대로 확인되지 않습니다.
1. **[ACP2E-4565](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4565.md)**: X-Adobe-Company 헤더가 사용될 때 회사 GraphQL 쿼리가 &quot;현재 고객이 승인되지 않음&quot;을 반환하는 문제를 해결했습니다.
1. **ACP2E-4591**: REST API를 통해 주문을 했을 때 &quot;처음 구매자&quot;와 같이 주문 수를 기반으로 한 고객 세그먼트가 업데이트되지 않는 문제를 해결했습니다.
1. **ACP2E-4609**: 일부 견적에 삭제된 제품이 포함되어 있을 때 내 견적 페이지에 견적이 표시되지 않는 문제를 해결했습니다.
1. **ACP2E-4613**: 큰 미디어 디렉터리 구조로 인해 gettree 응답이 느려져 미디어 갤러리 디렉터리 트리 로드 시간이 길어지는 문제를 해결했습니다.
1. **ACP2E-4628**: [계정 공유]가 [전역]으로 설정되어 있을 때 대문자 이메일 주소를 사용하여 고객을 가져오는 경우 정의되지 않은 배열 키 오류가 발생하는 문제를 해결했습니다.
1. **ACP2E-4665**: REST API를 통해 요청할 때 제품 갤러리에서 비디오를 포함하는 구성 가능한 제품의 하위 제품이 나열되지 않는 문제를 해결했습니다.
1. **ACP2E-4732**: 변경 로그 테이블의 version_id 열이 최대값에 도달할 때 많은 수의 업데이트가 있는 고객에 대해 부분 인덱싱이 중지되는 문제를 해결했습니다.
1. **ACP2E-4763**: 두 번 적용된 세금으로 인해 카탈로그 가격이 세금 포함으로 설정된 경우 GraphQL customerOrders 쿼리가 부풀려진 original_price_including_tax 및 original_row_total_including_tax 값을 반환하는 문제를 해결했습니다.
1. **ACSD-60989**: 선언적 스키마를 통해 외래 키로 열을 수정하면 MariaDB에 오류가 발생하는 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
