---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# 빌드 시스템 업데이트

**빌드 시스템을 업데이트하려면**:

1. 빌드 시스템에 파일 시스템 소유자로 로그인합니다.
1. 애플리케이션 루트 디렉토리로 변경합니다.

   ```bash
   cd <Magento root dir>
   ```

1. 소스 제어에서 `app/etc/config.php`에 대한 변경 내용을 가져옵니다.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. 코드를 컴파일합니다.

   ```bash
   bin/magento setup:di:compile
   ```

1. 코드가 컴파일되면 정적 보기 파일을 생성합니다.

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. 소스 제어에 대한 변경 내용을 확인합니다.

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
