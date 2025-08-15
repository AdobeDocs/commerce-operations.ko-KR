---
title: 사용
description: ' [!DNL Quality Patches Tool]을(를) 사용하는 방법을 알아봅니다.'
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 0%

---

# 사용

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches)은(는) Adobe 및 Magento Open Source 커뮤니티에서 개발한 개별 패치를 제공합니다. 설치된 Adobe Commerce 버전에 사용할 수 있는 모든 개별 패치에 대한 일반 정보를 적용, 되돌리기 및 볼 수 있습니다. 누가 패치를 개발했는지에 관계없이 Adobe Commerce 프로젝트에 패치를 적용할 수 있습니다. 예를 들어 커뮤니티에서 개발한 패치를 Adobe Commerce 프로젝트에 적용할 수 있습니다.

이 [기술 비디오](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en)를 시청하고 Adobe Commerce용 품질 패치 도구를 사용하는 방법을 알아보십시오.

>[!INFO]
>
>Adobe Commerce 프로젝트에 패치를 적용하는 방법은 [개별 패치 적용](#apply-individual-patches)을 참조하십시오. 릴리스된 패치의 전체 목록을 검토하려면 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하십시오.

>[!WARNING]
>
>코드의 복잡성을 높이고 새 버전으로 업그레이드하는 것을 더 어렵게 만들기 때문에 많은 수의 패치를 적용하려면 [!DNL Quality Patches Tool]을(를) 사용하지 않는 것이 좋습니다.

## 설치

>[!INFO]
>
>아직 설치되지 않은 경우 [[!DNL Git]을(를) 설치하기 전에 ](https://github.com/git-guides/install-git) [ 또는 ](https://man7.org/linux/man-pages/man1/patch.1.html)패치[!DNL Quality Patches Tool]을(를) 설치해야 합니다. `magento/quality-patches` 파일에 `composer.json` 작성기 패키지 추가:

```bash
composer require magento/quality-patches
```

## 개별 패치 보기

Adobe Commerce 버전에 사용할 수 있는 개별 패치 목록을 보려면 다음을 수행합니다.

```bash
./vendor/bin/magento-patches status
```

다음과 유사한 출력이 표시됩니다.

| Id | 제목 | 유형 | 상태 | 세부 사항 |
|--- |--- |--- |--- |--- |
| 매그클라우드 | 배포 중 FPC를 사용할 수 없습니다. | 선택 사항 | 적용되지 않음 | 영향을 받는 구성 요소:<br> - magento/module-page-cache |
| MCLOUD-5650 | 파일에서 읽은 후 배포 구성 보류 | 선택 사항 | 적용되지 않음 | 영향을 받는 구성 요소:<br> - magento/framework |
| MCLOUD-5684 | 페이지 매김이 작동하지 않음 - product_list_limit=all | 선택 사항 | 적용되지 않음 | 영향을 받는 구성 요소: - magento/module-elasticsearch |
| MCLOUD-5837 | 로드 밸런서 문제 해결 | 더 이상 사용되지 않음 | 적용됨 | 권장 교체: MC-1 <br> 영향을 받는 구성 요소: - magento/framework |
| BUNDLE-2554 | 결제 정보 버그 설정 | 선택 사항 | 적용되지 않음 | 영향을 받는 구성 요소: <br>- amzn/amazon-pay-module |
| - | 문제 1 수정 | 선택 사항 | 적용됨 | 영향을 받는 구성 요소: <br> - magento/module-cms |
| - | 문제 2 수정 | 선택 사항 | 적용되지 않음 | 영향을 받는 구성 요소: <br> - magento/module-cms |
| - | 문제 3 수정 | 선택 사항 | 적용되지 않음 | 필수 패치:<br> - MC-2 <br>영향을 받는 구성 요소: <br>- magento/module-cms |
| MC-3-V2 | 문제 3에 대한 수정 사항이 업데이트되어 MC-3 패치를 대체합니다. | 선택 사항 | 해당 사항 없음 | 영향을 받는 구성 요소: <br>- magento/module-cms |

Adobe Commerce 2.3.5.

상태 테이블에는 다음이 포함됩니다.

- **유형**:
   - `Optional` — [!DNL Quality Patches Tool] 및 [Commerce on Cloud Infrastructure Guide > Apply patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 패키지의 모든 패치는 Adobe Commerce 설치에 선택 사항입니다.
   - `Deprecated` — Adobe에서 개별 패치를 더 이상 사용하지 않습니다. 패치를 적용한 경우에는 되돌리는 것이 좋습니다. 되돌리기 작업도 상태 테이블에서 패치를 제거합니다.

- **상태**:
   - `Applied` — 패치가 적용되었습니다.
   - `Not applied` — 패치가 적용되지 않았습니다.
   - `N/A` — 충돌로 인해 패치 상태를 정의할 수 없습니다.

- **세부 정보**:
   - `Affected components` — 영향을 받는 모듈 목록입니다.
   - `Required patches` — 표시된 패치가 제대로 작동하기 위해 적용해야 하는 패치 목록(종속성).
   - `Recommended replacement` — 더 이상 사용되지 않는 패치의 권장 대체 패치입니다.

>[!INFO]
>
>새 버전의 Adobe Commerce으로 업그레이드한 후 새 버전에 패치가 포함되지 않은 경우 패치를 다시 적용해야 합니다. [업그레이드 후 패치 다시 적용](#re-apply-patches-after-an-upgrade)을 참조하십시오.

## 개별 패치 적용 {#apply-individual-patches}

>[!WARNING]
>
>프로덕션에 배포하기 전에 스테이징 또는 개발 환경에서 모든 패치를 테스트하는 것이 좋습니다. 또한 패치를 적용하기 전에 데이터를 백업하는 것이 좋습니다. [파일 시스템, 미디어 및 데이터베이스 백업 및 롤백](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html)을 참조하십시오.

단일 패치를 적용하려면 다음 명령을 실행합니다. 여기서 `MAGETWO-XXXX`은(는) 상태 표에 지정된 패치 ID입니다.

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

각 추가 패치 ID를 공백으로 구분하여 여러 패치를 동시에 적용할 수도 있습니다.

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Adobe Commerce 애플리케이션에서 변경 사항을 보려면 패치를 적용한 후 캐시를 정리해야 합니다.

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>적용된 패치 목록을 별도의 위치에 유지하는 것이 좋습니다. 새 버전의 Adobe Commerce으로 업그레이드한 후 일부를 다시 적용해야 할 수 있습니다. [업그레이드 후 패치 다시 적용](#re-apply-patches-after-an-upgrade)을 참조하십시오.

## 개별 패치 되돌리기

>[!WARNING]
>
>프로덕션에 배포하기 전에 스테이징 또는 개발 환경에서 모든 패치를 테스트하는 것이 좋습니다. 또한 패치를 적용하기 전에 데이터를 백업하는 것이 좋습니다. [파일 시스템, 미디어 및 데이터베이스 백업 및 롤백](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html)을 참조하십시오.

단일 패치를 되돌리려면 다음 명령을 실행합니다. 여기서 `MAGETWO-XXXX`은(는) 상태 표에 지정된 패치 ID입니다.

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

또한 공백으로 각 추가 패치 ID를 분리하여 여러 패치를 동시에 되돌릴 수 있습니다.

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

적용된 모든 패치를 되돌리려면 다음을 수행합니다.

```bash
./vendor/bin/magento-patches revert --all
```

Adobe Commerce 애플리케이션에서 변경 사항을 보려면 패치를 되돌린 후 캐시를 정리해야 합니다.

```bash
./bin/magento cache:clean
```

## 업데이트 받기

Adobe Commerce은 정기적으로 새로운 개별 패치를 릴리스합니다. 새 개별 패치를 가져오려면 [!DNL Quality Patches Tool]을(를) 업데이트해야 합니다.

```bash
composer update magento/quality-patches
```

추가된 패치를 확인합니다.

>[!TIP]
>
>새 패치 추가가 테이블 하단에 표시됩니다.

```bash
./vendor/bin/magento-patches status
```

## 업그레이드 후 패치 재적용 {#re-apply-patches-after-an-upgrade}

새 버전의 Adobe Commerce으로 업그레이드할 때 패치가 새 버전에 포함되지 않은 경우 패치를 다시 적용해야 합니다.

패치를 다시 적용하려면 다음을 수행합니다.

1. [!DNL Quality Patches Tool] 업데이트:

   ```bash
   composer update magento/quality-patches.
   ```

1. [개별 패치 적용](#apply-individual-patches)에서 권장된 이전에 적용된 패치 목록을 엽니다.

1. 패치를 적용합니다.

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   패치를 한 번에 하나씩 적용하는 것이 가장 좋습니다.

1. 캐시를 정리합니다.

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >`status` 명령을 실행하면 새 버전에 포함된 패치가 사용 가능한 패치 테이블에 더 이상 표시되지 않습니다.

## 로깅

[!DNL Quality Patches Tool]은(는) `<Magento_root>/var/log/patch.log` 파일에 모든 작업을 기록합니다.
