---
title: 변경 사항 마이그레이션
description: 을(를) 사용하여 마지막 Magento 1 데이터 마이그레이션 이후 변경된 데이터만 마이그레이션하는 방법에 대해 알아봅니다. [!DNL Data Migration Tool].
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# 변경 사항 마이그레이션

증분 마이그레이션 도구는 접두사가 있는 deltalog 테이블을 설치합니다. `m2_cl_*`Magento ) 및 (변경 내용 추적을 위한) 트리거 [데이터 마이그레이션](data.md). 이러한 deltalog 테이블 및 트리거는 마지막으로 데이터를 마이그레이션한 이후 Magento 1에서 변경된 사항만 마이그레이션하도록 하는 데 필수적입니다. 이러한 변경 사항은 다음과 같습니다.

* 고객이 storefront를 통해 추가한 데이터(고객 프로필에서 생성된 주문, 검토 및 변경)

* 관리 패널에서 주문, 제품 및 범주를 포함하는 모든 작업

>[!NOTE]
>
>속성 또는 CMS 페이지와 같이 관리자를 통해 입력된 다른 모든 새 엔티티 또는 업데이트된 엔티티는 증분 마이그레이션에 포함되지 않으며 마이그레이션되지 않습니다.


시작하기 전에 다음 단계를 수행하여 준비하십시오.

1. 애플리케이션 서버에 다음으로 로그인 [파일 시스템 소유자](../../../installation/prerequisites/file-system/overview.md).
1. (으)로 변경 `/bin` 디렉토리 또는 시스템에 추가되었는지 확인합니다. `PATH`.

다음을 참조하십시오. [첫 단계](overview.md#first-steps) 섹션에 자세히 설명되어 있습니다.

## 증분 마이그레이션 명령 실행

증분 변경 사항 마이그레이션을 시작하려면 다음을 실행합니다.

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

위치:

* `[-r|--reset]` 는 처음부터 마이그레이션을 시작하는 선택적 인수입니다. 이 인수는 마이그레이션 테스트에 사용할 수 있습니다.

* `[-a|--auto]` 는 무결성 검사 오류가 발생할 때 마이그레이션이 중지되지 않도록 하는 선택적 인수입니다.

* `{<path to config.xml>}` 는 의 절대 파일 시스템 경로입니다. `config.xml`; 이 인수는 필수입니다.

>[!NOTE]
>
>증분 마이그레이션은 연속 프로세스이며, 5초마다 자동으로 다시 시작됩니다. Ctrl-C를 사용하여 마이그레이션 프로세스를 중단합니다.


## 타사 확장에서 만든 데이터 마이그레이션

다음에서 `Delta` 모드, [!DNL Data Migration Tool] 는 Magento의 자체 모듈로만 만들어진 데이터를 마이그레이션하며, 서드파티 개발자가 만든 코드 또는 확장에 대한 책임이 없습니다. 이러한 확장이 상점 데이터베이스에 데이터를 만들었으며 판매자가 이 데이터를 Magento 2 — 의 구성 파일에 보관하려는 경우 [!DNL Data Migration Tool] 를 만들고 그에 따라 수정해야 합니다.

확장에 자체 테이블이 있고 델타 마이그레이션에 대한 변경 사항을 추적해야 하는 경우 다음 단계를 수행합니다.

1. 추적할 테이블을 `deltalog.xml` 파일
1. 를 확장하는 추가 델타 클래스 만들기 `Migration\App\Step\AbstractDelta`
1. 새로 만든 클래스의 이름을 의 델타 모드 섹션에 추가합니다. `config.xml`
