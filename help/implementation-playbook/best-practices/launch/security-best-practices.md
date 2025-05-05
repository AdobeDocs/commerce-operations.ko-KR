---
title: Commerce 사이트 및 인프라 보안
description: Adobe Commerce 설치를 설정, 구성 및 업데이트할 때 보안 모범 사례를 구현하여 보안을 유지합니다.
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '2000'
ht-degree: 0%

---

# Commerce 사이트 및 인프라 보안

클라우드 인프라에 배포된 Adobe Commerce 프로젝트에 대한 안전한 환경을 구축하고 유지 관리하는 것은 Adobe Commerce 고객, 솔루션 파트너 및 Adobe 간에 공유되는 책임입니다. 이 안내서의 목적은 방정식의 고객 측면에 대한 모범 사례를 제공하는 것입니다.

모든 보안 위험을 제거할 수는 없지만 이러한 모범 사례를 적용하면 Commerce 설치의 보안 자세가 강화됩니다. 안전한 사이트와 인프라는 악의적인 공격에 덜 매력적인 타겟을 만들고, 솔루션 및 고객의 민감한 정보에 대한 보안을 보장하며, 사이트 중단과 많은 비용이 드는 조사를 야기할 수 있는 보안 관련 사고를 최소화하도록 도와줍니다.

>[!NOTE]
>
>클라우드 인프라에서 Adobe Commerce 프로젝트의 보안 및 유지 관리를 위한 역할 및 책임에 대한 자세한 내용은 _Adobe Commerce 보안 및 규정 준수 안내서_&#x200B;의 [공유 책임 모델](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility#security-responsibilities-chart)을 참조하십시오.

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 우선 순위 권장 사항

Adobe은 다음 권장 사항을 모든 고객에게 가장 높은 우선 순위로 고려합니다. 모든 Commerce 배포에서 다음과 같은 주요 보안 모범 사례를 구현합니다.

![검사 목록](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **관리자 및 모든 SSH 연결에 대해 이중 인증 사용**

- Commerce 관리자에 대한 [보안](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html)

- [보안 SSH 연결](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html)(클라우드 인프라)

프로젝트에서 MFA가 활성화되면 SSH 액세스 권한이 있는 클라우드 인프라 계정의 모든 Adobe Commerce은 인증 워크플로를 따라야 합니다. 이 워크플로우에서는 환경에 액세스하려면 이중 인증(2FA) 코드나 API 토큰 및 SSH 인증서가 필요합니다.

![검사 목록](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **관리자 보안**

- [기본 `admin` 또는 `backend`과(와) 같은 일반적인 용어를 사용하지 않고 기본값이 아닌 관리자 URL을 구성](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url)합니다. 이 구성은 사이트에 대한 무단 액세스를 시도하는 스크립트에 대한 노출을 줄입니다.

- [고급 보안 설정 구성](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html)—URL에 비밀 키를 추가하고, 암호는 대/소문자를 구분해야 하며, 관리자 사용자 계정을 잠그기 전에 허용되는 관리자 세션 길이, 암호 수명 간격 및 로그인 시도 횟수를 제한합니다. 보안을 강화하려면 현재 세션이 만료되기 전에 키보드 비활성화 시간을 구성하고 사용자 이름과 암호를 대소문자를 구분해야 합니다.

- [ReCAPTCHA를 사용](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html)하여 자동 불법 공격으로부터 관리자를 보호합니다.

- [관리자 권한](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html)을(를) 역할 및 역할에 관리자 사용자 계정에 할당할 때 최소 권한의 원칙을 따르십시오.

![검사 목록](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Adobe Commerce 최신 릴리스로 업그레이드**

[Commerce 프로젝트를 최신 릴리스로 업그레이드](#upgrade-to-the-latest-release)하여 코드를 업데이트하세요. 보안 패치, 핫픽스, Adobe에서 제공하는 기타 패치를 포함하여 Adobe Commerce, Commerce 서비스 및 확장의 최신 릴리스입니다.

![검사 목록](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **보안 중요 구성 값**

중요한 구성 값을 잠그려면 [구성 관리](../../../configuration/cli/set-configuration-values.md)를 사용하십시오.

`lock config` 및 `lock env` CLI 명령은 관리자가 환경 변수를 업데이트하지 못하도록 구성합니다. 이 명령은 값을 `<Commerce base dir>/app/etc/env.php` 파일에 씁니다. 클라우드 인프라 프로젝트의 Commerce에 대해서는 [저장소 구성 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html#sensitive-data)를 참조하십시오.

![검사 목록](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **보안 검사 실행**

[Commerce 보안 검색 서비스](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html)를 사용하여 모든 Adobe Commerce 사이트에서 알려진 보안 위험 및 맬웨어를 모니터링하고 등록하여 패치 업데이트 및 보안 알림을 받습니다.

## 확장 및 사용자 지정 코드의 보안 보장

Adobe Commerce Marketplace에서 타사 확장을 추가하여 Adobe Commerce을 확장하거나 사용자 지정 코드를 추가할 때 다음 모범 사례를 적용하여 이러한 사용자 지정의 보안을 유지하십시오.

![검사 목록](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **보안에 정통한 파트너 또는 솔루션 통합자(SI)를 선택하십시오** - 보안 개발 사례를 따르고 보안 문제를 예방하고 해결한 실적이 탄탄한 조직을 선택하여 보안 통합과 사용자 지정 코드의 안전한 전달을 보장합니다.

![검사 목록](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **보안 확장 사용** - 솔루션 통합자 또는 개발자와 상의하고 [Adobe 확장 모범 사례](../planning/extensions.md)를 따라 Commerce 배포에 가장 적절하고 안전한 확장을 식별합니다.

- Adobe Commerce Marketplace 또는 솔루션 통합자를 통한 소스 확장만 해당됩니다. 확장 프로그램이 통합자를 통해 제공되는 경우 통합자가 변경되는 경우 확장 라이선스의 소유권을 양도할 수 있는지 확인합니다.

- 확장 및 공급업체 수를 제한하여 위험 노출을 줄입니다.

- 가능한 경우 Commerce 애플리케이션과 통합하기 전에 보안을 위해 확장 코드를 검토하십시오.

- PHP 확장 개발자가 Adobe Commerce 개발 지침, 프로세스 및 보안 모범 사례를 따르도록 하십시오. 특히, 개발자는 원격 코드 실행 또는 약한 암호화를 초래할 수 있는 PHP 기능의 사용을 피해야 합니다. *확장 개발자 우수 사례 안내서*&#x200B;에서 [보안](https://developer.adobe.com/commerce/php/best-practices/security/)을 참조하세요.

![검사 목록](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **감사 코드** - 서버 및 소스 코드 리포지토리에서 개발 중 남은 부분을 검토하십시오. 액세스 가능한 로그 파일, 공개적으로 표시되는 .git 디렉터리, SQL 문을 실행하기 위한 터널, 데이터베이스 덤프, php 정보 파일 또는 필요하지 않으며 공격에 사용할 수 있는 보호되지 않은 기타 파일이 없는지 확인합니다.

## 최신 릴리스로 업그레이드

Adobe은 보안을 강화하고 가능한 손상으로부터 고객을 더 잘 보호하기 위해 업데이트된 솔루션 구성 요소를 지속적으로 릴리스합니다. 최신 버전의 Adobe Commerce 애플리케이션, 설치된 서비스 및 확장으로 업그레이드하고 현재 패치를 적용하는 것은 보안 위협에 대한 첫 번째 및 최상의 방어선입니다.

Commerce은 일반적으로 분기별로 보안 업데이트를 릴리스하지만 우선 순위 및 기타 요소를 기반으로 주요 보안 위협에 대한 핫픽스를 릴리스할 수 있는 권한을 보유합니다.

사용 가능한 Adobe Commerce 버전, 릴리스 주기 및 업그레이드 및 패치 프로세스에 대한 정보는 다음 리소스를 참조하십시오.

- [릴리스된 버전](../../../release/versions.md)
- [제품 가용성](../../../release/product-availability.md)(Adobe Commerce 서비스 및 Adobe 작성 확장)
- [Adobe Commerce 라이프사이클 정책](../../../release/lifecycle-policy.md)
- [업그레이드 안내서](../../../upgrade/overview.md)
- [패치 적용 방법](../../../upgrade/patches/overview.md)

>[!TIP]
>
>[Adobe 보안 알림 서비스](https://www.adobe.com/subscription/adbeSecurityNotifications.html)를 구독하여 최신 보안 정보를 얻고 알려진 보안 문제를 완화하세요.

## 재해 복구 계획 수립

Commerce 사이트가 손상된 경우 포괄적인 재해 복구 계획을 개발 및 구현하여 피해를 제어하고 정상적인 비즈니스 운영을 신속하게 복원하십시오.

재해로 인해 Commerce 인스턴스 복원이 필요한 경우 Adobe에서 고객에게 백업 파일을 제공할 수 있습니다. 해당되는 경우 고객 및 솔루션 통합업체가 복원을 수행할 수 있습니다.

재해 복구 계획의 일부로, Adobe은 무중단 업무 운영을 위해 필요한 경우 재배포를 쉽게 하기 위해 고객에게 [Adobe Commerce 애플리케이션 구성을 내보내기](../../../configuration/cli/export-configuration.md)할 것을 강력히 권장합니다. 구성을 파일 시스템으로 내보내는 주된 이유는 시스템 구성이 데이터베이스 구성보다 우선하기 때문입니다. 읽기 전용 파일 시스템에서는 민감한 구성 설정을 변경하기 위해 응용 프로그램을 재배포해야 하므로 추가 보호 계층이 제공됩니다.

### 추가 정보

**클라우드 인프라에 배포된 Adobe Commerce**

- [백업 및 재해 복구](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)

- [클라우드 인프라에서 Adobe Commerce에 대한 구성 관리 저장](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)

**Adobe Commerce이 온 프레미스에 배포됨**

- [구성 설정 내보내기](../../../configuration/cli/export-configuration.md)

   - [구성 설정 가져오기](../../../configuration/cli/import-configuration.md)

   - [파일 시스템, 미디어 및 데이터베이스 백업 및 롤백](../../../installation/tutorials/backup.md)

## 안전한 사이트 및 인프라 유지

이 섹션에서는 Adobe Commerce 설치를 위한 사이트 및 인프라 보안 유지 관리에 대한 모범 사례를 요약합니다. 이러한 모범 사례 중 대부분은 일반적으로 컴퓨터 인프라 보안에 중점을 두므로 일부 권장 사항이 이미 구현되었을 수 있습니다.

![검사 목록](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **무단 액세스 차단**—호스팅 파트너와 협력하여 Commerce 사이트 및 고객 데이터에 대한 무단 액세스를 차단하는 VPN 터널을 설정하십시오. Commerce 애플리케이션에 대한 무단 액세스를 차단하려면 SSH 터널을 설정하십시오.

![검사 목록](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **웹 응용 프로그램 방화벽 사용**—트래픽을 분석하고 웹 응용 프로그램 방화벽을 사용하여 알 수 없는 IP 주소로 전송되는 신용 카드 정보와 같은 의심스러운 패턴을 검색합니다.

클라우드 인프라에 배포된 Adobe Commerce 설치는 [Fastly 서비스 통합](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)에서 사용할 수 있는 기본 WAF 서비스를 사용할 수 있습니다.

![검사 목록](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **고급 암호 보안 설정 구성**—섹션 8.2.4의 PCI 데이터 보안 표준에서 권장하는 대로 강력한 암호를 설정하고 적어도 90일마다 변경합니다. [관리자 보안 설정 구성](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html)을 참조하십시오.

![검사 목록](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **HTTPS 사용**—Commerce 사이트가 새로 구현된 경우 HTTPS를 사용하여 전체 사이트를 시작합니다. Google은 HTTPS를 등급 요소로 사용할 뿐만 아니라 많은 사용자가 HTTPS로 보안이 되지 않는 한 사이트에서 구매를 고려조차 하지 않고 있다.

## 맬웨어에 대한 Protect

전자 상거래 사이트를 대상으로 하는 맬웨어 공격은 모두 너무 흔하며 위협 행위자는 거래에서 신용 카드와 개인 정보를 수집하는 새로운 방법을 지속적으로 개발합니다.

그러나 Adobe은 대부분의 사이트 타협이 혁신적인 해커 때문이 아니라는 것을 발견했다. 오히려 위협 행위자가 파일 시스템의 기존 취약성, 부실한 암호, 취약한 소유권 및 권한 설정을 활용하는 경우가 많습니다.

가장 일반적으로 경험하는 공격에서는 고객 스토어의 절대 머리글이나 절대 바닥글에 악성 코드가 삽입됩니다. 여기에서 코드는 고객 로그인 자격 증명과 체크아웃 양식 데이터를 포함하여 고객이 상점 앞에 입력하는 양식 데이터를 수집합니다. 그런 다음 이 데이터는 Commerce 백엔드가 아닌 악의적인 목적을 위해 다른 위치로 전송됩니다. 또한 맬웨어는 관리자가 원래의 결제 양식을 결제 공급자가 설정한 보호를 무시하는 가짜 양식으로 대체하는 코드를 실행하도록 위협할 수 있습니다.

클라이언트측 신용 카드 스키머는 다음 그림과 같이 사용자의 브라우저에서 실행할 수 있는 판매자 웹 사이트 콘텐츠에 코드를 임베드하는 맬웨어 유형입니다.

전자 상거래 사이트를 타깃팅하는 맬웨어 공격에 대한 데이터 흐름![1&rbrace;](../../../assets/playbooks/malware-data-flow.svg)

사용자가 양식을 제출하거나 필드 값을 수정하는 등 특정 작업이 발생하면 스키머는 데이터를 정리하여 타사 엔드포인트로 보냅니다. 이러한 끝점은 일반적으로 데이터를 최종 대상으로 전송하는 릴레이 역할을 하는 다른 손상된 웹 사이트입니다.


>[!TIP]
>
>Commerce 사이트가 맬웨어 공격의 영향을 받는 경우 [보안 문제에 응답](../maintenance/respond-to-security-incident.md)하기 위한 Adobe Commerce 모범 사례를 따르십시오.

### 가장 일반적인 공격 이해

다음은 모든 Commerce 고객에게 인지하고 보호 조치를 취할 것을 권장하는 Adobe의 일반적인 공격 카테고리 목록입니다.

- **사이트 숨김**—공격자가 사이트의 시각적 모양을 변경하거나 자신의 메시지를 추가하여 웹 사이트를 손상시킵니다. 사이트 및 사용자 계정에 대한 액세스가 손상되었지만 결제 정보는 종종 안전하게 유지됩니다.

- **봇넷** - 고객의 Commerce 서버는 스팸 이메일을 보내는 봇넷의 일부가 됩니다. 사용자 데이터는 일반적으로 손상되지 않지만 스팸 필터를 통해 고객의 도메인 이름이 차단 목록에 추가된으로 제공되므로 도메인에서 이메일이 전달되지 않을 수 있습니다. 또는 고객의 사이트가 봇넷의 일부가 되어 다른 사이트에 대한 DDoS(분산 서비스 거부) 공격을 야기합니다. 봇넷은 Commerce 서버에 대한 인바운드 IP 트래픽을 차단하여 고객이 쇼핑을 할 수 없도록 할 수 있습니다.

- **직접 서버 공격**—데이터가 손상되고, 백도어와 맬웨어가 설치되었으며, 사이트 운영에 영향을 줍니다. 서버에 저장되지 않은 결제 정보는 이러한 공격을 통해 훼손될 가능성이 적다.

- **자동 카드 캡처**—이 가장 위험한 공격에서 침입자는 숨겨진 맬웨어나 카드 캡처 소프트웨어를 설치하거나 더 나아가 체크아웃 프로세스를 수정하여 신용 카드 데이터를 수집합니다. 그런 다음, 데이터는 다크웹에서 판매하기 위해 다른 사이트로 전송됩니다. 이러한 공격은 오랜 기간 동안 눈에 띄지 않게 될 수 있으며 고객 계정과 재무 정보의 심각한 손상을 초래할 수 있습니다.

- **자동 키 로깅**—위협 행위자는 고객 서버에 키 로깅 코드를 설치하여 관리자 사용자 자격 증명을 수집하므로 고객이 발견되지 않고 로그인하고 다른 공격을 시작할 수 있습니다.

### 암호 추측 공격에 대한 Protect

무차별 암호 추측 공격으로 인해 관리자 권한이 승인되지 않을 수 있습니다. 다음 모범 사례에 따라 이러한 공격으로부터 사이트를 Protect 합니다.

- 외부에서 Commerce 설치에 액세스할 수 있는 모든 지점을 식별하고 보호합니다.

  Commerce 프로젝트를 구성할 때 Adobe의 [우선 순위 권장 사항](#priority-recommendations)을 따라 일반적으로 가장 보호가 필요한 관리자에 대한 액세스를 보호할 수 있습니다.

- 지정된 IP 주소 또는 네트워크에서 온 사용자에게만 액세스를 허용하는 액세스 제어 목록을 설정하여 Commerce 사이트에 대한 액세스를 제어합니다.

  사용자 지정 VCL 코드 조각과 함께 Fastly Edge ACL을 사용하여 들어오는 요청을 필터링하고 IP 주소별 액세스를 허용할 수 있습니다. 요청을 허용하려면 [사용자 지정 VCL을 참조하십시오](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html).


  >[!TIP]
  >
  >원격 인력을 채용하는 경우, 원격 직원의 IP 주소가 Commerce 사이트에 액세스할 수 있는 권한이 있는 주소 목록에 포함되어 있는지 확인하십시오.

### 클릭재킹 악용 방지

Adobe은 요청에 포함할 수 있는 `X-Frame-Options` HTTP 요청 헤더를 상점 전면으로 제공하여 스토어의 클릭재킹 공격을 방지합니다. *Adobe Commerce 구성 가이드*&#x200B;에서 [클릭재킹 악용 방지](../../../configuration/security/xframe-options.md)를 참조하십시오.
