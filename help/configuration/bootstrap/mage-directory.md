---
title: 기본 디렉터리 경로 사용자 지정
description: MAGE_DIRS 변수를 사용하여 절대 경로 배열을 설정합니다.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# 기본 디렉터리 경로

`MAGE_DIRS` 환경 변수를 사용하면 Commerce 응용 프로그램에서 다양한 파일에 대한 절대 경로를 작성하거나 URL을 생성하는 데 사용하는 기본 URL의 조각과 사용자 지정 기본 디렉터리 경로를 지정할 수 있습니다.

## MAGE_DIRS 설정

키가 각각 [\\Magento\\App\\Filesystem\\DirectoryList][directory-list]의 상수이고 값이 디렉터리의 절대 경로 또는 해당 URL 경로인 연관 배열을 지정합니다.

다음 방법 중 하나로 `MAGE_DIRS`을(를) 설정할 수 있습니다.

- [부트스트랩 매개 변수 값 설정](../bootstrap/set-parameters.md)
- 다음과 같은 사용자 지정 진입점 스크립트를 사용합니다.

  ```php
  <?php
  /**
   * Copyright [first year code created] Adobe
   * All Rights Reserved.
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

앞의 예제에서는 `[cache]` 및 `[media]` 디렉터리의 경로를 각각 `/mnt/nfs/cache` 및 `/mnt/nfs/media`(으)로 설정합니다.

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
