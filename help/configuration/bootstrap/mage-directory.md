---
title: 기본 디렉토리 경로 사용자 정의
description: MAGE_DIRS 변수를 사용하여 절대 경로의 배열을 설정합니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# 기본 디렉터리 경로

다음 `MAGE_DIRS` 환경 변수를 사용하면 상거래 응용 프로그램에서 다양한 파일에 대한 절대 경로를 빌드하거나 URL을 생성하는 데 사용하는 사용자 지정 기본 디렉토리 경로 및 기본 URL의 조각을 지정할 수 있습니다.

## MAGE_DIRS 설정

키가 상수인 연관 배열을 지정합니다 [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] 및 값은 각각 디렉토리 또는 해당 URL 경로의 절대 경로입니다.

다음을 설정할 수 있습니다 `MAGE_DIRS` 다음 방법 중 하나로 사용됩니다.

- [부트스트랩 매개 변수의 값 설정](../bootstrap/set-parameters.md)
- 다음과 같은 사용자 지정 시작 지점 스크립트를 사용합니다.

   ```php
   <?php
   /**
    * Copyright © Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\App\Bootstrap;
   use Magento\Framework\App\Filesystem\DirectoryList;
   use Magento\Framework\App\Http;
   
   require __DIR__ . '/app/bootstrap.php';
   $params = $_SERVER;
   $params[Bootstrap::INIT_PARAM_FILESYSTEM_DIR_PATHS] = [
        DirectoryList::PUB => [DirectoryList::URL_PATH => ''],
        DirectoryList::MEDIA => [DirectoryList::PATH => '/mnt/nfs/media', DirectoryList::URL_PATH => ''],
        DirectoryList::STATIC_VIEW => [DirectoryList::URL_PATH => 'static'],
        DirectoryList::UPLOAD => [DirectoryList::URL_PATH => '/mnt/nfs/media/upload'],
        DirectoryList::CACHE => [DirectoryList::PATH => '/mnt/nfs/cache'],
   ];
   $bootstrap = Bootstrap::create(BP, $params);
   /** @var Http $app */
   $app = $bootstrap->createApplication(Http::class);
   $bootstrap->run($app);
   ```

앞의 예제에서는 `[cache]` 및 `[media]` 디렉토리 `/mnt/nfs/cache` 및 `/mnt/nfs/media`각각 입니다.

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
