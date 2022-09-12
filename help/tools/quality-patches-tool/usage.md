---
title: 사용
description: 사용 방법을 알아봅니다 [!DNL Quality Patches Tool].
source-git-commit: 356ee307e0199d70c0e391e0d903e8f2e1600e63
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 사용

다음 [품질 패치 도구](https://github.com/magento/quality-patches) 는 Adobe 및 Magento Open Source 커뮤니티에서 개발한 개별 패치를 제공합니다. 설치된 Adobe Commerce 또는 Magento Open Source 버전에서 사용할 수 있는 모든 개별 패치에 대한 일반 정보를 적용, 되돌리고 볼 수 있습니다. 패치를 개발한 사람에 관계없이 Adobe Commerce 및 Magento Open Source 프로젝트에 패치를 적용할 수 있습니다. 예를 들어 커뮤니티에서 개발한 패치를 Adobe Commerce 프로젝트에 적용할 수 있습니다.


>[!INFO]
> 
>자세한 내용은 [개별 패치 적용](#apply-individual-patches) Adobe Commerce 또는 Magento Open Source 프로젝트에 패치를 적용하는 방법에 대한 지침을 참조하십시오. 자세한 내용은 [사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 릴리즈된 패치 전체 목록 검토

>[!WARNING]
>
>을 사용하지 않는 것이 좋습니다 [!DNL Quality Patches Tool] 많은 패치를 적용하는 것은 코드의 복잡성을 높이고 새 버전으로 업그레이드하는 것을 더 어렵게 하기 때문에

## 설치

>[!INFO]
> 
>아직 설치되지 않은 경우 설치해야 합니다 [Git](https://github.com/git-guides/install-git) 또는 [Patch](https://man7.org/linux/man-pages/man1/patch.1.html) 설치하기 전에 [!DNL Quality Patches Tool]. 추가 `magento/quality-patches` 대상 패키지 작성기 `composer.json` 파일:

```bash
composer require magento/quality-patches
```

## 개별 패치 보기

Adobe Commerce 또는 Magento Open Source 버전에 사용할 수 있는 개별 패치 목록을 보려면 다음을 수행하십시오.

```bash
./vendor/bin/magento-patches status
```

다음과 유사한 출력이 표시됩니다.

| Id | 제목 | 유형 | 상태 | 세부 사항 |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | 배포 중 FPC를 사용하지 않도록 설정하는 중 | 선택 사항입니다 | 적용되지 않음 | 영향을 받는 구성 요소:<br> - magento/module-page-cache |
| MCLOUD-5650 | 파일에서 읽은 후 배포 구성을 보류합니다. | 선택 사항입니다 | 적용되지 않음 | 영향을 받는 구성 요소:<br> - magento/framework |
| MCLOUD-5684 | 페이지 매김이 작동하지 않음 - product_list_limit=all | 선택 사항입니다 | 적용되지 않음 | 영향을 받는 구성 요소: - magento/module-elasticsearch |
| MCLOUD-5837 | 로드 밸런서 문제 해결 | 사용되지 않음 | 적용됨 | 권장 교체: MC-1 <br> 영향을 받는 구성 요소: - magento/framework |
| BUNDLE-2554 | 결제 정보 버그 설정 | 선택 사항입니다 | 적용되지 않음 | 영향을 받는 구성 요소: <br>- amzn/amazon-pay-module |
| MC-1 | 수정 문제 1 | 선택 사항입니다 | 적용됨 | 영향을 받는 구성 요소: <br> - magento/module-cms |
| MC-2 | 수정 문제 2 | 선택 사항입니다 | 적용되지 않음 | 영향을 받는 구성 요소: <br> - magento/module-cms |
| MC-3 | 수정 사항 3 | 선택 사항입니다 | 적용되지 않음 | 필요한 패치:<br> - MC-2 <br>영향을 받는 구성 요소: <br>- magento/module-cms |
| MC-3-V2 | MC-3 패치를 대체하는 문제 3에 대한 업데이트 수정 | 선택 사항입니다 | 해당 없음 | 영향을 받는 구성 요소:  <br>- magento/module-cms |

Adobe Commerce 2.3.5.

상태 테이블에는 다음이 포함됩니다.

- **유형**:
   - `Optional` — [!DNL Quality Patches Tool] 그리고 [클라우드 패치](https://devdocs.magento.com/cloud/project/project-patch.html) 패키지는 Adobe Commerce 및 Magento Open Source 설치에 선택 사항입니다.
   - `Deprecated` — Adobe은 개별 패치를 더 이상 사용하지 않습니다. 패치를 적용한 경우에는 되돌릴 것을 권장합니다. 되돌리기 작업은 상태 테이블에서 패치를 제거합니다.

- **상태**:
   - `Applied` — 패치가 적용되었습니다.
   - `Not applied` — 패치가 적용되지 않았습니다.
   - `N/A` — 충돌로 인해 패치 상태를 정의할 수 없습니다.

- **세부 사항**:
   - `Affected components` — 영향을 받는 모듈 목록입니다.
   - `Required patches` — 표시된 패치가 제대로 작동하려면 적용해야 하는 패치 목록(종속성)입니다.
   - `Recommended replacement` — 사용되지 않는 패치에 대해 권장되는 대체 패치입니다.

>[!INFO]
> 
>새 버전의 Adobe Commerce 또는 Magento Open Source으로 업그레이드한 후 새 버전에 패치가 포함되지 않은 경우 패치를 다시 적용해야 합니다. 자세한 내용은 [업그레이드 후 패치 다시 적용](#re-apply-patches-after-an-upgrade).

## 개별 패치 적용 {#apply-individual-patches}

>[!WARNING]
>
>프로덕션에 배포하기 전에 스테이징 또는 개발 환경에서 모든 패치를 테스트하는 것이 좋습니다. 패치를 적용하기 전에 데이터를 백업하는 것이 좋습니다. 자세한 내용은 [파일 시스템 백업 및 롤백](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

단일 패치를 적용하려면 다음 명령을 `MAGETWO-XXXX` 상태 테이블에 지정된 패치 ID입니다.

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

공간을 사용하여 각 추가 패치 ID를 구분하여 동시에 여러 패치를 적용할 수도 있습니다.

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Adobe Commerce 응용 프로그램에서 변경 사항을 보려면 패치를 적용한 후 캐시를 정리해야 합니다.

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>적용된 패치 목록을 별도의 위치에 유지하는 것이 좋습니다. 새 버전의 Adobe Commerce 또는 Magento Open Source으로 업그레이드한 후 해당 구성 요소 중 일부를 다시 적용해야 할 수 있습니다. 자세한 내용은 [업그레이드 후 패치 다시 적용](#re-apply-patches-after-an-upgrade).

## 개별 패치 되돌리기

>[!WARNING]
>
>프로덕션에 배포하기 전에 스테이징 또는 개발 환경에서 모든 패치를 테스트하는 것이 좋습니다. 패치를 적용하기 전에 데이터를 백업하는 것이 좋습니다. 자세한 내용은 [파일 시스템 백업 및 롤백](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

단일 패치를 되돌리려면 다음 명령을 `MAGETWO-XXXX` 상태 테이블에 지정된 패치 ID입니다.

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

또한 공간을 사용하여 각 추가 패치 ID를 분리하여 동시에 여러 패치를 되돌릴 수 있습니다.

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

적용된 모든 패치를 되돌리는 방법은 다음과 같습니다.

```bash
./vendor/bin/magento-patches revert --all
```

Adobe Commerce 응용 프로그램에서 변경 사항을 보려면 패치를 복원한 후 캐시를 정리해야 합니다.

```bash
./bin/magento cache:clean
```

## 업데이트 가져오기

Adobe Commerce은 정기적으로 새로운 개별 패치를 출시합니다. 를 업데이트해야 합니다. [!DNL Quality Patches Tool] 새 개별 패치를 받으려면 다음을 수행합니다.

```bash
composer update magento/quality-patches
```

추가된 패치를 확인합니다.

>[!TIP]
>
>새 추가 패치가 테이블 하단에 표시됩니다.

```bash
./vendor/bin/magento-patches status
```

## 업그레이드 후 패치 다시 적용 {#re-apply-patches-after-an-upgrade}

새 버전의 Adobe Commerce 또는 Magento Open Source으로 업그레이드할 때 패치가 새 버전에 포함되지 않은 경우 패치를 다시 적용해야 합니다.

패치를 다시 적용하려면

1. 업데이트 [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. 이전에 적용된 패치 목록을 열고 [개별 패치 적용](#apply-individual-patches).

1. 패치 적용:

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   패치를 한 번에 하나씩 적용하는 것이 가장 좋습니다.

1. 캐시 정리:

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >를 실행할 때 `status` 명령을 실행하면 새 버전에 포함된 패치는 사용 가능한 패치 테이블에 더 이상 표시되지 않습니다.

## 로깅

다음 [!DNL Quality Patches Tool] 에서 모든 작업을 기록합니다. `<Magento_root>/var/log/patch.log` 파일.
