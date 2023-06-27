---
title: 마스크 설정(선택 사항)
description: 파일 시스템 권한을 제한하여 Adobe Commerce 또는 Magento Open Source 온프레미스 설치의 보안 자세를 개선합니다.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 마스크 설정(선택 사항)

웹 서버 그룹은 파일 시스템의 특정 디렉터리에 대한 쓰기 권한이 있어야 합니다. 그러나 특히 프로덕션 환경에서는 더 엄격한 보안이 필요할 수 있습니다. 를 사용하여 이러한 권한을 추가로 제한할 수 있는 유연성을 제공합니다. [마스크](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

해결 방법은 다음 파일을 선택적으로 만들 수 있도록 하는 것입니다. `magento_umask` 웹 서버 그룹 및 기타 사용자의 권한을 제한하는 응용 프로그램 루트 디렉터리의

>[!NOTE]
>
>한 명의 사용자 또는 공유 호스팅 시스템에 대해서만 umask를 변경하는 것이 좋습니다. 전용 응용 프로그램 서버가 있는 경우 그룹은 파일 시스템에 대한 쓰기 액세스 권한을 가져야 합니다. umask는 그룹에서 쓰기 액세스 권한을 제거합니다.

기본 마스크(없음) `magento_umask` 지정됨)은 `002`: 다음을 의미합니다.

* 775를 사용하면 사용자가 모든 디렉터리를 제어할 수 있으며 그룹이 모든 디렉터리를 트래버스할 수 있습니다. 이러한 권한은 일반적으로 공유 호스팅 공급자에 필요합니다.

* 664 - 사용자가 쓸 수 있고, 그룹이 쓸 수 있으며, 다른 모든 사용자가 읽기 전용입니다

일반적인 제안 사항은 값을 사용하는 것입니다. `022` 다음에서 `magento_umask` 파일, 즉

* 디렉토리용 755: 사용자를 위한 모든 권한 및 기타 모든 사용자가 디렉토리를 탐색할 수 있습니다.
* 파일의 경우 644: 사용자에 대한 읽기-쓰기 권한 및 기타 모든 사용자에 대한 읽기 전용 권한.

설정 `magento_umask`:

1. 명령줄 터미널에서 애플리케이션 서버에 다음으로 로그인합니다. [파일 시스템 소유자](../prerequisites/file-system/overview.md).
1. 응용 프로그램 설치 디렉토리로 이동합니다.

   ```bash
   cd <Application install directory>
   ```

1. 다음 명령을 사용하여 다음 파일을 생성합니다 `magento_umask` 및 작성 `umask` 가치있는 일입니다.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   이제 이름이 인 파일이 있어야 합니다. `magento_umask` 다음에서 `<Magento install dir>` (콘텐츠만 `umask` 숫자.

1. 에서 로그아웃했다가 다음으로 다시 로그인합니다. [파일 시스템 소유자](../prerequisites/file-system/overview.md) 를 눌러 변경 사항을 적용합니다.
