---
title: 시작 단계
description: launch 체크리스트를 사용하여 Adobe 상거래 사이트 구현을 원활하게 하십시오.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# 시작 단계

사전 실행 체크리스트를 테스트하고 완료한 후 제거할 때 시작할 최종 단계를 시작할 수 있습니다. 이러한 단계에는 사이트 시작(go live) 티켓 입력, 액세스 권한 초과 및 마지막으로 라이브 상태일 때 스토어 테스트 등이 포함됩니다.

Adobe 상거래 지원 담당자는 프로세스를 통해 귀사와 협력하여 상태를 확인하고 발생하는 모든 질문이나 문제를 처리하는 데 도움을 줍니다. 발생한 사항과 해결된 방법을 가장 잘 캡처하려면 모든 문제를 티켓과 함께 추적해야 합니다. When you begin deploying continuous iterations of updates to your launched store, you may have similar issues occur again. These tickets can help pinpoint the issues and help adjust your deployment tasks.

- 기본 URL로 애플리케이션 구성
   - 새 사이트로 DNS 전환
   - DNS 서비스 액세스
   - 도메인 및 호스트 이름에 대한 A 및 CNAME 레코드를 업데이트합니다
   - Wait for the TTL time to pass and access your store

- 프로덕션에서 완전히 테스트
   - 웹 사이트의 모든 기능 확인
   - CDN 캐시 확인
   - 모든 통합 타사 서비스 확인
   - 모든 타사 시스템 확인

- 문제가 go-live를 차단하는 경우 Adobe 상거래 핫라인에 문의하십시오

![실행 프로세스의 3단계를 보여주는 다이어그램](../../assets/playbooks/launch-steps-3.svg)
