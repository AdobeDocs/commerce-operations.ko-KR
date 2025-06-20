---
title: 구현 업그레이드
description: Adobe Commerce 프로젝트에 대한 다양한 업그레이드 구현 단계에 대해 알아봅니다.
exl-id: d64855a7-73ee-463f-a314-6a8d4ebe4726
source-git-commit: a81d2c0b6526c2c8c8c5c4652c83595667985543
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 1%

---

# 구현 업그레이드

업그레이드 구현은 다음 5단계로 구성됩니다.

- 업그레이드 분석
- 개발 및 품질 보증(QA)
- UAT(사용자 승인 테스트) 및 출시 준비
- 시작
- Post-launch

## 업그레이드 분석

분석은 업그레이드 프로세스에서 가장 중요한 부분일 것입니다. 잘 실행된 분석을 통해 시간을 절약하고 향후 발생할 수 있는 예상치 못한 일을 막을 수 있습니다. 이 단계의 결과는 모든 종속성이 포함된 자세한 업그레이드 체크리스트와 문서여야 합니다.

다음은 전체 분석에 포함할 수 있는 항목입니다.

- **대상 릴리스의 범위**—[Experience League](../../release/release-notes/overview.md)에 대한 설명서와 파트너 릴리스 웨비나의 정보는 대상 업그레이드에 대해 알고 있어야 하는 모든 세부 정보를 제공합니다.

- **[!DNL Upgrade Compatibility Tool]개의 결과**—이 도구를 사용하면 현재 코드와 대상 버전의 코드를 비교하고 해결해야 하는 모든 문제에 대한 보고서를 만들어 모든 업그레이드를 더 빠르고 쉽게 수행할 수 있습니다. [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md)을(를) 참조하세요. 보고서의 주요 세부 사항은 다음과 같습니다.

   - 현재 설치된 버전
   - 대상 버전 업그레이드
   - 발견된 중요 오류 번호 및 세부 정보

  >[!TIP]
  >
  >이 모든 정보 등은 사이트 전체 분석 도구 [대시보드](../../tools/site-wide-analysis-tool/dashboard.md)에서 사용할 수 있습니다.

- 대상 버전을 지원하도록 서비스를 업그레이드하는 중입니다. 다음 표 템플릿을 사용하여 업그레이드해야 하는 서비스를 매핑합니다. [시스템 요구 사항](../../installation/system-requirements.md)을 사용하여 _업그레이드_ 열에 추가할 항목을 결정하십시오.


  | 서비스 | 현재 버전 | 다음으로 업그레이드 | 메모 |
  |-----------------|-----------------|------------|----------------------------------------------------------|
  | PHP | 7.4 | 8.1 |                                                          |
  | 레디스 | 6.0 | 6.2 |                                                          |
  | [!DNL RabbitMQ] | 3.8 | 3.9 | 현재 사용되지 않고 있지만 사용을 고려해야 합니다 |
  | MariaDB(클라우드) | 10.4 | 10.6 |                                                          |
  | MySQL | 8.0 | -/-/ |                                                          |
  | 작성기 | 1.9.2 | 2.2 |                                                          |
  | Elasticsearch | 7.10 | 7.17 |                                                          |

- **확장 및 타사 모듈**—이 테이블 서식 파일을 사용하여 확장 및 사용자 지정의 상태를 이해하면 전략적 결정을 내리고 작업을 정의할 수 있습니다. 이는 프로젝트의 복잡성을 최소화하기 위해 Adobe Commerce이 기본 옵션일 수 있는 모든 확장을 대체할 수 있는 기회입니다. 모듈 및 확장 목록을 보려면 `bin/magento module:status` 명령을 사용하십시오.

  | # | 확장/<br>모듈 이름 | 작성기 패키지 | 공급업체 | 현재 버전 | 기능 | 최신<br>Commerce 버전과 호환됩니까? | 문제 | Commerce 토박이입니까? | 작업 | 메모 |
  |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
  | 1 | 확장 이름 및 링크 | extension/<br>extensionx-magento-2 | 공급업체 이름 | 버전 설치됨 | 비즈니스 요구 사항 | 예/아니요 | 이 확장에 직면한 식별된 문제 나열 | 예/아니요 | 유지/바꾸기/<br>제거 |       |

- **사용자 지정 모듈**—타사 모듈 테이블과 유사한 템플릿으로 사용자 지정 모듈을 업그레이드하는 데 필요한 상태와 작업을 추적하고 이해할 수 있습니다.

  | # | 모듈 이름 | 기능 | 필수? | Commerce 토박이입니까? | 작업 | 메모 |
  |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
  | 1 | 모듈 이름 | 비즈니스 요구 사항 | 예/아니요 | 예/아니요 | 유지/바꾸기/제거 |       |

- **업데이트가 필요한 composer.json의 Composer 패키지 및 종속성.**

또한 파트너는 [Adobe Commerce 베타 릴리스](../../release/beta.md)에 참여하고 프리릴리스 기회를 사용하여 예정된 릴리스에 대한 코드에 일찍 액세스할 수 있습니다. 코드에 일찍 액세스하면 개발자는 GA(일반 가용성) 날짜까지 업그레이드를 완료할 수 있을 만큼 충분한 시간을 준비할 수 있습니다. Beta 코드는 일반적으로 GA 날짜 5주 전에 릴리스되고 프리릴리스는 2주 전에 릴리스됩니다.

## 개발 및 QA

테스트는 가장 많은 시간이 필요한 업그레이드 단계입니다. 따라서 이 프로세스는 가능한 한 자동화되어야 합니다. 더 빠른 QA를 위해 플랫폼 및 시스템 테스트 도구를 설정하고 사용하는 방법에 대한 자세한 내용은 _[응용 프로그램 테스트 안내서](https://developer.adobe.com/commerce/testing/guide/)_&#x200B;에 나와 있습니다. 스테이징 환경을 사용하여 프로덕션으로 이동하기 전에 업그레이드를 테스트하고 유효성을 검사하십시오.

## UAT 및 출시 준비

UAT는 사이트를 검토하고 유효성을 검사해야 하는 업그레이드의 마지막 단계 중 하나입니다. 배포 시기와 유지 관리 페이지 필요 여부도 결정해야 합니다. cron 프로세스 및 타사 메시지에 대한 계획을 수립합니다.

파병일이 다가옴에 따라 의사소통은 필수적이다. 지평선 상의 변화, 그것이 그들에게 미치는 영향, 그리고 그들이 그것을 어떻게 다루어야 하는지에 대해 더 많은 사람들이 알고 있다면, 당신은 성공적인 출시를 할 가능성이 더 높습니다. 모든 단계에서 과도한 의사 소통을 하는 것을 두려워하지 마십시오. 이렇게 하면 라이브 진행 후 관련된 모든 사람의 평가 결과가 나올 가능성이 높아집니다.

## 시작

프로덕션에 배포하고 확장을 업데이트하여 업그레이드를 완료합니다. 시뮬레이션된 주문을 사용하여 중요 경로 흐름을 테스트해야 합니다. 최소한의 문제로 시작하는 방법에 대한 몇 가지 팁을 보려면 이 [모범 사례](../prepare/best-practices.md)를 확인하십시오.

커뮤니케이션 계획을 따라 모든 이해 당사자가 업그레이드를 인지하고 업그레이드를 지원하도록 완전히 교육되었는지 확인하십시오.

마지막으로, 팀에게 브리핑을 열어 학습한 내용과 위험 요소를 파악합니다. 이 회고록은 다음에 프로세스를 개선하는 데 도움이 됩니다.

## Post-Launch

사이트 시작 후에는 분석 데이터, Google 검색 콘솔 및 기타 리소스를 확인하여 예기치 않은 문제가 없고 모든 것이 예상대로 작동하는지 확인하십시오.

잘 설계된 모니터링 도구를 통해 성능을 주시하는 것은 항상 좋은 생각입니다. 사이트 성능을 모니터링하는 많은 도구와 수단이 있으므로 조직과 적절한 도구를 선택하십시오. 클라우드 인프라 관리 시스템을 사용하는 Adobe Commerce 고객은 [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=ko)와 같은 서비스를 이용하여 사이트 성능을 모니터링하는 것이 좋습니다.
