---
title: 요구 사항 확인 목록
description: 이 포괄적인 질문 목록을 사용하여 Adobe 상거래 구현을 준비할 수 있습니다.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 0%

---


# 요구 사항 확인 목록

다음 질문은 조직의 준비 상태를 확인하기 위해 어떤 정보를 문서화해야 하는지 확인하는 시작점 역할을 할 수 있습니다. RFP를 개발할 때도 도움이 될 수 있습니다.

## 비즈니스

- What are the business goals for the new ecommerce platform?

- 현재 전자 상거래 플랫폼을 변경하는 이유는 무엇입니까?

- 웹 사이트 인프라의 목표는 무엇입니까?

- 새로운 전자 상거래 플랫폼을 제공하는 기간은 얼마입니까?

- 이 프로젝트에 몇 명의 IT 프로젝트 관리자가 할당됩니까?

- 이 프로젝트에 몇 명의 비즈니스 분석가가 지정됩니까?

- 이 프로젝트에 몇 명의 기술 분석가가 지정됩니까?

- 이 프로젝트에 지정되는 HTML 개발자는 몇 명입니까?

- 현재 비즈니스 프로세스에 대한 설명서는 무엇입니까?

- 현재 시스템 통합에 대한 설명서는 무엇입니까?

- 현재 프로세스 플로우에 대한 설명서는 무엇입니까?

- 현재 데이터 흐름에 대한 설명서는 무엇입니까?

- 누가 교육을 제공합니까?

- 라이브로 전환하기 전에 어떤 교육을 완료할 예정입니까?

- 생중계 후에는 어떤 교육이 완료됩니까?

- go-live 후 어떤 Adobe 상거래 지원이 필요합니까?

- 이 프로젝트는 다른 시스템 개발 프로젝트에 종속되어 있습니까?

- 향후 12개월에서 24개월 동안 매출이 증가한다는 것은 어떻게 보십니까?

- 주요 경쟁자는 누구입니까? 해당 사이트에 대한 링크를 제공하십시오. 온라인 경험을 경쟁업체와 어떻게 차별화하시겠습니까?

- Where do you see future growth coming from in your business?

- What role does digital commerce play in your business strategy? 이 클라우드 플랫폼 설정을 위한 주요 목적은 무엇입니까?

- 옴니채널 비즈니스 성장 방법에 대한 참조로 가져오는 브랜드/회사가 있습니까?

- 어떤 팀이나 개인이 전자 상공 전략을 추진하고 있습니까? Describe the relevant positions.

## Current platform

- How is the current platform being hosted: Internal, hosting provider, private cloud servers, or hosted cloud servers?

- Which environments does the current platform have: development, QA, pre-production, production?

- 개발 환경에 있는 웹 및 데이터베이스 서버는 몇 개입니까?

- QA 환경에 있는 웹 및 데이터베이스 서버는 몇 개입니까?

- 스테이징(사전 프로덕션) 환경에 있는 웹 및 데이터베이스 서버는 몇 개입니까?

- How many web and database servers are in the production environment?

- 로드 밸런싱이 있는 다중 서버 아키텍처입니까?

- Is it a high-availability system architecture?

- 현재 웹 사이트에서 어떤 문제를 겪고 있습니까?

- 현재 카탈로그 크기(SKU 수)?

- Average visitors per day?

- 시간당 평균 동시 세션 수

- Average page views per day?

- 시간당 평균 주문 수 및 일일 주문 수?

## 필요한 플랫폼 요구 사항

- 어떤 Adobe 상거래 버전을 사용합니까?

- 향후 플랫폼은 어떻게 호스팅됩니까? 내부, 호스팅 공급자, 비공개 클라우드 서버 또는 호스팅된 클라우드 서버?

- Which environments will the future platform have: development, QA, pre-production, production?

- 개발 환경에 포함되는 웹 및 데이터베이스 서버 수는 몇 개입니까?

- 고가용성 시스템 아키텍처가 됩니까?

- 몇 명의 Adobe Commerce 관리자가 있습니까?

- 카탈로그 크기(SKU 수)가 예상됩니까?

- 일일 평균 방문자가 예상됩니까?

- Expected average concurrent sessions per hour?

- 일별 평균 페이지 보기 수가 예상됩니까?

- 이전 사이트에서 새 사이트로 가져올 데이터는 무엇입니까? (예: product, customer, order history)

## Websites

- 몇 개의 국내 웹사이트가 구현될 예정입니까?

- Which languages will be implemented?

- 몇 개의 국제 웹사이트를 구현할 예정입니까?

- 웹 사이트는 어떤 지역을 지원합니까?

- 어떤 언어가 구현됩니까?

- 어떤 통화가 구현됩니까?

- 각 국가에 대한 배송 서비스 수준 계약이 있습니까?

- 각 국가의 게재 공급자는 어디입니까?

- 각 국가의 세무사는 누구입니까?

- 맞춤형 국제 웹사이트 테마가 필요합니까?

- 주로 B2C 또는 B2B 사이트입니까? B2B2B 또는 B2B2C 요소가 있습니까?

- 기존 디자인이 채택되어 있습니까, 아니면 플랫폼이 처음부터 디자인될 예정입니까?

- 헤드리스 상거래(별도의 프런트 엔드 및 백엔드 계층)에 대한 요구 사항이 있습니까?

- 반응형 디자인을 위한 중단점(태블릿/모바일)은 무엇입니까?

- 모바일 앱에 요구 사항이 있습니까? PWA을 모바일 프런트 엔드에 활용해야 합니까?

- 테스트해야 하는 특정 브라우저(표준 브라우저 IE9+, Firefox, Chrome, Safari 제외)만 있습니까?

- 각 프런트 엔드의 언어는 무엇입니까? 번역된 콘텐츠를 사용할 수 있습니까, 아니면 지원이 필요합니까?

- 여러 개의 웹 사이트가 있습니까? 그럴 경우 고객은 모든 사이트에서 자신의 자격 증명을 사용할 수 있습니까?

- 제품 데이터가 모든 사이트에서 공유됩니까?

- 디자인에서 사이트로의 변경이 있습니까?

- 구독 옵션이 있으며 구독자를 어떻게 관리합니까?

- 특정 SEO 요구 사항이 있습니까? 검색 엔진 마케팅은 어떻게 관리됩니까?

## 통합

- Which CMS system will be integrated withAdobe Commerce? (예: WordPress, Drupal, Concrete5)

Are there existing APIs that can be used?

- Has system-error handling been designed and developed for this third-party-system integration?

- 어떤 ERP 시스템을 Adobe Commerce와 통합합니까? (Examples: SAP, MS Dynamics NAV)

- Which shipping carrier system will be integrated withAdobe Commerce?

- 어떤 세금 소프트웨어 시스템이 Adobe Commerce와 통합됩니까? (예: 분류기)

- From which system will product data be imported intoAdobe Commerce?

- 가져온 제품 데이터 로드 빈도

- Adobe Commerce는 제품 데이터를 어떤 시스템으로 내보내나요?

- 내보낸 제품 데이터 로드 빈도

- 어떤 시스템에서 데이터를 Adobe Commerce로 가져올 수 있습니까?

- 가져온 주문 데이터 로드 빈도

- Into which system willAdobe Commerceexport order data?

- 내보낸 주문 데이터 로드 빈도입니까?

- 어떤 분석 플랫폼이 사용됩니까? (예: Adobe Analytics, Google Analytics)

- Will there be single sign on and social network sharing? If so, which social networks?

- Is there any rewards or loyalty programs in place? 보상을 위해 POS 시스템과 통합되는 것이 있습니까?

- How are product returns handled? 고객이 온라인으로 반환 요청을 기록해야 합니까?

- 온라인 채팅 도구가 필요합니까? Is a chatbot needed?

- 사이트에서 어떤 결제 게이트웨이를 제공하시겠습니까?

- 어떤 주문 관리 시스템이 Adobe Commerce와 통합됩니까? (예: Microsoft Dynamics, SAP, Retail Pro)

- Adobe Commerce와 통합되는 제품 인벤토리 관리 시스템은 무엇입니까? (예: Akeneo, InRiver, Bluestone)

- Adobe Commerce와 통합되는 고객 관계 관리 시스템은 무엇입니까? (예: Hubspot, Salesforce, Klaviyo)

## Adobe 상거래 관련 기능

- 어떤 종류의 A/B 테스트가 필요합니까?

- 시스템에서 사용할 수 있는 동시 관리자는 몇 명입니까?

- Will you allow a customer to pick up items purchased on the website at a store?

- Will you have promotional pages?

- 마케팅 배너가 있나요?

- CMS 페이지에서 비디오를 재생하시겠습니까?

- 콘텐츠를 수정하거나 업데이트하는 빈도는 얼마입니까?

- 어떤 유형의 콘텐츠가 로드됩니까?

- 콘텐츠 업데이트를 예약할 예정입니까?

- 컨텐츠 스테이징 웹 사이트가 필요합니까?

- 고객이 웹 사이트 계정을 만들 수 있어야 함

- 판촉에 고유 할인 쿠폰을 사용하시겠습니까?

- Will you have promotional pricing?

- 유연한 쿠폰(웹 사이트, 고객 그룹, 시간, 카테고리 또는 제품별로 설정할 수 있는 기능)이 있습니까?

- 단일 품목에 대해 퍼센트 할인이 제공됩니까?

- 어떤 종류의 선물 기능이 필요합니까?

- 보상 프로그램 기능이 필요합니까?

- 뉴스레터 기능이 필요합니까?

- 고객이 이전 주문을 조회하고 교환할 품목을 선택할 수 있도록 허용하시겠습니까?

- 고객이 웹사이트 주문 취소를 시작하도록 허용할 건가요?

- 고객이 웹 사이트에서 항목 교환을 시작할 수 있도록 허용하시겠습니까?

- 실시간 주소 확인이 필요합니까?

- 고객이 웹 사이트에서 항목 반품을 시작하도록 허용하시겠습니까?

- Adobe 상거래에 반품 RMA가 발급됩니까?

- Adobe Commerce에서 환불 정보를 캡처하시겠습니까?

- 등록된 고객에 대해 온라인 주문 추적이 필요합니까?

- 게스트 고객을 위해 온라인 주문 추적이 필요합니까?

- 주문 배치 중에 온라인 인증 및 캡처 실행

- 지연된 캡처가 있는 주문 배치 중 위조 필터가 있는 인증

- 전체 지급(승인 아님)을 받을 일 수

- 인증 만료에 대해 캡처 및 실행하시겠습니까?

- Authorize.net

- Braintree

- PayPal Express

- 스토어 신용

- 플라스틱 기프트 카드

- 보상 점수

- &quot;나중에 청구서&quot; - 더 일반적으로 &quot;지금 구매, 나중에 결제&quot;라고 알려지며, 즉시 청구되지만 아직 지불되지 않았습니다

- 다양한 웹 사이트마다 제품 가격이 다를 수 있습니까?

- 다양한 제품을 비교할 수 있는 기능이 필요합니까?

- 어떤 제품을 판매하실 건가요?

- 신제품을 추가하는 빈도는 어떻게 됩니까?

- 제품 업데이트 빈도는 얼마입니까?

- 새 카테고리 또는 하위 카테고리를 만드는 빈도는 얼마입니까?

- Will &quot;Ratings and Reviews&quot; functionality be required?

- Will you allow customers to recommend a product?

- Sales: Orders, tax, invoiced, shipping, refunds, coupons, PayPal settlement reports

- 장바구니: 장바구니, 버려진 예술 제품

- Products: Bestsellers, products ordered, most viewed, lowstock, downloads

- 고객: 신규 계정,고객별 주문 합계,고객별 주문 수,고객 세그먼트,고객 평가

- 제품 검토

- Tags: Customers, products, popular

- 검색어

- 초대: 일반, 고객, 주문 전환율

- Will you need Adobe Commerce to generate reports based on coupon usage data?

- 판매 데이터를 기반으로 보고서를 생성하려면 Adobe 상거래 계정이 필요합니까?

- 사용자 지정 Adobe 커머셜 포트가 필요합니까?

- 현재 SEO 전략은 무엇입니까?

- 새로운 SEO 전략은 무엇입니까?

- SEO 마이그레이션에 대한 요구 사항은 무엇입니까?

- Adobe 상거래에 고정 요금을 저장합니까?

- 부분 배송을 허용하시겠습니까?

- 배송 추적 정보를 Adobe Commerce에 저장해야 합니까?

- 국내 지역에 대한 세금 계산 규칙이 필요합니까?

- Will you require tax-calculation rules for your international regions?
