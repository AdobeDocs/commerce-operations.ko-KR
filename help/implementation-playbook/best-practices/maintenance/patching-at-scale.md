---
title: 규모에 맞게 패치를 배포하기 위한 모범 사례
description: Adobe Commerce에 대한 중앙 집중식 패치가 엔터프라이즈 프로젝트 관리에 어떻게 도움이 되는지 알아봅니다.
role: Developer
feature: Best Practices
badge: label="Anton Evers, 수석 기술 설계자, Adobe의 기여" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="안톤 에버스의 기여"
source-git-commit: 9cda88a4aeb4cc58d8ec9c4417e3107885a6cdb8
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---


# Adobe Commerce 패치를 대규모로 배포하기 위한 우수 사례

여러 Adobe Commerce 설치를 관리하는 경우 [패치](../../../upgrade/patches/apply.md) 은(는) 복잡한 프로세스일 수 있습니다. _중앙 집중식 패치_ 의 필수적인 부분 [글로벌 참조 아키텍처](../../architecture/global-reference/overview.md) 기업을 위한 모범 사례 모든 Adobe Commerce 설치에 올바른 패치를 적용하는 데 도움이 됩니다. 이 항목에서는 모든 유형의 Adobe Commerce에 대해 중앙 집중식 패치 배포를 수행하는 방법을 설명합니다 [패치](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>다음 콘텐츠는 원래 다음에 게시되었습니다. [규모에 맞게 Adobe Commerce 패치 배포](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) Adobe 기술 블로그에 게시합니다. 중앙 집중식 패치 전략을 구현하기 위한 단계 및 코드 샘플에 중점을 두도록 수정되었습니다. 여기에 설명된 다양한 유형의 패치에 대한 자세한 내용은 원래 게시물을 참조하십시오.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 전략

패치 종류가 다양하고 적용 방법도 많기 때문에 어떤 패치가 먼저 적용되는지 어떻게 아십니까? 패치가 많을수록 동일한 파일이나 동일한 코드 행에 적용할 가능성이 커집니다. 패치는 다음 순서로 적용됩니다.

1. **보안 패치** 는 Adobe Commerce 릴리스의 정적 코드 기반의 일부입니다.
1. **Composer 패치** 에서 `composer install` 및 `composer update` 다음과 같은 플러그인 [cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches).
1. 모두 **필요한 패치** 다음에 포함됨: [Commerce용 클라우드 패치](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) 패키지.
1. 선택됨 **품질 패치** 다음에 포함됨: [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **사용자 지정 패치** 및 의 Adobe Commerce 지원 패치 `/m2-hotfixes` 디렉토리(패치 이름별 알파벳순)

   >[!IMPORTANT]
   >
   >패치를 많이 적용할수록 코드가 더 복잡해집니다. 복잡한 코드를 사용하면 새 버전의 Adobe 상거래로의 업그레이드가 더욱 어려워지고 총 소유 비용이 증가할 수 있습니다.

Adobe Commerce의 여러 설치를 유지 관리하는 책임이 있는 경우 모든 인스턴스에 동일한 패치 세트가 설치되도록 하는 것은 어려울 수 있습니다. 각 설치에는 자체 git 저장소가 있으며, `/m2-hotfixes` 디렉토리 및 `composer.json` 파일. 이 보증은 **보안 패치** 및 **필요한 패치** cloud용 사용자는 모두 기본 Adobe Commerce 버전의 일부로 설치됩니다.

현재 이 문제에 대한 중앙 집중식 단일 솔루션이 없지만 Composer는 이러한 차이를 메울 수 있는 방법을 제공합니다. 다음 [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) 패키지를 사용하면 다음 작업을 수행할 수 있습니다. [종속성에서 패치 적용](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). 모든 패치를 설치하는 Composer 패키지를 만든 다음 모든 프로젝트에 해당 패키지가 필요합니다.

다음을 포함합니다. **보안 패치**, **필요한 패치**, 및 **Composer 패치**, 하지만 품질 패치와 의 콘텐츠는 어떻습니까? `/m2-hotfixes` 디렉토리?

## 품질 패치 및 핫픽스 적용

다음을 사용하여 클라우드 인프라와 온프레미스 설치 모두에 품질 패치를 설치할 수 있습니다. `vendor/bin/magento-patches apply` 명령입니다. 다음을 확인해야 합니다. `vendor/bin/magento-patches apply` 다음 시간 이후에 명령 실행 `composer install` 작업.

>[!NOTE]
>
>클라우드 인프라에서는 프로젝트의 목록에 품질 패치를 나열하여 설치할 수도 있습니다. `.magento.env.yaml` 파일. 여기에 설명된 예에서는 `vendor/bin/magento-patches apply` 명령입니다.

다음에 적용할 패치를 지정할 수 있습니다. `composer.json` 사용자 지정 작성기 구성 요소 패키지의 파일인 다음 다음 명령을 실행하는 플러그인 패키지를 만듭니다. `composer install` 작업.

요약하자면, 이 중앙 집중식 패치 적용 예제를 사용하려면 두 개의 사용자 지정 Composer 패키지를 생성해야 합니다.

- **구성 요소 패키지:** `centralized-patcher`

   - 품질 패치 목록 정의 `m2-hotfixes` 설치하려면
   - 를 필요로 합니다. `centralized-patcher-composer-plugin` 패키지: `vendor/bin/magento-patches apply` 다음 이후 명령 `composer install` 작업

- **플러그인 패키지:** `centralized-patcher-composer-plugin`

   - 다음을 정의합니다. `CentralizedPatcher` 에서 품질 패치 목록을 읽는 PHP 클래스 `centralized-patcher` 패키지
   - 실행 `vendor/bin/magento-patches apply` 다음 시간 이후에 품질 패치 목록을 설치하는 명령 `composer install` 작업

### `centralized-patcher`

작성기 구성 요소 패키지(`centralized-patcher`) 모든 품질 패치를 중앙에서 관리 `/m2-hotfixes` 를 모든 Adobe Commerce 설치에 적용할 수 있습니다.

구성 요소 패키지는 다음 작업을 수행해야 합니다.

- 의 내용을 복사합니다. `/m2-hotfixes` 배포 중 모든 설치에 디렉토리 추가.
- 설치할 품질 패치 목록을 정의합니다.
- 실행 `vendor/bin/magento-patches` 모든 설치에 동일한 품질 패치 목록을 설치하는 명령(사용) [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) plugin package as a dependency).

다음을 만들려면 `centralized-patcher` 구성 요소 패키지:

1. 만들기 `composer.json` 다음 내용이 포함된 파일:

   >[!NOTE]
   >
   >다음 `require` 다음 예제의 속성은 `require` 다음에 대한 종속성 [플러그인 패키지](#centralized-patcher-composer-plugin) 이 예제는 나중에 만들어야 합니다.

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

1. 만들기 `/m2-hotfixes` 패키지 내의 디렉터리 및 `map` 의 속성 `composer.json` 파일. 다음 `map` 속성에는 이 패키지에서 패치할 대상 프로젝트의 루트로 복사할 파일이 포함되어 있습니다.

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
   >다음 `centralized-patcher` 패키지는 의 콘텐츠를 복사합니다. `/m2-hotfixes` 대상 프로젝트의 m2-hotfixes 디렉터리로의 디렉터리 `composer install`.  클라우드 배포 스크립트가 다음에 m2-핫픽스를 적용함 `composer install`, 모든 핫픽스는 배포 메커니즘에 의해 설치됩니다.

1. 에 설치할 품질 패치 정의 `quality-patches` 특성.

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


다음 `quality-patches` 이전 코드 샘플의 속성에는 [전체 패치 목록](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 예를 들어,  이러한 품질 패치는 필요한 모든 프로젝트에 설치됩니다. `centralized-patcher` 를 사용한 패키지 `vendor/bin/magento-patches apply` 명령입니다.

테스트 목적으로 예제 패치(`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>자신의 패치를 `m2-hotfixes` Adobe Commerce 지원에서 직접 받는 패치와 함께 디렉토리입니다.

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

이 예제에서는 온-프레미스 메서드를 사용하여 품질 패치를 설치하므로 `vendor/bin/magento-patches apply` 다음 시간 이후에 명령 실행 `composer install` 작업. 이 플러그인은 다음 이후에 트리거됩니다. `composer install` 작업: `vendor/bin/magento-patches apply` 명령입니다.

다음을 만들려면 `centralized-patcher-compose-plugin` 구성 요소 패키지:

1. 만들기 `composer.json` 다음 내용이 포함된 파일:

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

1. PHP 파일을 만들고 `CentralizedPatcher` 클래스에서 품질 패치 목록을 읽는 클래스 [`centralized-patcher`](#centralized-patcher) 구성 요소 패키지 및 설치 간격 `composer install` 작업.

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
>다음을 참조하십시오. [코드-예](#code-examples) 이 예제에 설명된 두 가지 패키지를 실제로 확인합니다.


## 프로젝트별 패치로 수행할 작업

일부 패치가 특정 인스턴스에만 적용되는 반면, 모든 프로젝트에서 95%의 패치만 필요한 시나리오가 있을 수 있습니다. 패치를 적용하는 일반적인 방법은 여전히 작동합니다. 프로젝트별 패치를 `/m2-hotfixes` 프로젝트별 품질 패치 디렉토리 및 설치

이 방법을 사용하면 **금지** 에서 모든 패치를 커밋합니다. `/m2-hotfixes` 에서 프로젝트에 복사한 디렉토리 `centralized-patcher` 구성 요소 패키지. 을 추가하여 우발적 커밋을 방지할 수 있습니다. `/m2-hotfixes` (으)로 `.gitignore` 파일. 업데이트 후 `.gitignore` 파일, 모든 프로젝트별 `/m2-hotfixes` 을(를) 사용하여 추가해야 합니다. `git add –force` 명령입니다.

## 다른 Adobe Commerce 버전 실행

에서 올바른 종속성을 설정했는지 확인합니다. `centralized-patcher` 구성 요소 패키지. 예를 들어, 패키지의 특정 버전에 Adobe Commerce 2.4.5-p2가 필요할 수 있으며, 이 버전에서는 Adobe Commerce 2.4.5-p2와 호환되는 패치만 제공합니다. Adobe Commerce 2.4.4와 호환되는 이 패키지의 다른 버전이 있을 수 있습니다.

## 결과 이해

클라우드 인프라의 Adobe Commerce과 마찬가지로 이 문서에서는 배포 프로세스가 `composer install` 명령 및 아님 `composer update` 또는 `git pull` 서버에 새 코드를 배포합니다. 그런 다음 중앙 집중식 패치 설치의 흐름은 다음과 같습니다.

1. Composer 설치

   - -p1 또는 -p2 보안 및 기능 패치를 포함한 Adobe Commerce 설치
   - 중앙 집중식 결합 `/m2-hotfixes` 프로젝트별 패치 및 지원 `/m2-hotfixes` 및 지원 패치
   - 와 함께 설치된 모든 패치를 적용합니다. `cweagans/composer-patches` 작성기 패키지

1. 다음 이후 `composer install`

   - Composer 플러그인이 중앙 집중식 품질 패치를 설치합니다.

1. 배포

   - 필수 패치 및 프로젝트별 품질 패치는 다음을 기반으로 설치됩니다. `.magento.env.yaml` 파일(클라우드 인프라 프로젝트의 Adobe Commerce만 해당).
   - 사용자 정의 패치 및 지원 패치 `/m2-hotfixes` 디렉토리는 패치 이름별로 알파벳순으로 설치됩니다.

이렇게 하면 모든 설치에 대한 모든 패치를 중앙에서 관리할 수 있으며 Adobe Commerce 스토어의 보안 및 안정성을 더 잘 보장할 수 있습니다. 패치 상태를 확인하려면 다음 방법을 사용하십시오.

- [클라우드 인프라 프로젝트](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [온-프레미스 프로젝트](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## 코드 예

- [Magento Open Source의 중앙 집중식 패치](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [클라우드 인프라의 Adobe Commerce에 중앙 집중식 패치](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [중앙 집중식 Patcher Composer 플러그인](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [중앙 집중식 패치제 구성 요소](https://github.com/AntonEvers/centralized-patcher)
