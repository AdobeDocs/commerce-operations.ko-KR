---
title: 명령줄 도구
description: Commerce 명령줄 도구를 사용하여 설치 및 구성 작업을 실행합니다.
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# 명령줄 도구

Commerce에는 하나의 CLI(명령줄 인터페이스)가 있습니다.`<magento_root>/bin/magento`—다음을 포함한 설치 및 구성 작업을 실행합니다.

- Commerce 설치(및 데이터베이스 스키마 업데이트, 배포 구성 만들기 등 관련 작업)
- 캐시 지우기
- 리인덱싱을 포함한 인덱스 관리
- 번역 사전 및 번역 패키지 만들기
- 플러그인에 대한 공장 및 인터셉터와 같이 존재하지 않는 클래스를 생성하여 객체 관리자에 대한 종속성 삽입 구성을 생성합니다.
- 정적 보기 파일 배포
- Less에서 CSS 만들기

추가 이점은 다음과 같습니다.

- 단일 명령(`<magento_root>/bin/magento list`) 사용 가능한 모든 설치 및 구성 명령을 나열합니다.
- Symfony 기반의 일관된 사용자 인터페이스.
- CLI는 타사 개발자가 &quot;플러그인&quot;할 수 있도록 확장 가능합니다. 이는 사용자의 학습곡선을 제거할 수 있다는 추가적인 이점이 있다.
- 비활성화된 모듈에 대한 명령이 표시되지 않습니다.

이 항목에서는 CLI를 사용하여 Adobe Commerce 소프트웨어를 구성하는 방법에 대해 설명합니다. Commerce 설치에 대한 자세한 내용은 [설치 흐름](../../installation/overview.md) 다음에서 _설치 안내서_.

## 전제 조건

CLI를 사용하기 전에 다음을 확인하십시오.

1. 시스템에서 설명한 요구 사항을 충족합니다. [시스템 요구 사항](../../installation/system-requirements.md) 다음에서 _설치 안내서_.
1. 에서 논의한 모든 전제 조건 작업을 완료했습니다. [전제 조건](../../installation/prerequisites/overview.md) 다음에서 _설치 안내서_.
1. Commerce 서버에 로그인한 후 Commerce 파일 시스템에 쓸 수 있는 권한이 있는 사용자로 전환합니다. 다음을 참조하십시오 [파일 시스템 소유자로 전환](../../installation/prerequisites/file-system/overview.md) 다음에서 _설치 안내서_.

## 명령 실행

기본 셸의 경우 다음 구문을 사용하여 파일 시스템 소유자로 전환하고 동시에 명령을 입력합니다.

```bash
su <file system owner> -s /bin/bash -c <command>
```

파일 시스템 소유자가 로그인을 허용하지 않는 경우 다음을 사용할 수 있습니다.

```bash
sudo -u <file system owner> <command>
```

**디렉토리에서 CLI 명령을 실행하려면**:

추가 `<magento_root>/bin` 내 시스템으로 `PATH`.

CentOS용 샘플 bash 쉘:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

선택적으로 다음을 실행할 수 있습니다.

- `cd <magento_root>/bin` 다음 계정으로 실행 `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` 는 웹 서버 docroot의 하위 디렉토리입니다.
