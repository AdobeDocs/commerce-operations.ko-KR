---
source-git-commit: dbb758dd76fd9ea2f2e2e64fb87ea03d1c426263
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---
# Adobe Commerce 릴리스 노트(v2.4.9-alpha3)

## v2.4.9-alpha3의 주요 특징

Adobe Commerce 2.4.9-alpha3 릴리스에는 다음과 같은 사항이 적용됩니다.

### Braintree

#### 계정 영역을 통해 Google 지급 저장

Magento 2.4.9-alpha3에서 이제 Braintree에서 Google Pay Vault가 활성화되면 고객은 계정 영역을 통해 Google Pay 카드를 소산할 수 있습니다. 저장된 카드는 저장된 결제 방법 아래에 표시되며 체크아웃 시 향후 구매에 사용할 수 있으며 고객이 삭제할 수 있습니다. 이는 보관 지원을 Cards 및 PayPal을 넘어 Google Pay로 확장합니다.

_BUNDLE-3459_

#### Magento 주문을 Braintree 포털 주문에 연결

이제 Magento 2.4.9-alpha3에서 Braintree 포털 링크가 Magento 관리자의 주문 세부 사항에 추가됩니다. 이 링크를 클릭하면 Braintree 주문의 판매자 ID 및 거래 ID를 사용하여 Magento 포털(새 탭)에서 관련 거래가 열립니다. 이렇게 하면 두 시스템에 별도로 로그인하지 않고도 직접 상호 참조할 수 있습니다.

_BUNDLE-3461_

#### RTAU(실시간 계정 업데이트 프로그램)

Braintree용 Magento 2.4.9-alpha3의 RTAU(Real Time Account Updater) 기능을 사용하면 카드 만료 또는 교체 시 저장된 Visa, Mastercard 및 Discover 카드 세부 사항이 자동으로 업데이트됩니다. 이렇게 하면 실패한 결제를 최소화하고, Magento Vault를 최신 상태로 유지하며, 지원되지 않는 유형(선불, Apple Pay, Google Pay)을 오류 없이 건너뜁니다.

_BUNDLE-3462_

#### Braintree 카드 결제에 대한 ELO 카드 유형 지원

Magento 2.4.9-alpha3에서 ELO 카드 유형에 대한 지원이 Braintree 결제에 추가되었습니다. 이제 관리자는 신용 카드 구성에서 ELO를 활성화할 수 있으며 고객은 체크아웃 시 ELO 카드를 사용하여 성공적으로 주문할 수 있으므로 Braintree을 통해 원활한 거래가 보장됩니다.

_BUNDLE-3464_

### 프레임워크

#### RabbitMQ에서 Apache ActiveMQ로 마이그레이션

_AC-14558_

#### chart.js 종속성을 최신 버전으로 업그레이드

chart.js 종속성이 최신 버전 4.5.0으로 업그레이드되었습니다.

_AC-15133 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/657f983e)_

#### Laminas MVC에서 마이그레이션

Adobe Commerce은 PHP 8.5 이상의 장기적인 호환성과 안정성을 보장하기 위해 레거시 Laminas MVC를 대체하는 기본 MVC 구현을 도입했습니다. 이러한 변경 사항은 성능을 강화하고, 외부 의존성을 감소시키며, Commerce에 미래를 대비할 수 있는 기반을 제공합니다

_AC-15160_

### 보안

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-94](https://helpx.adobe.com/kr/security/products/magento/apsb25-94.html)을 참조하십시오.

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}
