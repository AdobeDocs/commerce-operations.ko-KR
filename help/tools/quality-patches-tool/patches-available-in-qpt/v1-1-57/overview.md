---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.57'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.57에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
exl-id: 3e252a71-f35f-4046-9353-169060451ffe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.57

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.57에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.57에는 다음 패치가 포함됩니다.

1. **ACSD-57570**: 특정 저장소에 액세스할 수 있는 제한된 관리자가 제품이 할당된 모든 공유 카탈로그를 항상 볼 수 없거나 저장할 수 없는 고객을 볼 수 없어 시스템 불일치가 발생하는 문제를 해결했습니다.
1. **ACSD-58325**: 유효성 검사 오류 후에도 [!UICONTROL Import] 단추를 사용할 수 있는 문제를 해결했습니다.
1. **ACSD-59083**: _업데이트가 동시에 실행되는 경우 일부 데이터베이스 업데이트 작업으로 인해_&#x200B;기본 테이블 또는 보기를 찾을 수 없음[!DNL mview] 오류가 발생하는 문제를 해결합니다.
1. **ACSD-61622**: [!DNL FedEx] 계정 특정 비율이 응답에 없는 문제를 해결했습니다. ACSD-61622은(는) [[!DNL FedEx] 배송 방법 통합 마이그레이션에 기록된 수정 사항을  [!DNL SOAP] 에서 [!DNL RESTful API]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/fedex-shipping-method-integration-migration-soap-restful-api)&#x200B;(으)로 바꿉니다.
1. **ACSD-61895**: 루트 범주에 [!DNL GraphQL]allow *권한이 없더라도* 범주가 *allow* 권한이 있는 범주를 반환하는 문제를 해결했습니다.
1. **ACSD-62212**: [!UICONTROL Forgot Password] 전자 메일 콘텐츠가 스토어 보기의 언어로 번역되지 않는 문제를 해결했습니다.
1. **ACSD-62481**: [!UICONTROL Persistence]을(를) 사용하도록 설정한 경우에도 고객의 장바구니가 비어 있는 문제가 해결되었습니다.
1. **ACSD-62629**: [!UICONTROL Widgets]에 사용된 제품 목록이 범주 조건을 준수하지 않는 문제를 해결했습니다.
1. **ACSD-62635**: 다중 스토어 관련 제품이 [!DNL GraphQL] 제품 쿼리에 제대로 표시되지 않는 문제를 해결했습니다.
1. **ACSD-62671**: [!DNL GraphQL] 요청이 첫 번째 시도에서 최신 주소 정보를 반환하지 않는 문제를 해결했습니다.
1. **ACSD-62689**: 고객이 깊이 4 이후에 [!UICONTROL Related Product Rules] 및 [!UICONTROL Widgets]에 범주를 추가할 수 없는 문제를 해결했습니다.
1. **ACSD-62708**: [!DNL TinyMCE]에서 수정 사항을 적용한 후 관리자의 [!UICONTROL pt] 7 편집기 글꼴 크기가 [!UICONTROL px]을(를) 표시하고 [!UICONTROL ACP2E-3430]을(를) 표시하지 않는 문제를 해결했습니다. 이제 [!UICONTROL px] 대신 [!UICONTROL pt]에서 글꼴 크기를 설정할 수도 있습니다.
1. **ACSD-62758**: URL에 선택한 옵션이 포함된 경우 [!UICONTROL Configurable Product] 세부 정보 페이지에서 제품 비디오가 올바르게 렌더링되지 않는 문제를 해결했습니다.
1. **ACSD-62951**: 항목 및 합계를 포함하지 않고 [!UICONTROL Credit Memo] 전자 메일을 보내는 문제를 해결했습니다.
1. **ACSD-62965**: *LocalizedException* 메시지가 주문 배치 [!DNL GraphQL response]에 포함되지 않는 문제를 해결했습니다.
1. **ACSD-63286**: API를 통해 공유 카탈로그에 할당된 제품이 수동 색인 재지정을 실행할 때까지 상점 앞에 표시되지 않는 문제를 해결했습니다.
1. **ACSD-63326**: 관리자가 백엔드에서 주문한 후 손상된 페이지로 리디렉션되는 문제를 해결했습니다.


왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
