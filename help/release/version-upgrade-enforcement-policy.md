---
title: 클라우드 버전 업그레이드 시행 정책
description: Adobe Commerce on Cloud(PaaS)의 버전 업그레이드 강제 적용 - Adobe에서 업그레이드, 강제 적용 날짜, 비활성화 및 필수 작업을 시행하는 이유에 대해 알아보십시오. 과도적 조항 및 마이그레이션 경로에 대해서는 라이프사이클 정책을 참조하십시오.
source-git-commit: 620523021580a9dba44e0e2041d8100761b8bce1
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---


# PaaS(Adobe Commerce on Cloud)에 대한 버전 업그레이드 시행 정책

Adobe Commerce 버전에 대한 일반 지원 및 확장 지원이 종료되면 Adobe은 해당 지원되지 않는 버전을 실행하는 PaaS(클라우드 기반 Adobe Commerce) 환경을 비활성화할 수 있는 권한을 보유합니다. 버전 업그레이드 적용은 Adobe 호스팅 PaaS 환경에만 적용되며, 온프레미스 고객은 자체 인프라를 관리합니다.

릴리스 라인에 게시된 [확장 지원 종료](lifecycle-policy.md#end-of-support-dates) 날짜 이전에 지원되는 Adobe Commerce 버전으로 이동하거나 [!DNL Adobe Commerce as a Cloud Service]&#x200B;(으)로 마이그레이션해야 합니다.

다음 섹션에서는 Adobe에서 업그레이드를 시행하는 이유, 시행 날짜가 계산되는 방법 및 시행 날짜에 발생하는 상황에 대해 설명합니다. 버전별 적용 날짜는 라이프사이클 정책의 [지원 종료 날짜](lifecycle-policy.md#end-of-support-dates) 표를 참조하십시오.

>[!NOTE]
>
>이 항목에서는 클라우드 업그레이드 적용만 다룹니다. 지원 계층 정의의 경우 [지원 종료 날짜](lifecycle-policy.md#end-of-support-dates) 테이블, [보안 전용 전환 규정](lifecycle-policy.md#security-only-transitional-provisions), [타사 소프트웨어 종속성](lifecycle-policy.md#platform-dependencies), [PHP 수명 종료 및 PCI 준수](lifecycle-policy.md#php-end-of-life-and-pci-compliance) 및 [업그레이드 및 마이그레이션 옵션](lifecycle-policy.md#upgrade-and-migration-options)은(는) [라이프사이클 정책](lifecycle-policy.md)을 참조하세요. 지원되는 Adobe Commerce 버전으로 업그레이드할 뿐만 아니라 Adobe에서는 적극적으로 지원되는 버전에 타사 소프트웨어 종속성을 유지해야 합니다.

## Adobe에서 이 정책을 도입하는 이유

Adobe은 Adobe Commerce on Cloud 고객이 실행하는 호스팅 플랫폼 인프라의 보안 및 규정 준수를 담당합니다. 여기에는 모든 기본 소프트웨어 종속성을 최신 상태로 유지하고, 보안 패치를 적용하며, 고객이 의존하는 PCI와 같은 규정 준수 표준을 준수하는 것이 포함됩니다.

공급업체에 의해 기본 소프트웨어 종속성에 대한 보안 지원이 공식적으로 종료되면 Adobe은 더 이상 필요한 수준의 보안 범위와 플랫폼 지원을 제공할 수 없습니다. 지원되지 않는 인프라에서 스토어를 계속 운영하면 고객, 쇼핑객 및 Adobe에 용납될 수 없는 위험이 발생합니다. 따라서 Adobe은 지원되지 않는 Commerce 버전을 실행하는 Adobe 호스팅 클라우드 환경이 비활성화되는 시기를 정의하는 공식적인 강제 버전 업그레이드 시행 정책을 도입합니다.

## 업그레이드 적용 날짜 계산 방법

각 Adobe Commerce 릴리스 라인에 대해 업그레이드 적용 날짜는 다음과 같이 계산됩니다.

**업그레이드 적용 날짜** = 일반 사용 가능 날짜 + 3년 정기 지원 + 1년 연장 지원

확장 지원은 각 릴리스 라인에 대한 일반 지원이 끝날 무렵에 발표됩니다.

## 버전 업그레이드 적용 날짜에 나타나는 결과

게시된 업그레이드 시행 날짜에, Adobe은 영향을 받는 릴리스 버전을 아직 실행 중인 모든 PaaS(Adobe Commerce on Cloud) 환경의 유지 관리를 중단하고 비활성화 권한을 예약합니다. 버전 업그레이드 적용 날짜까지의 주요 이정표에 대한 사전 알림을 받게 됩니다. Adobe에서는 데이터를 검색할 수 있도록 환경 비활성화 전에 데이터 내보내기 창을 제공합니다.

이 정책에 따른 첫 번째 적용 날짜는 **2027년 6월 1일**&#x200B;입니다. 해당 날짜 이전에 확장 지원이 종료되는 릴리스 라인의 경우. 버전별 적용 날짜는 [지원 종료 날짜](lifecycle-policy.md#end-of-support-dates) 표를 참조하십시오.
