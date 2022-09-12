---
title: umask 설정(선택 사항)
description: 파일 시스템 권한을 제한하여 Adobe Commerce 또는 Magento Open Source 온프레미스 설치의 보안 자세를 개선합니다.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# umask 설정(선택 사항)

웹 서버 그룹은 파일 시스템의 특정 디렉터리에 대한 쓰기 권한이 있어야 합니다. 그러나, 특히 생산에서 더욱 강력한 보안을 원할 수도 있습니다. Adobe는 다음을 사용하여 이러한 권한을 추가로 제한할 수 있는 유연성을 제공합니다. [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Adobe의 해결 방법은 다음과 같은 파일을 선택적으로 만들 수 있도록 하는 것입니다 `magento_umask` 웹 서버 그룹 및 기타 모든 사용자에 대한 권한을 제한하는 응용 프로그램 루트 디렉토리에서 다음 작업을 수행합니다.

>[!NOTE]
>
>한 사용자 또는 공유 호스팅 시스템에서만 umask를 변경하는 것이 좋습니다. 전용 응용 프로그램 서버가 있는 경우 해당 그룹은 파일 시스템에 대한 쓰기 액세스 권한이 있어야 합니다. umask는 그룹에서 쓰기 액세스를 제거합니다.

기본 umask(없음) `magento_umask` 지정된) `002`즉,

* 775는 사용자가 완전히 제어하고, 그룹에 의해 완전히 제어되며, 모든 사람이 디렉터리를 트래버스할 수 있도록 하는 디렉토리를 의미합니다. 이러한 권한은 일반적으로 공유 호스팅 공급자에 의해 필요합니다.

* 파일용 664: 사용자가 쓰기 가능, 그룹에 의해 쓰기 가능, 기타 모든 사용자가 읽기 전용

일반적인 제안은 값을 사용하는 것입니다. `022` 에서 `magento_umask` 파일:

* 디렉토리의 경우 755: 사용자에 대한 모든 제어 및 다른 모든 사용자가 디렉토리를 트래버스할 수 있습니다.
* 644(파일의 경우): 사용자의 읽기-쓰기 권한 및 기타 모든 사용자에 대한 읽기 전용.

설정하려면 `magento_umask`:

1. 명령줄 터미널에서 응용 프로그램 서버에 [파일 시스템 소유자](../prerequisites/file-system/overview.md).
1. 응용 프로그램 설치 디렉토리로 이동합니다.

   ```bash
   cd <Application install directory>
   ```

1. 다음 명령을 사용하여 `magento_umask` 그리고 `umask` 값을 로 설정합니다.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   이제 이름이 인 파일이 있어야 합니다. `magento_umask` 에서 `<Magento install dir>` 유일한 콘텐츠가 `umask` 번호.

1. 로그아웃한 후 다시 로그인하십시오. [파일 시스템 소유자](../prerequisites/file-system/overview.md) 변경 사항을 적용하려면
