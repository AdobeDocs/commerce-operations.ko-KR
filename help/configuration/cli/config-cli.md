---
title: 명령줄 도구
description: 전자 상거래 명령줄 도구를 사용하여 설치 및 구성 작업을 실행합니다.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---


# 명령줄 도구

상거래에 하나의 CLI(명령줄 인터페이스)—`<magento_root>/bin/magento`—다음을 포함하여 설치 및 구성 작업을 실행합니다.

- 상거래 설치(및 데이터베이스 스키마 업데이트, 배포 구성 만들기 등의 관련 작업)
- 캐시 지우기
- 재색인을 포함한 인덱스 관리
- 번역 사전 및 번역 패키지 만들기
- 플러그인을 위한 공장 및 인터셉터와 같은 존재하지 않는 클래스를 생성하여 객체 관리자에 대한 종속성 주입 구성을 생성합니다
- 정적 보기 파일 배포
- 최소한으로 CSS 만들기

추가 이점은 다음과 같습니다.

- 단일 명령(`<magento_root>/bin/magento list`) 사용 가능한 모든 설치 및 구성 명령을 나열합니다.
- Symfony를 기반으로 일관된 사용자 인터페이스
- CLI는 확장 가능하므로 타사 개발자가 CLI를 &quot;플러그인&quot;할 수 있습니다. 이로 인해 사용자의 학습 곡선을 없앨 수 있습니다.
- 비활성화된 모듈에 대한 명령이 표시되지 않습니다.

이 항목에서는 CLI를 사용하여 Adobe Commerce 및 Magento Open Source 소프트웨어를 구성하는 방법을 설명합니다. 상거래 설치에 대한 자세한 내용은 [설치 흐름](https://devdocs.magento.com/guides/v2.4/install-gde/install-flow-diagram.html) 에서 _설치 안내서_.

## 전제 조건

CLI를 사용하기 전에 다음을 확인하십시오.

1. 시스템이 [시스템 요구 사항](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 에서 _설치 안내서_.
1. 에 설명된 모든 전제 조건 작업을 완료했습니다. [전제 조건](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/prereq-overview.html) 에서 _설치 안내서_.
1. 상거래 서버에 로그인한 후 상거래 파일 시스템에 쓸 수 있는 권한이 있는 사용자로 전환하십시오. 자세한 내용은 [파일 시스템 소유자에게 전환](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) 에서 _설치 안내서_.

## 실행 중인 명령

bash 쉘의 경우 다음 구문을 사용하여 파일 시스템 소유자로 전환하고 명령을 동시에 입력합니다.

```bash
su <file system owner> -s /bin/bash -c <command>
```

파일 시스템 소유자가 로그인을 허용하지 않는 경우 다음을 사용할 수 있습니다.

```bash
sudo -u <file system owner> <command>
```

**모든 디렉토리에서 CLI 명령을 실행하려면**:

추가 `<magento_root>/bin` 시스템에 `PATH`.

CentOS용 샘플 bash 셸:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

다음을 실행할 수 있습니다(선택적).

- `cd <magento_root>/bin` 그리고 `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` 는 웹 서버 docroot의 하위 디렉토리입니다.
