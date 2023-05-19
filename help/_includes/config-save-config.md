---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# 공유 구성 업데이트

**구성을 업데이트하려면**:

1. 개발 시스템에 파일 시스템 소유자로 로그인하거나 파일 시스템 소유자로 전환합니다.

1. 애플리케이션 루트로 변경하고 dump 명령을 실행합니다.

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   예를 들어 Commerce가에 설치된 경우 `/var/www/html/magento2`, 다음을 입력합니다.

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. 다음을 확인합니다 `app/etc/config.php` 이(가) 업데이트되었습니다.

   ```bash
   git status
   ```

   샘플 응답:

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >실행 _아님_ 에 변경 사항 제출 `generated`, `pub/media`, 또는 `pub/static` 소스 제어의 디렉터리. 빌드 시스템에서 이러한 파일을 생성합니다. 개발 시스템에는 프로덕션 시스템에서 사용할 준비가 되지 않은 코드, 테마 등이 있을 수 있습니다.

1. 변경 내용을 체크 인합니다. `app/etc/config.php` 소스 제어에만 적용됩니다.

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
