---
title: 실행 후 단계
description: 원활한 Adobe Commerce 사이트 구현을 위해 출시 후 체크리스트를 사용합니다.
exl-id: 0c3162d9-6475-4b34-9278-e5aea39bd0f9
feature: Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---

# 실행 후 단계

웹 사이트가 활성 상태가 되면 사이트가 제대로 시작되었는지 확인하기 위해 가능한 한 빨리 다음 활동을 수행합니다.

- 업 타임 모니터링 도구(New Relic)를 활성화하고, 검사를 활성화하고, 사이트를 모니터링하여 모든 서비스 및 액세스가 녹색으로 표시되는지 확인
- 정기적으로 Adobe Commerce 보안 검사 활성화
- 클러스터를 라이브로 태깅하고 지원 티켓을 만들어 높은 SLA 모니터링 활성화
- CSE(Customer Success Engineer) 및 TAM(Technical Account Manager)은 컷오버가 완료되는 즉시 다음 작업을 수행합니다.
   - 클러스터를 Adobe Commerce 클라이언트에 대한 높은 SLA로 태깅하고 지원 티켓을 만들어 활성화합니다
   - 도메인 이름에 대한 Pingdom 검사 활성화
   - 모니터링 상태를 검토하고 모든 항목이 녹색인지 확인합니다.
   - 보증 기간 및 매개 변수에 대해 Go-Live 당일 이메일로 이해 당사자에게 계속 알립니다.

![실행 프로세스의 4단계를 보여 주는 다이어그램](../../assets/playbooks/launch-steps-4.svg)
