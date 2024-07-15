---
title: 마스크 설정(선택 사항)
description: 파일 시스템 권한을 제한하여 Adobe Commerce 온프레미스 설치의 보안 자세를 개선합니다.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# 마스크 설정(선택 사항)

웹 서버 그룹은 파일 시스템의 특정 디렉터리에 대한 쓰기 권한이 있어야 합니다. 그러나 특히 프로덕션 환경에서는 더 엄격한 보안이 필요할 수 있습니다. [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)을(를) 사용하여 이러한 권한을 추가로 제한할 수 있는 유연성을 제공합니다.

해결 방법은 웹 서버 그룹 및 기타 사용자의 권한을 제한하는 `magento_umask` 파일을 응용 프로그램 루트 디렉터리에 선택적으로 만들 수 있도록 하는 것입니다.

>[!NOTE]
>
>한 명의 사용자 또는 공유 호스팅 시스템에 대해서만 umask를 변경하는 것이 좋습니다. 전용 응용 프로그램 서버가 있는 경우 그룹은 파일 시스템에 대한 쓰기 액세스 권한을 가져야 합니다. umask는 그룹에서 쓰기 액세스 권한을 제거합니다.

기본 umask(`magento_umask`이(가) 지정되지 않음)는 `002`이며, 이는 다음을 의미합니다.

* 775를 사용하면 사용자가 모든 디렉터리를 제어할 수 있으며 그룹이 모든 디렉터리를 트래버스할 수 있습니다. 이러한 권한은 일반적으로 공유 호스팅 공급자에 필요합니다.

* 664 - 사용자가 쓸 수 있고, 그룹이 쓸 수 있으며, 다른 모든 사용자가 읽기 전용입니다

일반적인 제안은 `magento_umask` 파일에서 `022` 값을 사용하는 것입니다. 즉, 다음과 같습니다.

* 디렉토리용 755: 사용자를 위한 모든 권한 및 기타 모든 사용자가 디렉토리를 탐색할 수 있습니다.
* 파일의 경우 644: 사용자에 대한 읽기-쓰기 권한 및 기타 모든 사용자에 대한 읽기 전용 권한.

`magento_umask`을(를) 설정하려면:

1. 명령줄 터미널에서 응용 프로그램 서버에 [파일 시스템 소유자](../prerequisites/file-system/overview.md)(으)로 로그인합니다.
1. 응용 프로그램 설치 디렉토리로 이동합니다.

   ```bash
   cd <Application install directory>
   ```

1. 다음 명령을 사용하여 이름이 `magento_umask`인 파일을 만들고 `umask` 값을 씁니다.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   이제 `<Magento install dir>`에 이름이 `magento_umask`인 파일이 있어야 하며 콘텐츠만 `umask` 번호입니다.

1. 로그아웃한 후 [파일 시스템 소유자](../prerequisites/file-system/overview.md)(으)로 다시 로그인하여 변경 사항을 적용하세요.
