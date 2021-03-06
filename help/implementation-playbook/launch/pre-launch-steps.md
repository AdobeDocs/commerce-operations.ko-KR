---
title: 사전 실행 단계
description: 사전 실행 확인 목록을 사용하여 Adobe Commerce 사이트를 원활하게 구현할 수 있습니다.
exl-id: bd10881f-0336-4aa4-82ad-4d635010e2e4
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# 사전 실행 단계

스테이징 환경에서 배포 및 테스트를 완료하면 사이트 시작 준비를 시작할 수 있습니다. 스테이징은 유사한 하드웨어, 구성, 아키텍처 및 서비스에서 실행되는 거의 프로덕션 환경입니다. 다운타임을 줄이고 확장, 서비스, 사용자 지정 구성 및 머천트 사용자 수락 테스트를 통해 사이트 및 스토어를 출시할 수 있습니다.

출시 전 확인 목록은 다음 주요 확인 사항이 포함된 시작 상태 전에 확인해야 합니다.

- 배포를 위한 코드 동결
- 유지 관리 릴리스를 위해 최소 1일, 첫 번째 실행을 위해 1주일 동안 다운타임이 사전에 전달되었는지 확인합니다.
- 배포 스크립트는 프로덕션/스테이징/통합 환경에 대해 완전히 설정/구성됩니다
- 데이터베이스는 모두 스테이징과 프로덕션 환경 간에 설정되고 동일합니다
- 스테이징/프로덕션 환경에 대해 SSL(TLS) 인증서의 유효성을 검사합니다
- 메일 서비스는 트랜잭션 이메일에 대해 잘 구성되고 작동합니다
- CDN은 스테이징/프로덕션 환경에 대해 구성됩니다
- 스테이징/프로덕션 환경에 대한 보안 검사 설정
   - Adobe Commerce 보안 검사
- 성능 평가 수행
   - JMeter
   - 포위 공격
   - 웹 페이지 테스트
   - Google 페이지 속도
- 애플리케이션(OMS, CRM)에서 작동할 모든 타사 통합 유효성 검사
- 성능 모니터 도구 사용(새 유물)
- 리허설(있는 경우)의 데이터 마이그레이션 활동

![실행 프로세스의 1단계를 보여주는 다이어그램](../../assets/playbooks/launch-steps-1.svg)

Adobe Commerce 온프레미스 및 클라우드 구현의 주요 차이점은 배포 스크립트 및 도구와 SSL, Mail 서비스 및 CDN에 대한 설정입니다. 그러나 그 과정은 여전히 같다.

SSL(TLS) 인증서의 경우 클라우드 인프라의 Adobe Commerce에서 와일드카드 인증서를 제공합니다. 사용을 시작하려면 유효성 검사를 전달해야 합니다. DNS 설정 내의 apex 도메인 이름에 기본 TXT 레코드를 추가합니다. 정확한 TXT 레코드는 온보딩 스프레드시트에서 찾을 수 있으며, 그렇지 않으면 티켓을 얻으려면 지원 티켓을 제출해야 합니다. 이 텍스트를 여기에서 질문/주석으로 바꿉니다. 실제 와일드카드 인증서 대신 SSL(TLS) 인증서를 사용하는 경우 설정에 첨부된 인증서와 함께 지원 티켓을 제출합니다.

Adobe Commerce on cloud infrastructure는 트랜잭션 이메일에 대한 SendGrid Mail 기능을 제공합니다. Pro 계획의 경우 DNS 설정에 SendGrid 레코드를 추가해야 합니다. SendGrid 레코드는 온보딩 스프레드시트에서 찾을 수 있습니다. 그렇지 않으면 SI 또는 merchant가 지원 티켓을 제출하여 승인을 받아야 합니다. 시작하려면 DNS를 변경할 필요가 없습니다. SendGrid가 사전 구성되어 있습니다.

## 전체 사전 실행 검사 목록

전체 사전 실행 확인 목록은 론치 상태로 이동하는 데 필요한 모든 주요 활동을 보여줍니다.

- Go-live 위험 완화 계획을 업데이트했습니다.
- 제공된 올바른 도메인 이름
- 보내는 이메일이 테스트되었습니다
- SSL 인증서가 프로비저닝되고 구성되었습니다
- Adobe Commerce 애플리케이션의 중요한 구성이 올바르게 업데이트되었습니다
- 기본 URL 및 기본 관리 URL이 최종 호스트 이름으로 올바르게 설정됨
- 관리자 암호가 변경되었습니다.
- 더 이상 액세스가 필요하지 않은 애플리케이션에 액세스할 수 있는 모든 사용자는 제거됩니다
- 프로덕션 환경에 대한 지급 구성(일부 경우, 결제가 테스트를 위해 샌드박스 모드를 사용)
- 프로덕션 데이터베이스의 테스트 데이터(고객, 희망 목록, 검토, 주문 및 관련 데이터)가 지워집니다

![실행 프로세스의 2단계를 보여주는 다이어그램](../../assets/playbooks/launch-steps-2.svg)
