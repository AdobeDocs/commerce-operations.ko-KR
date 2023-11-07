---
title: 결제 처리 및 보관에 대한 우수 사례
description: 결제 세부 정보를 안전하게 처리하고 저장하는 방법 알아보기
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: db0fce79b22d409e8d639b959dc5a04693e72659
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# 결제 처리 및 보관 모범 사례

유지 관리의 주요 원칙 중 하나 [PCI 준수](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) 는 신용카드 결제를 적절히 처리하고 저장하는 전략을 가지고 있다.

Adobe Commerce에 카드 소지자 데이터 저장 **엄격하게 금지되어** PCI-DSS(Payment Card Industry Data Security Standard)에 따라 판매자로서의 의무를 위반할 수 있습니다. 상인 의무에 대한 공유 책임 모델과 지침에 대한 자세한 내용은 [Adobe Commerce 공유 책임 모델 안내서](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) Adobe 트러스트 센터에서.

전자 상거래 사이트에서 결제 정보를 제대로 처리하고 있는지 확인하려면 아래 모범 사례를 따르십시오. 보안 모범 사례에 대한 추가 지침은 [사이트 및 인프라 보안](../launch/security-best-practices.md).

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

* 클라우드 인프라의 Adobe Commerce
* Adobe Commerce 온-프레미스

## 카드 소지자 데이터 보호

카드 소지자의 데이터 저장이 필요한 경우, 카드 소지자의 데이터는 저장 안전장치가 있는 Adobe Commerce 외부에 저장되어야 합니다. 신용 카드 소지자 데이터와 같은 결제 세부 정보에 대한 스토리지 보호 수단을 갖추면 사기 및 기타 잠재적인 보안 문제를 방지하는 데 도움이 됩니다. 다른 PCI 표준에 따라 보호 기능을 갖추는 것이 첫 번째 방어선입니다. 저장된 데이터의 보호를 강화하기 위한 몇 가지 바람직한 방법에는 암호화, 자르기, 토큰화, 단방향 해시 및 마스킹이 있습니다.

암호화 키에 대한 보호는 데이터 보호 전략에 필수적입니다. 이러한 키를 관리하는 숙련되고 신뢰할 수 있는 관리자를 확보하는 것이 중요합니다.

마지막으로, 기본 계정 번호(PAN)는 저장 중에 읽을 수 없어야 합니다(예: `XXX`. 여기에는 휴대용 저장소와 플래시 드라이브, USB, 외장형 하드 드라이브, 감사 로그 등의 백업 미디어가 포함됩니다.

## 카드 소지자 데이터 전송 암호화

전송 중 데이터를 보호하는 것은 카드 소지자 데이터와 같은 결제 정보를 보호하는 데 중요합니다. 이러한 정보가 개방형 네트워크를 통해 전송되면 보안 문제에 더욱 취약해질 수 있다.

### 보안 전송 프로토콜 사용

다음을 포함한 보안 전송 프로토콜 및 사례를 사용하여 카드 소지자의 데이터를 전송합니다.

* 신뢰할 수 있는 키 및 인증서
* TLS, SSH 또는 VPN과 같은 보안 전송 프로토콜
* 암호화의 비대칭 알고리즘
* PAN 전송 및 표시를 통한 토큰화, 마스킹 및 침투 테스트
* 카드 소지자 데이터에 대한 액세스 제한
* 중요한 정보에 대한 액세스는 반드시 알아야 하는 기준으로 제한되어야 하며 비즈니스 요구 사항이 있는 승인된 직원에게만 제공됩니다

카드 소지자의 데이터를 처리하는 권장 방법은 데이터를 저장하는 대신 토큰화하는 것입니다. 특정 결제 처리 공급업체에 카드를 토큰화하고 토큰, 카드 유형 및 암호화된 만료일을 저장합니다. 이 토큰은 각 판매자에 대해서만 고유하므로 나중에 사용할 수 있도록 파일에 대한 자격 증명으로 사용할 수 있습니다. 토큰은 고유하므로 보안 문제가 있는 경우 토큰이 무효화되어 사기 활동을 방지할 수 있습니다.

## 추가 정보

Adobe으로 추천 결제 솔루션을 찾고 있다면 다음을 고려하십시오. [Adobe 결제 서비스](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
