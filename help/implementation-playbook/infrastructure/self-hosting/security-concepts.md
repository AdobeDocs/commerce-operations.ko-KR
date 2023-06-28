---
title: 자체 호스팅 Adobe Commerce 보안 개념
description: 자체 호스팅 보안 아이디어와 고려 사항 및 모범 사례에 대해 알아봅니다. 읽기 전용 파일 시스템, 맬웨어 검색 및 adobe commerce를 호스팅할 때 고려해야 할 기타 많은 주제와 같은 개념에 대해 알아봅니다.
landing-page-description: Adobe Commerce을 직접 호스팅할 때 고려해야 할 몇 가지 보안 개념과 사항에 대해 알아봅니다.
short-description: Adobe Commerce을 직접 호스팅하기 위한 전략과 보안 개념에 대해 알아봅니다.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: c4912f02-0411-466f-8c77-d610de9eb35d
feature: Install, Security
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---

# 보안 개념

보안은 전자 상거래 프로젝트와 관련된 모든 것에 대한 강력한 고려가 되어야 합니다. 강력한 보안 스탠스가 없으면 공격할 수 있는 표면적이 기하급수적으로 커진다. 제시된 개념과 아이디어는 일반적으로 악용되는 일반적인 취약성을 감소시키는 것으로 입증된 방법을 제공한다.

다음 개념은 특별한 순서가 없습니다. 그들은 고려해야 할 몇 가지 아이디어와 개념을 제공하기 위한 것입니다. 대부분은 무료이거나 최소한의 설정 및 구성과 후속 모니터링이 필요할 수 있습니다. 이 자습서 이외의 주제에서는 여기에 제시된 개념을 충분히 깊이 있게 이해할 수 있도록 연구하십시오.

## 읽기 전용 파일 시스템

읽기 전용 파일 시스템 개념은에서 차용되었습니다. [클라우드 인프라의 Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. 이는 나쁜 배우가 사용하는 한 가지 주요 영역을 완전히 제거한다. 많은 악용은 검색을 방지하기 위해 Commerce 애플리케이션에 있을 것으로 예상되는 파일을 변경하는 데 사용되었습니다. 불량 액터는 파일을 만드는 대신 기존 파일의 내용을 변경하여 예기치 않은 작업을 수행합니다. 파일 시스템을 읽기 전용으로 만들면 이 공격 벡터가 크게 줄어듭니다.

## 2단계 인증 및 암호 관리자 사용

암호를 공유하지 마십시오. 각 관리자는 적절한 ACL이 있는 자체 계정이 있어야 합니다. 두 요소 식별이 비활성화되거나 제거되지 않도록 하십시오. 서드파티에 대한 관리자 액세스 권한을 제공하는 경우, 암호가 암호 관리자에 의해 생성되고 재사용되지 않는지 확인하십시오.

## 맬웨어 검사

맬웨어 스캔은 일반적으로 Adobe Commerce을 전문으로 만들려고 하는 호스팅 공급자에서 찾을 수 있습니다. 알려진 맬웨어 및 악용 라이브러리는 새로운 위협이 발견, 평가 및 진단됨에 따라 지속적으로 증가하는 목록입니다. 호스팅 공급자에게 이러한 서비스가 있는지, 그리고 이러한 서비스가 자동으로 실행되는지 또는 요청이 있을 때만 실행되는지를 확인합니다. 알려진 악용 라이브러리를 사용하여 상거래 애플리케이션에서 악용에 대한 확인을 지속적으로 수행할 수 있는 구독할 수 있는 서비스도 있습니다. 이 중 일부는 외부 전용이며 일부는 인프라에 추가하여 모든 폴더, 파일 및 데이터베이스에 대한 내부 딥 스캔을 제공할 수 있습니다. Sansec.io에서 Sucuri까지, 그리고 물론 MageReport까지 이 분야에서 수년간의 경험을 가진 몇 가지 공급자가 있습니다. 일부는 무료이고, 일부는 그에 상응하는 비용이 있다. 이러한 사실을 알고 Adobe Commerce 설계자 및 DevOps 팀과 신중하게 대화를 나누면 적절한 솔루션을 찾을 수 있습니다.

## Commerce용 사이트 전체 분석 도구

다음 [사이트 전체 분석 도구](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} 는 Adobe Commerce 설치의 보안 및 운영을 보장하기 위한 자세한 시스템 통찰력과 권장 사항이 포함된 사전 예방적 셀프서비스 도구이자 중앙 저장소입니다. 24시간 연중무휴 실시간 성능 모니터링, 보고서 및 조언을 제공하여 잠재적인 문제를 식별하고 사이트 상태, 안전 및 애플리케이션 구성에 대한 가시성을 향상시킵니다. 이는 해결 시간을 줄이고 사이트 안정성과 성능을 개선하는 데 도움이 됩니다.

## 관리자 작업 로깅에 대한 설정 활성화 및 확인

이 로그는 Adobe Commerce 관리자에 로그인하고 스토어 > 구성 > 고급 > 관리 > 관리자 작업 로깅으로 이동한 후 찾을 수 있습니다. 이렇게 하면 모니터링 및 기록되는 이벤트 목록이 제공됩니다. 혐의가 Commerce 관리자에 대한 액세스 권한을 얻은 경우 악용된 사이트에서 법의학 분석을 수행할 때 유용합니다. 이 로깅 및 보고서는 잘못된 액터가 수행한 이벤트를 확인하는 데 도움이 될 수 있습니다. 관리자 작업 로깅이 비활성화된 경우, 즉 특정 작업을 수행할 때 다른 사용자가 관리자 작업 로깅을 비활성화했을 수 있다는 표시입니다.

## ssh 액세스용 Bastion Server

보안 개념 자습서의 대부분의 주제를 설명하기 더 어렵습니다. 이에 대한 기본 아이디어는 ssh 액세스를 위한 중개자 역할을 하는 서버를 제공하는 것이다. 이렇게 하면 프로덕션 서버가 외부 ssh 연결을 허용하지 않습니다. 이 기본 서버를 만들고 로컬 IP 마스크를 사용하여 지정된 서버만 SSH로 서버에 연결할 수 있습니다.

## ACL 역할 및 권한 검토

Adobe Commerce의 모든 관리 사용자에게는 ACL 역할이 할당됩니다. 이 역할은 작업을 수행해야 하는 기능만 제공하도록 만들어야 합니다. ACL 역할이 필요 이상의 권한을 제공하지 않도록 자주 평가해야 합니다. 필요한 경우 책임이 있는 여러 ACL 역할을 생성합니다. 어떤 이유로든 액세스 권한이 서드파티에게 부여되면 가능한 한 빨리 비활성화해야 합니다. 관리자 사용자를 만들 때 액세스 시간과 자동 만료 날짜 설정이 절대적으로 필요한 시간을 질문합니다.

## 관리자 사용자 및 SSH 사용자가 자주 액세스함

원치 않거나 권한이 없는 관리자 사용자 생성을 감지하려면 관리자 사용자 목록을 자주 감사해야 합니다. 경험상 월별로 Adobe Commerce 애플리케이션에 대한 SSH 및 관리자 액세스 권한이 있는 사용자를 확인하는 것이 좋습니다. 새 사용자가 감지되면 계정을 비활성화하고 해당 문제에 대한 회사 정책 및 절차를 따르십시오. 악용으로부터 복구하는 것보다 사용자 액세스를 복구하는 것이 더 쉽습니다.

## 데이터베이스 정리

프로덕션 데이터에 대한 액세스 제한. 이러한 지정된 팀원은 운영 데이터베이스를 삭제하고 실제 데이터를 정리할 수 있어야 합니다. 데이터를 제거하는 것이 선택 사항인 경우 주문, 견적 및 고객과 같은 해당 테이블을 자릅니다. 그러나 경우에 따라 전체 데이터 세트를 원하지만 값은 익명으로 지정할 수 있습니다. 이는 일반적으로 스테이징 환경에서 적용됩니다. 또한 업그레이드 전에 유용합니다. 실제 양의 데이터가 있지만 익명으로 처리하면 업그레이드를 위한 배포 실행 시간을 테스트하고 확인할 수 있습니다. 제한된 데이터 세트가 있는 경우 업그레이드 프로세스 및 타이밍을 과소평가할 수 있습니다.

+++고객 정보 무작위 지정 예 다음은 Adobe Commerce이 데이터를 저장하는 일부 표준 테이블에서 임의의 문자열과 모든 이름 및 성 필드를 사용하여 고객 이메일 주소를 변경하는 방법에 대한 예입니다. **모든 테이블에서 중요한 데이터를 확인해야 합니다. 이 목록은 고객 데이터를 저장할 수 있는 테이블에 포함되지 않습니다**

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


+++익명으로 처리하려는 대신 테이블을 자를 수도 있습니다

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

+++정보 완전히 제거 예 다음은 모든 주문, 견적, 대변 메모 등을 실행하기 전에 또는 더 낮은 개발 환경에서 제거하는 예입니다.

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

[!BADGE Adobe Commerce on cloud only]{type=Informative}

환경 변수를 사용하면 각 환경에 대해 변경할 수 있고 변경해야 하는 특정 값을 설정할 수 있습니다. 예를 들어 모든 환경에 대해 서로 다른 관리자 URL을 보유할 수 있습니다. 이 값을 환경 변수로 설정하면 필요한 경우 Cloud UI에서 이 값을 구성하고 빠르게 참조할 수 있습니다.

Experience League에서 이 주제에 대해 자세히 읽어볼 수 있습니다. [클라우드 인프라의 Commerce 환경 변수](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## 소프트웨어 취약성 검색 도구

CI/CD 파이프라인은 강력한 도구가 될 수 있으며 일부 작업을 자동화하는 데 도움이 됩니다. 특히, 개발자가 악용할 수 있는 코드를 커밋할 수 있는 기회는 항상 현실의 가능성이다. 피어 코드 검토는 일반적으로 이러한 항목을 잡지만, 사람이므로 실수가 발생합니다. 자동화된 코드 스캔은 새로 도입된 기능에서 예상치 못한 취약점이 발생할 가능성을 줄이는 데 도움이 됩니다. 이러한 도구는 라이브 코드 베이스로의 코드 병합을 차단하기 위해 적절히 사용할 수도 있습니다. 자동화된 코드 보안 및 품질 검사를 제공하는 다양한 방법과 도구가 있습니다. 강력한 맞춤형 개발 도구가 있을 수 있지만 지속적인 업데이트와 조정이 필요합니다. synk.io 및 Amazon의 코드 검사기와 같이 미리 업데이트된 도구를 적용하는 것이 대안입니다.

## 웹 애플리케이션 방화벽

DevOps 또는 호스팅 공급자와 통신할 때 종종 사용되는 웹 애플리케이션 방화벽 또는 WAF입니다.

WAF(Web Application Firewall)는 보안 규칙 세트에 대해 트래픽을 필터링하여 악성 트래픽이 사이트 및 네트워크로 유입되는 것을 방지합니다. 규칙을 트리거하는 트래픽은 사이트 또는 네트워크를 손상시키기 전에 차단됩니다.

Adobe Commerce의 클라우드 WAF는 광범위한 공격으로부터 Adobe Commerce 웹 애플리케이션을 보호하기 위해 고안된 규칙 세트와 함께 WAF 정책을 제공합니다. 자체 호스팅 옵션을 선택하는 경우 WAF를 찾고 규칙을 구성하는 것은 사용자의 책임입니다. 일부 호스팅 공급자와 WAF 공급자는 좋은 시작인 일반적인 규칙 세트를 가지고 있지만 일부 작업을 통해 프로젝트에서 작업을 수행할 수 있습니다.

WAF는 웹 및 관리자 트래픽을 검사하여 의심되는 활동을 식별합니다. GET 및 POST 트래픽(HTTP API 호출)을 평가하고 규칙 세트를 적용하여 차단할 트래픽을 결정합니다. WAF는 SQL 삽입 공격, 크로스 사이트 스크립팅 공격, 데이터 내보내기 공격, HTTP 프로토콜 위반 등 다양한 공격을 차단할 수 있습니다.

클라우드 기반 서비스로서 WAF는 설치 또는 유지 관리에 필요한 하드웨어나 소프트웨어가 필요하지 않습니다. 기존 기술 파트너인 Fastly는 소프트웨어와 전문 지식을 제공합니다. Fastly의 글로벌 전달 네트워크에 있는 각 캐시 노드에는 항상 실행되는 고성능 WAF가 있습니다.

Fastly에서 제공하는 Adobe Commerce on cloud의 WAF에 대한 자세한 내용은 [Adobe Commerce 기술 자료 FAQ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
