---
title: 배포 개요
description: Commerce 응용 프로그램의 배포 전략에 대해 읽어 보십시오.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---


# 배포 개요

이 항목에서는 Adobe Commerce 버전 2.2 이상의 프로덕션 사이트에 Commerce 응용 프로그램을 배포하는 프로세스에 대해 설명합니다. Adobe은 배포 중 다운타임을 경험하지 않으려는 사이트가 큰 모든 사용자에게 이 배포 방법을 권장합니다.

단일 컴퓨터에 Commerce를 배포하고 배포 중 어느 정도의 다운타임이 발생할 수 있는 경우 [단일 시스템 배포](../deployment/single-machine.md).

## 파이프라인 배포

Commerce 버전 2.2에서는 Adobe이 도입되었습니다 _파이프라인 배포_ 다운타임 없이 프로덕션에 배포할 수 있는 새로운 방법입니다. 이 배포 프로세스는 서로 다른 시스템에서 수행되며 모든 파이프라인 배포 시스템에 대해 일관된 구성을 유지하는 방법을 제공합니다. 이 모델은 간단하지만 강력한 모델로, 일반 구성 설정을 시스템 특정 설정(예: 호스트 및 포트)이나 중요한 설정(예: 이름 및 암호)에서 분리할 수 있습니다.

파이프라인 배포를 사용하려면 Adobe에서 사용자가 다음과 같다고 가정합니다.

- Adobe Commerce 구성 옵션에 대한 뛰어난 지식을 갖춘 숙련된 시스템 통합자.
- 대규모 상거래 사이트(수천 개의 SKU)를 관리하고 프로덕션 사이트의 다운타임을 최소한으로 유지하려는 경우
- PHP 프로그래밍에 대해 잘 알고 있습니다.
- 소스 제어 방법을 사용하는 경험이 있습니다.
- 코드가 소스 제어 저장소에 있습니다. 이 안내서에서는 Git 기반 리포지토리를 사용하고 있다고 가정합니다.

### 다운타임 감소

정적 자산을 배포하고 프로덕션 시스템과 별도로 컴퓨터에 코드를 컴파일할 때 다운타임을 최소화합니다. 운영 시스템의 다운타임은 정적 파일과 컴파일된 코드를 서버에 전송하는 데 필요한 시간으로 제한됩니다.

## 배포 시스템

배포와 관련된 시스템을 설명하려면 다음 용어를 사용합니다.

- **개발 시스템**- 개발자가 코드를 사용자 지정하는 시스템 Commerce Marketplace에서 확장, 테마 및 언어 패키지를 설치합니다. 또한 개발 시스템에서 모든 구성을 변경할 수 있습니다. 많은 개발 시스템이 있을 수 있습니다.

- **빌드 시스템**- 정적 자산을 배포하고 프로덕션 시스템에 대한 코드를 컴파일하는 하나의 시스템입니다. 프로덕션 시스템이 아닌 시스템에서 이러한 자산을 구축하므로 프로덕션 시스템의 다운타임이 최소화됩니다.

   빌드 시스템에는 Commerce가 설치되어 있지 않아도 됩니다. 여기에는 상거래 코드만 필요하지만 데이터베이스 연결이 필요하지 않습니다. 또한 빌드 시스템은 물리적으로 분리된 서버가 될 필요가 없습니다.

- **스테이징 시스템**—_선택 사항입니다_. UAT(사용자 수락 테스트)를 포함하여 모든 통합 코드의 최종 테스트에 사용할 스테이징 시스템을 선택적으로 설정할 수 있습니다. 프로덕션 시스템을 설정하는 것과 동일한 방식으로 스테이징 시스템을 설정합니다. 스테이징이 라이브 스토어가 아니며 고객의 주문을 처리하지 않는다는 점을 제외하면 프로덕션과 동일합니다.

- **프로덕션 시스템**- 라이브 스토어입니다. 여기에서 최소한의 직접 구성을 변경해야 하며, 스테이징 인스턴스에서 테스트되지 않은 것은 확실히 없습니다. 가능한 경우 [데이터 패치](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) 스테이징/개발 인스턴스에서 테스트한 테스트입니다.

## 기타 배포 방법

다음을 포함한 다른 배포 방법을 사용할 수도 있습니다.

- SCP 또는 rsync를 통한 보안 복사
- [카피스트라노](https://capistranorb.com/documentation/overview/what-is-capistrano)
- 다음 [배포 도구](https://deployer.org/)

## 구성 관리

후 모델링 [12단계 앱 디자인의 3단계](https://12factor.net/config)로 지정하는 경우 Commerce는 이제 시스템 자체의 각 시스템에 대한 구성을 저장합니다. (개발 구성 설정은 개발 시스템에 저장되고 프로덕션 설정은 프로덕션 시스템에 저장됩니다.)

Adobe는 시스템의 구성을 동기화하는 방법을 제공합니다.

- **공유 구성**- 시스템별 또는 민감하지 않은 설정입니다.

   공유 설정은 개발 및 프로덕션 시스템에서 일관성을 유지할 설정입니다. 개발 관리자의 공유 구성(또는 클라우드 인프라의 Adobe Commerce)을 설정합니다 _통합_) 시스템.

   공유 구성 파일, `app/etc/config.php`개발, 빌드 및 프로덕션 시스템 간에 공유할 수 있도록 소스 제어에 를 포함해야 합니다.

- **시스템별 구성**- 검색 엔진 호스트 이름 및 포트와 같이 시스템에 따라 다양한 설정을 사용할 수 있습니다.

- **중요한 구성**- 설정해야 하는 설정 _not_ 개인 식별 정보(PII) 또는 API 키 또는 암호와 같은 설정을 노출하므로 소스를 제어할 수 있습니다.

   시스템별 구성 파일 `app/etc/env.php`, 여야 함 _not_ 소스 제어에 포함되거나 시스템 간에 공유될 수 있습니다. 대신, [`magento config:set` 및 `magento:sensitive:set` 명령](../cli/set-configuration-values.md) 를 입력하여 프로덕션 시스템에서 해당 설정에 대한 값을 제공할 수 있습니다.

>[!INFO]
>
>구성을 관리하는 이러한 새로운 방법은 선택 사항입니다. 그럴 필요는 없지만 사용해야 합니다.

대부분의 경우 공유, 시스템 특정 또는 중요한 구성에서 설정한 구성 옵션은 관리자에서 편집할 수 없습니다. 이렇게 하면 모든 시스템에서 설정이 일관되게 유지됩니다. (원할 경우 [`magento config:set` 명령](../cli/set-configuration-values.md) 없는 `--lock` 관리자에서 편집 가능한 설정을 구성하는 옵션.)

각 상거래 구성 옵션에는 고유한 가 있습니다 _구성 경로_. 구성 옵션 값을 설정하려면 CLI 명령 또는 환경 변수를 사용하여 특정 시스템에서 해당 구성 경로 값을 설정할 수 있습니다.