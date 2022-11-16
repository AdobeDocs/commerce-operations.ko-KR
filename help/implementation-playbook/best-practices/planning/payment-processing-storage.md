---
title: 결제 처리 및 스토리지 모범 사례
description: 결제 세부 사항을 안전하게 처리하고 저장하는 방법을 알아봅니다
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 124eaf6e7b465b320d3d7e6a3694130edb93f187
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---


# 결제 처리 및 저장 모범 사례

유지 관리의 주요 원칙 중 하나 [PCI 규정 준수](https://nam04.safelinks.protection.outlook.com/GetUrlReputation) 신용카드 결제를 제대로 처리하고 저장하는 전략이 있다.

Adobe Commerce에 카드홀더 데이터를 저장하는 것은 **엄금금지** 또한 PCI-DSS(Payment Card Industry Data Security Standard)에 따른 가맹점의 의무를 위반할 수 있습니다. Adobe의 공동 책임 모델 및 가맹점 책임에 대한 자세한 내용은 [Adobe Commerce 공유 권한 안내서](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) Adobe 신탁센터에서

전자 상거래 사이트에서 결제 정보를 제대로 처리할 수 있도록 아래 모범 사례를 따르는 것이 좋습니다. 전체 보안 모범 사례에 대한 추가 지침은 [Adobe Commerce에 대한 보안 모범 사례 가이드](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) Adobe 신탁센터에서

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

* Adobe Commerce on cloud 인프라
* Adobe Commerce 온-프레미스

## 카드홀더 데이터 보호

카드홀더 데이터를 저장해야 하는 경우 카드홀더 데이터는 스토리지 보호 기능을 사용하여 Adobe Commerce 외부에 저장해야 합니다. 신용카드 소지자 데이터와 같은 결제 세부 정보를 위한 스토리지 보호 기능을 활용하면 사기 및 기타 잠재적인 보안 문제를 방지할 수 있습니다. 다른 PCI 표준에 따라 보호 기능이 적용되는 첫 번째 방어선이 됩니다. 저장된 데이터의 보호를 향상시키기 위한 일부 기본 방법에는 암호화, 자르기, 토큰화, 단방향 해시 및 마스킹이 있습니다.

암호화 키를 보호하는 것은 데이터 보호 전략에 필수적입니다. 이러한 키를 관리하는 것은 숙련되고 신뢰할 수 있는 관리인들을 갖는 것이 중요합니다.

마지막으로, 스토리지 중에 기본 계정 번호(PAN)는 읽을 수 없습니다(예: XXX와 같이 마스킹됨). 여기에는 플래시 드라이브, USB 및 외부 하드 드라이브와 같은 이동식 스토리지 및 백업 미디어와 감사 로그도 포함됩니다.

## 카드홀더 데이터 전송 암호화

전송 중에 데이터를 보호하는 것은 카드홀더 데이터와 같은 결제 정보를 보호하는 열쇠입니다. 이 정보가 공개 네트워크를 통해 전송되면 보안 문제에 더 취약해질 수 있습니다.

### 보안 전송 프로토콜 사용

다음을 포함한 보안 전송 프로토콜 및 사례를 사용하여 카드홀더 데이터를 전송합니다.

* 신뢰할 수 있는 키 및 인증서
* TLS, SSH 또는 VPN과 같은 보안 전송 프로토콜
* 암호화의 비대칭 알고리즘
* PAN 전송 및 표시를 통한 토케니화, 마스킹 및 침투 테스트
* 카드홀더 데이터에 대한 액세스 제한
* 중요한 정보에 대한 액세스는 필요에 따라 제한되어야 하며, 비즈니스 요구 사항이 있는 권한이 있는 직원에게만 제공됩니다

카드홀더 데이터를 처리하는 권장 방법은 기본 계정 번호(PAN)를 저장하지 않고 특정 결제 처리 공급자로 카드를 토큰화하고 토큰, 카드 유형 및 암호화된 만료 날짜를 저장하는 것입니다. 각 머천트에 대해서만 고유하므로 나중에 사용할 수 있도록 파일에서 자격 증명으로 토큰을 사용할 수 있습니다. 토큰은 고유하므로 보안 문제가 있는 경우 무효화된 토큰으로 인해 부정 활동을 방지할 수 있습니다

## 추가 정보

Adobe의 권장 결제 솔루션을 찾고 있는 경우 다음 사항을 고려하십시오 [Adobe 결제 서비스](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
