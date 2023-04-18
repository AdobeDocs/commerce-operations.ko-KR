---
title: 자체 호스팅 Adobe Commerce 보안 개념
description: '고려해야 할 자체 호스팅 보안 아이디어 및 개념과 모범 사례에 대해 알아봅니다. adobe commerce를 호스팅할 때 읽기 전용 파일 시스템, 맬웨어 스캔 및 기타 여러 항목을 고려하여 개념(예: )을 배웁니다.'
landing-page-description: Adobe Commerce을 직접 호스팅할 때 고려해야 할 몇 가지 보안 개념과 사항을 알아봅니다.
short-description: Adobe Commerce을 직접 호스팅하기 위한 전략과 보안 개념을 알아봅니다.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: cca195c20ddcba634a8fc39c0867e0ae28f43683
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---


# 보안 개념

보안은 항상 전자 상거래 프로젝트와 관련된 모든 것에 대해 강한 배려여야 합니다. 강력한 보안 상태가 없으면 공격을 받을 수 있는 표면면적이 기하급수적으로 커집니다. 제시된 개념과 아이디어는 일반적으로 활용되는 일반적인 취약점을 줄이기 위해 입증된 방법을 제공합니다.

다음 개념은 특정 순서가 아닙니다. 그것들은 고려해야 할 몇 가지 아이디어와 개념을 제공하기 위한 것입니다. 많은 구성 요소가 무료이거나 최소 설정 및 구성과 이후 모니터링이 필요합니다. 이 자습서의 외부에서 이러한 주제를 검토하여 여기에 제시된 개념을 충분히 이해할 수 있습니다.

## 읽기 전용 파일 시스템

읽기 전용 파일 시스템 개념은 [Adobe Commerce on cloud 인프라](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. 이것은 나쁜 배우가 사용하는 하나의 주요 영역을 완전히 제거한다. 많은 이점이 검색을 방지하기 위해 상거래 애플리케이션에 있을 것으로 예상되는 파일을 변경하는 것을 활용합니다. 잘못된 작업자는 파일을 만드는 대신 기존 파일의 내용을 변경하여 예기치 않은 작업을 수행합니다. 파일 시스템을 읽기 전용으로 설정하면 이 공격 벡터가 크게 줄어듭니다.

## 2단계 인증 및 암호 관리자 사용

암호를 공유하지 마십시오. 각 관리자 사용자에게는 적절한 ACL이 있는 자체 계정이 있어야 합니다. 두 요소 식별이 비활성화되거나 제거되지 않도록 하십시오. 타사에 관리자 액세스 권한을 제공하는 경우, 암호 관리자가 암호를 생성하고 다시 사용하지 않아야 합니다.

## 맬웨어 검색

맬웨어 검색은 일반적으로 Adobe Commerce을 전문으로 하는 호스팅 공급자에서 찾습니다. 알려진 맬웨어 및 업적의 이 라이브러리는 새로운 위협이 발견되고, 테스트되고, 진단됨에 따라 점점 더 증가하고 있는 목록입니다. 호스팅 공급자가 이러한 서비스를 제공하는지, 그리고 요청 시에만 자동으로 또는 실행할 수 있는지 확인하십시오. 구독할 수 있는 서비스에는 자체 알려진 악용 라이브러리를 사용하여 상거래 애플리케이션에서 지속적으로 악용을 확인할 수 있습니다. 이러한 폴더 중 일부는 외부 전용이며 일부는 인프라에 추가하여 모든 폴더, 파일 및 데이터베이스에 대한 내부 심층 검사를 제공할 수 있습니다. Sansec.io에서 Sucuri에 이르기까지, 그리고 물론 MageReport에 이르기까지 이 분야에서 수년간의 경험을 가진 몇 개의 공급자가 있습니다. 일부는 무료이고, 일부는 관련 비용을 부담합니다. 이 방법을 알고 있고 Adobe Commerce 설계자와 DevOps 팀과 심도 있는 대화를 나눌 수 있으므로 적합한 솔루션을 찾을 수 있습니다.

## 상거래를 위한 사이트 전체 분석 도구

다음 [사이트 전체 분석 도구](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} 는 Adobe Commerce 설치의 보안 및 운영을 보장하기 위한 자세한 시스템 통찰력과 권장 사항이 포함된 사전 예방적 셀프 서비스 도구 및 중앙 저장소입니다. 또한 24/7의 실시간 성능 모니터링, 보고서 및 조언을 제공하여 잠재적인 문제를 파악하여 사이트 상태, 안전 및 애플리케이션 구성을 보다 효과적으로 파악할 수 있습니다. 해상도 시간을 줄이고 사이트 안정성과 성능을 개선하는 데 도움이 됩니다.

## 관리 작업 로깅에 대한 설정 활성화 및 확인

Adobe Commerce 관리자에 로그인하고 저장소 > 구성 > 고급 > 관리 > 관리 작업 로깅으로 이동한 후에 찾을 수 있습니다. 모니터링 및 기록된 이벤트 목록이 제공됩니다. 통상 행정관에게 접근할 수 있는 혐의가 있다면, 그 혐의가 있는 지역에 대한 법의학 분석을 할 때 유용하다. 이러한 로깅 및 보고는 불량 행위자가 수행한 이벤트를 확인하는 데 도움이 될 수 있습니다. 특정 작업을 수행할 때 누군가가 처리를 위해 관리자 작업 로깅을 비활성화했을 수 있다는 표시인 관리 작업 로깅을 사용하지 않도록 설정한 경우

## ssh 액세스를 위한 Bastion Server

보안 개념 자습서의 대부분의 항목을 설명하기가 어렵습니다. ssh 액세스를 위해 중간자 역할을 하는 서버를 제공하는 것이 이 방법의 기본 방법입니다. 이렇게 하면 프로덕션 서버에서 외부 ssh 연결을 허용하지 않습니다. 이 Bastion 서버를 만들고 로컬 IP 마스크를 사용하여 지정된 서버만 이 서버에 SSH를 사용할 수 있도록 할 수 있습니다.

## ACL 역할 및 권한 검토

Adobe Commerce의 모든 관리자 사용자에게 ACL 역할이 할당됩니다. 이 역할은 작업을 수행해야 하는 기능만 제공하도록 만들어야 합니다. ACL 역할은 필요 이상으로 더 많은 권한을 제공하지 않도록 자주 평가해야 합니다. 필요한 경우 권한으로 많은 ACL 역할을 만듭니다. 액세스 권한이 타사에 부여된 경우 가능한 한 빨리 비활성화해야 합니다. 관리자 사용자를 만들 때 액세스 권한이 절대적으로 필요한 시간을 확인하고 자동 만료 날짜를 설정하도록 합니다.

## 관리자 사용자 및 SSH 사용자 액세스 감사 자주

원치 않거나 허가되지 않은 관리자 사용자 생성을 감지하려면 관리자 사용자 목록이 자주 감사되어야 합니다. 경험상 매달 Adobe Commerce 애플리케이션에 SSH 및 관리자 액세스 권한이 있는 사용자를 확인하는 것이 좋습니다. 새 사용자가 감지되면 계정을 비활성화하고 해당 사건에 대한 회사 정책과 절차를 따릅니다. 악용으로부터 복구하는 것보다 사용자 액세스를 복원하는 것이 더 쉽습니다.

## 데이터베이스 정리

프로덕션 데이터에 대한 액세스를 제한합니다. 이 지정된 팀원들은 생산 데이터베이스를 끌어내리고 실제 데이터를 정리할 수 있는 능력을 가져야 합니다. 데이터를 제거하는 것이 선택 사항인 경우 주문, 견적 및 고객과 같은 적절한 테이블을 자릅니다. 그러나 경우에 따라 전체 데이터 세트를 원하지만, 값을 익명화할 수 있습니다. 이는 일반적으로 스테이징 환경에서 true입니다. 업그레이드 전에도 유용합니다. 실제 데이터 볼륨이 있지만 익명으로 처리되면 제대로 업그레이드하기 위해 배포를 실행하는 시간을 테스트하고 확인할 수 있습니다. 제한된 데이터 세트가 있는 경우 업그레이드 프로세스 및 타이밍을 과소평가할 수 있습니다.

+++고객 정보 무작위 지정 예 Adobe Commerce에서 데이터를 저장하는 일부 표준 테이블에서 임의 문자열 및 모든 이름 및 마지막 갈기 필드로 고객 이메일 주소를 변경하는 방법에 대한 예를 소개합니다. **모든 테이블에서 중요한 데이터를 확인해야 합니다. 이 목록은 고객 데이터를 저장할 수 있는 테이블을 모두 포함하는 것은 아닙니다**

```SQL
SET FOREIGN_KEY_CHECKS=0;
UPDATE customer_entity SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE email_contact SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE sales_invoice_grid SET customer_email = 'customer@example.com', customer_name  = 'Jack Smith';
UPDATE sales_order SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Smith', remote_ip = '127.0.0.1';
UPDATE sales_order_address SET region = 'Ohio', postcode = '12345-1234', lastname = 'Smith', street = '123 Main street', region_id = 44, city = 'Phoenix', telephone = NULL, firstname = 'Jane', company = NULL;
UPDATE sales_order_grid SET customer_email = 'customer@example.com', shipping_name = 'Jack', billing_name = 'Jack Smith', billing_address = '123 Main Street', shipping_address = '321 Pine Street', customer_name = 'Jane Smith';
UPDATE sales_shipment_grid SET customer_email = 'customer@example.com', customer_name = 'Jane Smith', billing_address = '123 Main street', billing_name = 'Jack Doe', shipping_name = 'Susie Smith';
UPDATE quote SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Jones', customer_dob = NULL, remote_ip = '127.0.0.1';
UPDATE quote_address SET email = 'customer@example.com', firstname = 'Jack', lastname = 'Smith', company = NULL, street = '123 Main st', city = 'AnyCity', region = 'Some State', region_id = 44, postcode = '12345-1234', telephone = NULL;
UPDATE magento_rma SET customer_custom_email = 'customer@example.com' WHERE customer_custom_email IS NOT NULL;
UPDATE customer_address_entity SET firstname = 'Jack', lastname = 'Smith', telephone = '909-555-1212', postcode = NULL,  region = NULL, street = '123 Main street', city = 'Anycity', company = NULL;
UPDATE customer_grid_flat SET name = 'Jane Doe', email = 'customer@example.com', dob = NULL, gender = NULL, taxvat = NULL, shipping_full = '', billing_full = '', billing_firstname = 'Jack', billing_lastname = 'Smith', billing_telephone = NULL, billing_postcode = NULL, billing_country_id = NULL, billing_region = NULL, billing_street = '123 Main street', billing_city = 'Anycity', billing_fax = NULL, billing_vat_id = NULL, billing_company = NULL;
UPDATE sales_creditmemo_grid SET billing_name = 'Sally', billing_address = '123 Main Street', customer_name = 'Jack Smith', customer_email = 'customer@example.com';
    
UPDATE magento_rma_grid SET customer_name = 'Jack Smith';
SET FOREIGN_KEY_CHECKS=1;
```

+++


+++익명화하려고 하지 않고 테이블을 자를 수도 있습니다

```SQL
SET FOREIGN_KEY_CHECKS=0;
TRUNCATE customer_log;  
TRUNCATE customer_visitor;  
TRUNCATE magento_logging_event;
TRUNCATE oauth_consumer;
TRUNCATE oauth_nonce;
TRUNCATE oauth_token;
TRUNCATE password_reset_request_event;
TRUNCATE acknowledgement;
TRUNCATE acknowledgement_report;
TRUNCATE avatax_log;
TRUNCATE avatax_queue;
TRUNCATE cron_schedule;
SET FOREIGN_KEY_CHECKS=1;
```

+++

+++정보 완전 제거 예 실행 전 또는 하위 개발 환경에 대한 모든 주문, 견적, 대변 메모 등을 제거하는 예입니다

```SQL
DELETE FROM `gift_message`;
DELETE FROM `inventory_reservation`;
DELETE FROM `quote`;
DELETE FROM `quote_address`;
DELETE FROM `quote_address_item`;
DELETE FROM `quote_id_mask`;
DELETE FROM `quote_item`;
DELETE FROM `quote_item_option`;
DELETE FROM `quote_payment`;
DELETE FROM `quote_shipping_rate`;
DELETE FROM `reporting_orders`;
DELETE FROM `sales_bestsellers_aggregated_daily`;
DELETE FROM `sales_bestsellers_aggregated_monthly`;
DELETE FROM `sales_bestsellers_aggregated_yearly`;
DELETE FROM `sales_creditmemo`;
DELETE FROM `sales_creditmemo_comment`;
DELETE FROM `sales_creditmemo_grid`;
DELETE FROM `sales_creditmemo_item`;
DELETE FROM `sales_invoice`;
DELETE FROM `sales_invoiced_aggregated`;
DELETE FROM `sales_invoiced_aggregated_order`;
DELETE FROM `sales_invoice_comment`;
DELETE FROM `sales_invoice_grid`;
DELETE FROM `sales_invoice_item`;
DELETE FROM `sales_order`;
DELETE FROM `sales_order_address`;
DELETE FROM `sales_order_aggregated_created`;
DELETE FROM `sales_order_aggregated_updated`;
DELETE FROM `sales_order_grid`;
DELETE FROM `sales_order_item`;
DELETE FROM `sales_order_payment`;
DELETE FROM `sales_order_status_history`;
DELETE FROM `sales_order_tax`;
DELETE FROM `sales_order_tax_item`;
DELETE FROM `sales_payment_transaction`;
DELETE FROM `sales_refunded_aggregated`;
DELETE FROM `sales_refunded_aggregated_order`;
DELETE FROM `sales_shipment`;
DELETE FROM `sales_shipment_comment`;
DELETE FROM `sales_shipment_grid`;
DELETE FROM `sales_shipment_item`;
DELETE FROM `sales_shipment_track`;
DELETE FROM `sales_shipping_aggregated`;
DELETE FROM `sales_shipping_aggregated_order`;
DELETE FROM `tax_order_aggregated_created`;
DELETE FROM `tax_order_aggregated_updated`;
DELETE FROM `magento_rma`;
DELETE FROM `magento_rma_grid`;
DELETE FROM `magento_rma_item_entity`;
DELETE FROM `magento_rma_status_history`;
DELETE FROM `magento_sales_creditmemo_grid_archive`;
DELETE FROM `magento_sales_invoice_grid_archive`;
DELETE FROM `magento_sales_order_grid_archive`;
DELETE FROM `magento_sales_shipment_grid_archive`;
DELETE FROM `sequence_creditmemo_0`;
DELETE FROM `sequence_creditmemo_1`;
DELETE FROM `sequence_creditmemo_2`;
DELETE FROM `sequence_creditmemo_7`;
DELETE FROM `sequence_invoice_0`;
DELETE FROM `sequence_invoice_1`;
DELETE FROM `sequence_invoice_2`;
DELETE FROM `sequence_invoice_7`;
DELETE FROM `sequence_order_0`;
DELETE FROM `sequence_order_1`;
DELETE FROM `sequence_order_2`;
DELETE FROM `sequence_order_7`;
DELETE FROM `sequence_rma_item_0`;
DELETE FROM `sequence_rma_item_1`;
DELETE FROM `sequence_rma_item_2`;
DELETE FROM `sequence_rma_item_7`;
DELETE FROM `sequence_shipment_0`;
DELETE FROM `sequence_shipment_1`;
DELETE FROM `sequence_shipment_2`;
DELETE FROM `sequence_shipment_7`;

## USE THE FOLLOWING WITH CAUTION - CAN CAUSE ISSUES WITH TAX/PAYMENT PROCESSORS IF YOU REUSE ORDER NUMBERS, ETC.

ALTER TABLE sequence_creditmemo_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_7 AUTO_INCREMENT=1;
```

+++

## 환경 변수 사용

[!BADGE Adobe Commerce on cloud 전용]{type=Informative}

환경 변수를 사용하면 각 환경에 대해 변경할 수 있고 변경해야 하는 특정 값을 설정할 수 있으므로 도움이 됩니다. 예를 들어 모든 환경에 대해 다른 관리 URL이 있어야 할 수 있습니다. 이 값을 환경 변수로 설정하여 필요한 경우 클라우드 UI에서 이 값을 구성하고 이 값을 빠르게 참조할 수도 있습니다.

Experience League에서 이 항목에 대한 자세한 내용을 읽을 수 있습니다 [클라우드 인프라 환경 변수의 상거래](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## 소프트웨어 취약성 검색 도구

CI/CD 파이프라인은 강력한 툴이 될 수 있으며 일부 작업을 자동화하는 데 도움이 됩니다. 특히 개발자가 개발 가능한 코드를 커밋할 수 있는 기회는 항상 실제로 있습니다. 피어 코드 검토는 보통 그러한 항목들을 잡지만, 그것이 인간이기 때문에, 실수가 일어납니다. 자동화된 코드 스캔을 사용하면 새로 도입된 기능에서 예기치 않은 취약점에 대한 기회를 줄일 수 있습니다. 이러한 도구는 코드를 라이브 코드 베이스에 병합하는 것을 차단하기 위해 사용할 수도 있습니다. 자동화된 코드 보안 및 품질 검사를 제공하는 다양한 방법과 도구가 있습니다. 강력한 사용자 정의 개발 도구가 있을 수 있지만 지속적인 업데이트 및 조정이 필요합니다. 대신 synk.io 및 Amazon의 코드 검사자와 같이 사전에 업데이트된 도구를 적용하는 것이 좋습니다.

## 웹 응용 프로그램 방화벽

웹 애플리케이션 방화벽 또는 WAF는 DevOps 또는 호스팅 공급자에게 말할 때 자주 사용됩니다.

WAF(웹 애플리케이션 방화벽)는 보안 규칙 세트에 대한 트래픽을 필터링하여 악의적인 트래픽이 사이트 및 네트워크에 들어가는 것을 방지합니다. 규칙을 트리거하는 트래픽은 사이트 또는 네트워크에 영향을 주기 전에 차단됩니다.

Adobe Commerce의 클라우드 WAF는 광범위한 공격으로부터 Adobe Commerce 웹 애플리케이션을 보호하기 위해 설계된 규칙 세트를 사용하여 WAF 정책을 제공합니다. 자체 호스팅 옵션을 선택하고, WAF를 찾고, 규칙을 구성하는 것이 귀하의 책임입니다. 일부 호스팅 제공자와 WAF 제공업체는 일반적인 규칙 세트를 가지고 있지만 일부 작업이 프로젝트에 대해 제대로 작동하는지 확인할 수 있습니다.

WAF는 웹 및 관리자 트래픽을 조사하여 의심스러운 활동을 식별합니다. GET 및 POST 트래픽(HTTP API 호출)을 평가하고 규칙 세트를 적용하여 차단할 트래픽을 결정합니다. WAF는 SQL 주입 공격, 사이트 간 스크립팅 공격, 데이터 필터링 공격 및 HTTP 프로토콜 위반을 포함하여 광범위한 공격을 차단할 수 있습니다.

클라우드 기반 서비스로서 WAF는 설치하거나 유지 관리할 하드웨어 또는 소프트웨어가 필요하지 않습니다. 실제로, 기존 기술 파트너인 는 소프트웨어와 전문 지식을 제공합니다. Fibre Channel의 글로벌 게재 네트워크를 통해 각 캐시 노드에 항상 고성능의 WAF가 있습니다.

Apple에서 제공하는 클라우드 기반의 Adobe Commerce의 WAF에 대한 자세한 내용은 다음을 참조하십시오. [Adobe Commerce 기술 자료 FAQ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
