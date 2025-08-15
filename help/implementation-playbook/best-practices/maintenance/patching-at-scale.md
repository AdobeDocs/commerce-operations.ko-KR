---
title: 규모에 맞게 패치를 배포하기 위한 모범 사례
description: Adobe Commerce에 대한 중앙 집중식 패치가 엔터프라이즈 프로젝트 관리에 어떻게 도움이 되는지 알아봅니다.
role: Developer
feature: Best Practices
badge: label="Tony Evers, 수석 기술 설계자, Adobe 제공" type="Informative" url="https://www.linkedin.com/in/evers-tony/" tooltip="토니 에버스의 기고문"
exl-id: 08c38dc5-3dc2-49ee-b56f-59e1718e12b5
source-git-commit: 2c9f827326315bc4ef77d511dddce81e059a1092
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# Adobe Commerce 패치를 대규모로 배포하기 위한 우수 사례

여러 Adobe Commerce 설치를 관리하는 경우 [패치](../../../upgrade/patches/apply.md)는 복잡한 프로세스일 수 있습니다. _중앙 집중식 패치_&#x200B;은(는) 엔터프라이즈의 모범 사례입니다. 모든 Adobe Commerce 설치에 올바른 패치를 적용하는 데 도움이 됩니다. 이 항목에서는 모든 유형의 Adobe Commerce [패치](../../../upgrade/patches/overview.md)에 대해 중앙 집중식 패치 배포를 수행하는 방법을 설명합니다.

>[!NOTE]
>
>다음 콘텐츠는 원래 Adobe 기술 블로그의 [규모에 Adobe Commerce 패치 배포](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) 게시물에 게시되었습니다. 중앙 집중식 패치 전략을 구현하기 위한 단계 및 코드 샘플에 중점을 두도록 수정되었습니다. 여기에 설명된 다양한 유형의 패치에 대한 자세한 내용은 원래 게시물을 참조하십시오.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 전략

패치 종류가 다양하고 적용 방법도 많기 때문에 어떤 패치가 먼저 적용되는지 어떻게 아십니까? 패치가 많을수록 동일한 파일이나 동일한 코드 행에 적용할 가능성이 커집니다. 패치는 다음 순서로 적용됩니다.

1. **보안 패치**&#x200B;은(는) Adobe Commerce 릴리스의 정적 코드 기반의 일부입니다.
1. **Composer 패치**&#x200B;부터 `composer install`까지 및 `composer update`cweagans/composer-patches[와(과) 같은 ](https://packagist.org/packages/cweagans/composer-patches)개의 플러그인.
1. **Commerce용 클라우드 패치** 패키지에 포함된 모든 [필수 패치](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).
1. 선택한 **품질 패치**&#x200B;이(가) [[!DNL [Quality Patches Tool]]](../../../tools/quality-patches-tool/usage.md)에 포함되어 있습니다.
1. **디렉터리의**&#x200B;사용자 지정 패치`/m2-hotfixes` 및 Adobe Commerce 지원 패치는 패치 이름별로 알파벳순으로 정렬됩니다.

   >[!IMPORTANT]
   >
   >패치를 많이 적용할수록 코드가 더 복잡해집니다. 복잡한 코드를 사용하면 새 버전의 Adobe Commerce로의 업그레이드가 더욱 어려워지고 총 소유 비용이 증가할 수 있습니다.

Adobe Commerce의 여러 설치를 유지 관리하는 책임이 있는 경우 모든 인스턴스에 동일한 패치 세트가 설치되도록 하는 것은 어려울 수 있습니다. 각 설치에는 자체 git 저장소, `/m2-hotfixes` 디렉터리 및 `composer.json` 파일이 있습니다. 클라우드 사용자를 위한 **보안 패치** 및 **필수 패치**&#x200B;이(가) 기본 Adobe Commerce 버전의 일부로 모두 설치되었음을 보증할 수 있습니다.

현재 이 문제에 대한 중앙 집중식 단일 솔루션이 없지만 Composer는 이러한 차이를 메울 수 있는 방법을 제공합니다. [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) 패키지를 사용하면 [종속성에서 패치를 적용](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies)할 수 있습니다. 모든 패치를 설치하는 Composer 패키지를 만든 다음 모든 프로젝트에 해당 패키지가 필요합니다.

여기에는 **보안 패치**, **필수 패치** 및 **작성기 패치**&#x200B;가 포함되지만 품질 패치와 `/m2-hotfixes` 디렉터리의 내용은 어떻습니까?

## 품질 패치 및 핫픽스 적용

`vendor/bin/magento-patches apply` 명령을 사용하여 클라우드 인프라와 온-프레미스 설치 모두에 품질 패치를 설치할 수 있습니다. `vendor/bin/magento-patches apply` 작업 후에 `composer install` 명령이 실행되는지 확인해야 합니다.

>[!NOTE]
>
>클라우드 인프라에서는 프로젝트의 `.magento.env.yaml` 파일에 품질 패치를 나열하여 설치할 수도 있습니다. 여기에 설명된 예제에서는 `vendor/bin/magento-patches apply` 명령을 사용해야 합니다.

사용자 지정 작성기 구성 요소 패키지의 `composer.json` 파일에 적용할 패치를 지정한 다음, `composer install` 작업 후에 명령을 실행하는 플러그인 패키지를 만들 수 있습니다.

요약하자면, 이 중앙 집중식 패치 적용 예제를 사용하려면 두 개의 사용자 지정 Composer 패키지를 생성해야 합니다.

- **구성 요소 패키지:** `centralized-patcher`

   - 설치할 품질 패치 및 `m2-hotfixes` 목록을 정의합니다.
   - `centralized-patcher-composer-plugin` 작업 후 `vendor/bin/magento-patches apply` 명령을 실행하는 `composer install` 패키지가 필요합니다.

- **플러그 인 패키지:** `centralized-patcher-composer-plugin`

   - `CentralizedPatcher` 패키지에서 품질 패치 목록을 읽는 `centralized-patcher` PHP 클래스를 정의합니다.
   - `vendor/bin/magento-patches apply` 작업 후 품질 패치 목록을 설치하려면 `composer install` 명령을 실행합니다.

### `centralized-patcher`

작성기 구성 요소 패키지(`centralized-patcher`)를 만들어 모든 Adobe Commerce 설치에서 모든 품질 패치와 `/m2-hotfixes`을(를) 중앙에서 관리할 수 있습니다.

구성 요소 패키지는 다음 작업을 수행해야 합니다.

- 배포 중에 `/m2-hotfixes` 디렉터리의 내용을 모든 설치에 복사합니다.
- 설치할 품질 패치 목록을 정의합니다.
- `vendor/bin/magento-patches` 명령을 실행하여 모든 설치에 동일한 품질 패치 목록을 설치합니다([`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) 플러그인 패키지를 종속성으로 사용).

`centralized-patcher` 구성 요소 패키지를 만들려면:

1. 다음 내용이 포함된 `composer.json` 파일을 만듭니다.

   >[!NOTE]
   >
   >다음 예제의 `require` 특성은 나중에 이 예제를 만들어야 하는 `require`플러그 인 패키지[에 대한 ](#centralized-patcher-composer-plugin) 종속성을 보여줍니다.

   ```json
   {
    "name": "magento-services/centralized-patcher",
    "version": "0.0.1",
    "description": "Centralized patcher for patching multiple web stores from a central place",
    "type": "magento2-component",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "magento-services/centralized-patcher-composer-plugin": "~0.0.1"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "extra": {
        "map": [
        ],
   }
   ```

1. 패키지 내에 `/m2-hotfixes` 디렉터리를 만들어 `map` 파일의 `composer.json` 특성에 추가합니다. `map` 특성에는 이 패키지에서 패치할 대상 프로젝트의 루트로 복사할 파일이 포함되어 있습니다.

   ```json
   {
    ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
   }
   ```

   >[!NOTE]
   >
   >`centralized-patcher` 패키지는 `/m2-hotfixes` 디렉터리의 내용을 `composer install`에 있는 대상 프로젝트의 m2 핫픽스 디렉터리에 복사합니다.  클라우드 배포 스크립트는 `composer install` 뒤에 m2 핫픽스를 적용하므로 모든 핫픽스는 배포 메커니즘에 의해 설치됩니다.

1. `quality-patches` 특성에 설치할 품질 패치를 정의합니다.

   ```json
   {
   ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
        "quality-patches": [
            "MDVA-30106",
            "MDVA-12304"
        ]
   }
   ```


이전 코드 샘플의 `quality-patches` 특성에는 예를 들어 [전체 패치 목록](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)의 패치가 두 개 있습니다.  이 품질 패치는 `centralized-patcher` 명령을 사용하여 `vendor/bin/magento-patches apply` 패키지가 필요한 모든 프로젝트에 설치됩니다.

테스트 목적으로 예제 패치(`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`)를 만들 수 있습니다.

>[!NOTE]
>
>Adobe Commerce 지원에서 직접 받은 패치와 함께 고유한 패치를 `m2-hotfixes` 디렉터리에 배치해야 합니다.

예제 패치 파일(`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`):

```diff
diff --git a/vendor/magento/framework/Mview/View/Subscription.php b/vendor/magento/framework/Mview/View/Subscription.php
index 03a3bf9..681e0b0 100644
--- a/vendor/magento/framework/Mview/View/Subscription.php
+++ b/vendor/magento/framework/Mview/View/Subscription.php
@@ -16,6 +16,7 @@ use Magento\Framework\Mview\ViewInterface;
 
 /**
  * Mview subscription.
+ * Test Patch File
  */
 class Subscription implements SubscriptionInterface
 {
```

### `centralized-patcher-composer-plugin`

이 예제에서는 온-프레미스 메서드를 사용하여 품질 패치를 설치하므로 `vendor/bin/magento-patches apply` 작업 후에 `composer install` 명령을 실행해야 합니다. 이 플러그인은 `composer install` 명령을 실행하는 `vendor/bin/magento-patches apply` 작업 후에 트리거됩니다.

`centralized-patcher-compose-plugin` 구성 요소 패키지를 만들려면:

1. 다음 내용이 포함된 `composer.json` 파일을 만듭니다.

   ```json
   {
    "name": "magento-services/centralized-patcher-composer-plugin",
    "version": "0.0.1",
    "description": "Centralized patcher composer plugin to apply quality patches from the centralized patcher",
    "type": "composer-plugin",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "symfony/process": "^4.1 || ^5.1",
        "magento/magento-cloud-patches": "~1.0.20",
        "magento/framework": "~103.0.5-p1",
        "composer-plugin-api": "^2.0"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "suggest": {
        "magento-services/centralized-patcher": "~0.0.1"
    },
    "autoload": {
        "psr-4": {
            "MagentoServices\\CentralizedPatcherComposerPlugin\\": ""
        }
    },
    "extra": {
        "class": "MagentoServices\\CentralizedPatcherComposerPlugin\\Patcher"
    }
   }
   ```

1. PHP 파일을 만들고 `CentralizedPatcher` 클래스를 정의하여 [`centralized-patcher`](#centralized-patcher) 구성 요소 패키지에서 품질 패치 목록을 읽고 매 `composer install` 작업 후 즉시 설치합니다.

   ```php
   <?php
   declare(strict_types=1);
   
   namespace MagentoServices\CentralizedPatcherComposerPlugin;
   
   use Composer\Composer;
   use Composer\EventDispatcher\EventSubscriberInterface;
   use Composer\IO\IOInterface;
   use Composer\Plugin\PluginInterface;
   use Composer\Script\ScriptEvents;
   use Symfony\Component\Process\Exception\ProcessFailedException;
   use Symfony\Component\Process\Process;
   
   class Patcher implements PluginInterface, EventSubscriberInterface
   {
    /**
     * @var Composer $composer
     */
    protected $composer;
   
    /**
     * @var IOInterface $io
     */
    protected $io;
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function activate(Composer $composer, IOInterface $io)
    {
        $this->composer = $composer;
        $this->io = $io;
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function deactivate(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function uninstall(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @return string[]
     */
    public static function getSubscribedEvents()
    {
        return [
            ScriptEvents::POST_UPDATE_CMD => 'installPatches',
            ScriptEvents::POST_INSTALL_CMD => 'installPatches',
        ];
    }
   
    /**
     * Apply patches from magento-services/centralized-patcher
     *
     * @param \Composer\Script\Event $event
     * @return void
     */
    public function installPatches(\Composer\Script\Event $event)
    {
        $patches = [];
        $this->io->write('Applying centralized quality patches');
        $packages = $this->composer->getLocker()->getLockData()['packages'];
        foreach ($packages as $package) {
            if ($package['name'] !== 'magento-services/centralized-patcher') {
                continue;
            }
            $patches = $package['extra']['quality-patches'] ?? [];
        }
        if (empty($patches)) {
            $this->io->error("No centralized quality patches to install");
            exit(0);
        }
        $command = array_merge(
            ['php','./vendor/bin/magento-patches','apply','--no-interaction'],
             $patches
        );
        $process = new Process($command);
        try {
            $this->io->debug($process->getCommandLine());
            $process->mustRun();
            $this->io->write(
                str_replace("\n\n", "\n", trim($process->getErrorOutput() ?: $process->getOutput(), "\n"))
            );
        } catch (ProcessFailedException $e) {
            $process = $e->getProcess();
            $error = sprintf(
                'The command "%s" failed. %s',
                $process->getCommandLine(),
                trim($process->getErrorOutput() ?: $process->getOutput(), "\n")
            );
            throw new \RuntimeException($error, $process->getExitCode());
        }
    }
   }
   ```

>[!TIP]
>
>이 예제에 설명된 두 패키지를 실제로 보려면 [code-examples](#code-examples)을 참조하세요.


## 프로젝트별 패치로 수행할 작업

일부 패치가 특정 인스턴스에만 적용되는 반면, 모든 프로젝트에서 95%의 패치만 필요한 시나리오가 있을 수 있습니다. 패치를 적용하는 일반적인 방법은 여전히 작동합니다. `/m2-hotfixes` 디렉터리에 프로젝트별 패치를 유지하고 프로젝트당 품질 패치를 설치할 수 있습니다.

이 방법을 사용하는 경우 **구성 요소 패키지로 프로젝트에 복사된** 디렉터리에 있는 패치를 `/m2-hotfixes`커밋하지 마십시오`centralized-patcher`. `/m2-hotfixes` 파일에 `.gitignore`을(를) 추가하여 실수로 커밋하는 것을 방지할 수 있습니다. `.gitignore` 파일을 업데이트한 후에는 `/m2-hotfixes` 명령을 사용하여 모든 프로젝트 관련 `git add –force`을(를) 추가해야 합니다.

## 다른 Adobe Commerce 버전 실행

`centralized-patcher` 구성 요소 패키지에서 올바른 종속성을 설정했는지 확인하십시오. 예를 들어, 패키지의 특정 버전에 Adobe Commerce 2.4.5-p2가 필요할 수 있으며, 이 버전에서는 Adobe Commerce 2.4.5-p2와 호환되는 패치만 제공합니다. Adobe Commerce 2.4.4와 호환되는 이 패키지의 다른 버전이 있을 수 있습니다.

## 결과 이해

클라우드 인프라의 Adobe Commerce과 마찬가지로 이 문서에서는 배포 프로세스가 `composer install` 또는 `composer update`이(가) 아닌 `git pull` 명령을 사용하여 서버에 새 코드를 배포한다고 가정합니다. 그런 다음 중앙 집중식 패치 설치의 흐름은 다음과 같습니다.

1. Composer 설치

   - -p1 또는 -p2 보안 및 기능 패치를 포함한 Adobe Commerce 설치
   - 중앙 집중식 `/m2-hotfixes` 및 지원 패치를 프로젝트별 `/m2-hotfixes` 및 지원 패치와 결합
   - `cweagans/composer-patches` 작성기 패키지와 함께 설치된 모든 패치를 적용합니다.

1. `composer install` 이후

   - Composer 플러그인이 중앙 집중식 품질 패치를 설치합니다.

1. 배포

   - 필요한 패치와 프로젝트별 품질 패치가 `.magento.env.yaml` 파일을 기반으로 설치됩니다(Adobe Commerce 클라우드 인프라 프로젝트에만 해당).
   - `/m2-hotfixes` 디렉터리의 사용자 지정 패치와 지원 패치가 패치 이름별로 알파벳순으로 설치되어 있습니다.

이렇게 하면 모든 설치에 대한 모든 패치를 중앙에서 관리할 수 있으며 Adobe Commerce 스토어의 보안 및 안정성을 더 잘 보장할 수 있습니다. 패치 상태를 확인하려면 다음 방법을 사용하십시오.

- [클라우드 인프라 프로젝트](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [온-프레미스 프로젝트](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## 코드 예

- [Magento Open Source의 중앙 집중식 패치](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [클라우드 인프라의 Adobe Commerce에 중앙 집중식 패치](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Centralized Patcher Composer 플러그인](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [중앙 패처 구성 요소](https://github.com/AntonEvers/centralized-patcher)
