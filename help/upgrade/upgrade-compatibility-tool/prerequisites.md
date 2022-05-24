---
title: '"[!DNL Upgrade Compatibility Tool] 전제 조건"'
description: '시스템이 [!DNL Upgrade Compatibility Tool] Adobe Commerce 프로젝트에 사용할 수 있습니다. '
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] 전제 조건

{{commerce-only}}

를 실행하기 위한 최소 요구 사항 [!DNL Upgrade Compatibility Tool] 입니다.

| **요구 사항** | **제한** |
|----------------|-----------------|
| PHP 버전 | >= 7.3 |
| 작성기 | 없음 |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`, 또는 `>=16.0.0`) |
| 메모리 제한 | 최소 2GB RAM |
| Adobe Commerce 액세스 키 | 없음 |
| Adobe Commerce | 없음 |

를 실행할 수 있습니다 [!DNL Upgrade Compatibility Tool] 일부 운영 체제(Windows는 지원되지 않음)에서 사용할 수 있습니다. 를 실행할 필요가 없습니다 [!DNL Upgrade Compatibility Tool] Adobe Commerce 인스턴스가 있는 위치.

이것은 [!DNL Upgrade Compatibility Tool] Adobe Commerce 인스턴스의 소스 코드에 액세스할 수 있습니다. 예를 들어 한 서버에 설치하고 다른 서버에 Adobe Commerce 설치 시 가리킬 수 있습니다. 자세한 내용은 [설치](../upgrade-compatibility-tool/install.md) 주제 를 참조하십시오.

를 실행하는 경우 [!DNL Upgrade Compatibility Tool] 큰 모듈 및 파일이 있는 Adobe Commerce 인스턴스에 대해 도구에 높은 양의 RAM(최소 2GB)이 필요할 수 있습니다. 를 사용할 수 있습니다 `[=MODULE-PATH]` 낮은 메모리 제한으로 인해 문제가 발생하지 않도록 하려면 명령에 모듈 경로 디렉터리를 지정하십시오.

```bash
bin/uct upgrade:check <dir> -m[=MODULE-PATH]
```

여기서 인수는 다음과 같습니다.

- `<dir>`: Adobe Commerce 설치 디렉토리.
- `[=MODULE-PATH]`: 특정 모듈 경로 디렉터리입니다.
