---
title: 변경 사항 마이그레이션
description: 를 사용하여 마지막 Magento 1 데이터 마이그레이션 이후 변경된 데이터만 마이그레이션하는 방법을 알아봅니다. [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# 변경 사항 마이그레이션

증분 마이그레이션 도구는 접두사가 있는 삭제 로그 테이블을 설치합니다 `m2_cl_*`) 및 triggers(for tracking changes)( [데이터 마이그레이션](data.md). 이러한 로그 테이블 및 트리거는 마지막으로 데이터를 마이그레이션한 이후 Magento 1에서 수행한 변경 사항만 마이그레이션하도록 하는 데 필수입니다. 이러한 변경 사항은 다음과 같습니다.

* 고객이 를 통해 추가한 데이터 [상점](https://glossary.magento.com/storefront) (고객 프로필에서 주문, 검토 및 변경 내용 작성)

* 주문, 제품 및 범주가 있는 모든 작업 [관리](https://glossary.magento.com/magento-admin) 패널

>[!NOTE]
>
>속성 또는 CMS 페이지와 같이 관리자를 통해 입력한 다른 모든 신규 또는 업데이트된 엔티티는 증분 마이그레이션에 포함되지 않으며 마이그레이션되지 않습니다.


시작하기 전에 다음 단계를 수행하여 준비하십시오.

1. 다음 방법으로 애플리케이션 서버에 로그인합니다. [파일 시스템 소유자](../../../installation/prerequisites/file-system/overview.md).
1. 로 변경 `/bin` 디렉토리 또는 시스템에 추가되었는지 확인합니다. `PATH`.

자세한 내용은 [첫 단계](overview.md#first-steps) 섹션을 참조하십시오.

## 증분 마이그레이션 명령 실행

증분 변경 사항 마이그레이션을 시작하려면 다음을 실행하십시오.

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

위치:

* `[-r|--reset]` 는 처음부터 마이그레이션을 시작하는 선택적 인수입니다. 마이그레이션을 테스트하는 데 이 인수를 사용할 수 있습니다.

* `[-a|--auto]` 무결성 검사 오류가 발생할 때 마이그레이션이 중지되지 않도록 하는 선택적 인수입니다.

* `{<path to config.xml>}` 의 절대 파일 시스템 경로입니다. `config.xml`; 이 인수는 필수입니다.

>[!NOTE]
>
>증분 마이그레이션은 지속적인 프로세스입니다. 5초마다 자동으로 다시 시작됩니다. 마이그레이션 프로세스를 중단하려면 CTRL-C를 사용합니다.


## 타사 확장에서 만든 데이터 마이그레이션

에서 `Delta` 모드, [!DNL Data Migration Tool] 는 Magento의 자체 모듈로만 작성된 데이터를 마이그레이션하며, 타사 개발자가 만든 코드나 확장에 대한 책임은 없습니다. 이러한 확장이 storefront 데이터베이스에서 데이터를 생성했으며 머천트가 Magento 2에서 이 데이터를 사용하려는 경우 [!DNL Data Migration Tool] 를 만들고 그에 따라 수정해야 합니다.

다음과 같은 경우 [확장](https://glossary.magento.com/extension) 에는 자체 테이블이 있으며, 델타 마이그레이션에 대한 변경 사항을 추적해야 하는 경우 다음 단계를 수행합니다.

1. 추적할 테이블을 `deltalog.xml` 파일
1. 추가 델타 클래스를 만들어 `Migration\App\Step\AbstractDelta`
1. 새로 만든 클래스의 이름을 `config.xml`
