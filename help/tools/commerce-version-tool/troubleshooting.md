---
title: '[!DNL Commerce Version Tool] 문제 해결'
description: ' [!DNL Commerce Version Tool] Composer 감지, 내부 시험 실행 검사, 레지스트리 캐시, JSON 출력 및 감사 로그 문제를 해결하는 방법을 알아봅니다.'
TQID: 'https://experienceleague.adobe.com/JwRSy7pfM89WoifYUzTVPhR-WrDIvj2A2B8SaEnmyWM'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 1222
ht-degree: 0%

---

# [!DNL Commerce Version Tool] 문제 해결

이 페이지에서는 작성기 감지, 레지스트리 로드, 내부 시험 실행 패치 감지, 출력 생성 및 감사 로깅과 관련된 일반적인 [!DNL Commerce Version Tool]&#x200B;([!DNL CVT]) 문제를 해결할 수 있습니다.

## 빠른 문제 해결 단계

[!DNL CVT] 도구가 필요한 패치 상태 보고서를 반환하지 않는 경우:

- 대상 설치에서 지원되는 Adobe Commerce 버전 및 에디션을 사용하는지 확인합니다.
- `composer.lock`이(가) 있고 검사할 환경과 일치하는지 확인하십시오.
- PHP와 시스템 `patch` 바이너리를 사용할 수 있는지 확인합니다.
- [!DNL CVT]이(가) 패치 레지스트리 파일을 읽을 수 있는지 확인하십시오.
- 출력에서 `warnings`, `missing_patches` 및 `unknown_patches`을(를) 검토합니다.
- 로그 파일이 만들어진 경우 실행에서 감사 요약을 `var/log/patch_status.log`을(를) 확인하십시오.

>[!TIP]
>
> 로그 파일은 패치를 분류할 수 없는 이유를 이해해야 할 때 가장 유용합니다. 알 수 없는 각 패치에 대해 로그는 오류 또는 청크 실패를 포함하여 순방향 및 역방향 드라이 런 시도의 원시 출력을 기록합니다.
>
> 레지스트리 또는 패치 파일을 가져오는 데 문제가 있는 경우 보고서의 경고 필드를 확인하십시오. 이러한 세부 사항은 로그에 표시되지 않습니다.

## 일반적인 문제 및 솔루션

### 기본 버전을 검색할 수 없음

[!DNL CVT] 도구가 Adobe Commerce 기본 버전을 찾을 수 없는 경우 다음 조건을 확인하십시오.

**확인:**

- `composer.lock`이(가) 없습니다.
- `patch-status` 명령이 Adobe Commerce 프로젝트 루트 외부에서 실행 중이므로(또는 `--root`이(가) 잘못된 경로를 가리킴) `composer.lock`을(를) 찾을 수 없습니다.
- `composer.lock`이(가) 존재하지만 올바른 JSON이 아니거나 읽을 수 없습니다.
- `composer.lock`에 인식할 수 있는 기본 패키지(`magento/product-enterprise-edition`, `magento/product-community-edition`, `magento/magento2-base`)가 없습니다.

**경고 메시지:**

`composer.lock`이(가) 있지만 읽을 수 없거나 구문 분석할 수 없거나 인식되는 기본 패키지가 들어 있지 않으면 도구에서 경고 출력 필드에 다음 문자열 중 하나를 표시합니다.

```shell-session
No recognized Commerce base package found in composer.lock
composer.lock exists but could not be read
composer.lock could not be parsed as JSON
```

>[!NOTE]
>
> `composer.lock`이(가) 완전히 누락된 경우 도구에서 `base_version: "unknown"`을(를) 보고하며 **경고 메시지가 전혀 표시되지 않습니다**. 항상 출력에서 `base_version`을(를) 직접 확인합니다. 이 문제를 찾기 위해 경고의 존재 여부에 의존하지 마십시오.

이전에 언급된 모든 조건은 도구가 기본 버전을 감지할 수 없음을 나타냅니다. 도구가 코드 `1`(으)로 종료되고 패치 검색이 수행되지 않습니다.

**작업:**

- [!DNL Adobe Commerce] 프로젝트 루트에서 `patch-status` 명령을 실행하거나 올바른 `--root`을(를) 전달합니다.
- `composer.lock`이(가) 현재 유효한 JSON인지 확인합니다.
- 지원되는 Adobe Commerce 버전을 사용하여 `composer.lock`에 인식된 기본 패키지 중 하나가 포함되어 있는지 확인하십시오.

### 설치된 버전에 적용되는 패치 없음

[!DNL CVT]에서 올바른 `base_version`을(를) 보고했지만 `applied_patches`, `missing_patches` 및 `unknown_patches`이(가) 비어 있으면 설치된 버전이 현재 패치 레지스트리에서 적용되지 않습니다.

**확인:**

- 설치된 [!DNL Adobe Commerce] 버전이 패치 레지스트리 파일에 표시되지 않습니다. 예를 들어, 레지스트리의 최신 항목보다 최신 릴리스입니다.

**경고 메시지:**

```shell-session
No patches found in registry for installed component versions (CE=2.4.7-p9)
```

이 경고는 &quot;기본 버전을 감지할 수 없음&quot;과 다릅니다. `base_version`이(가) 올바르고 도구가 `0`을(를) 종료했으며 레지스트리에 비교할 대상이 없습니다.

**작업:**

- 출력에서 `base_version`이(가) 예상한 대로인지 확인합니다.
- `registry_source`이(가) `remote` 또는 오래된 `cache`이(가) 아닌지 확인합니다.
- 버전이 이미 포함된 경우 Adobe Commerce 지원 센터에 문의하십시오.

### 패치 레지스트리를 가져올 수 없음

[!DNL CVT] 도구가 최신 패치 레지스트리 파일을 가져올 수 없는 경우 네트워크 및 캐시 설정을 확인하십시오.

**확인:**

- 네트워크를 사용할 수 없습니다.
- Adobe 패치 끝점 요청 시간이 초과되었습니다.
- `--no-cache`이(가) 사용되었으며 원격 레지스트리에 연결할 수 없습니다.
- `PATCH_REGISTRY_URL`이(가) 사용할 수 없는 레지스트리를 가리키거나 올바른 HTTPS URL이 아닙니다.
- [!DNL CVT] 도구가 최신 패치 레지스트리 파일을 가져올 수 없는 경우 네트워크 및 캐시 설정을 확인하십시오.

>[!NOTE]
>
>레지스트리 파일이 없거나 만료된 경우 도구는 원격 호스트에서 최신 레지스트리를 다운로드합니다.

**경고 메시지:**

이 도구는 이 시나리오의 경고 출력 필드에 다음 문자열을 내보냅니다.

```shell-session
Remote registry fetch failed (HTTP 403). Check PATCH_REGISTRY_URL (if set) and network connectivity.
Remote registry response was not valid JSON; ignoring.
Could not load remote registry. Using cached registry (3 hours old). CVE coverage may be incomplete.
Patch registry could not be loaded.
Could not fetch remote registry and --no-cache was set; aborting.
```

부실 캐시 메시지에 실제 사용 기간(시간)이 포함됩니다(예: `(3 hours old)`).

`patch registry could not be loaded` 및 `could not fetch remote registry` 경고는 패치 검색을 실행하지 않고 도구가 종료되었음을 나타냅니다.

**작업:**

- 네트워크 연결을 사용할 수 있을 때 `patch-status` 명령을 다시 실행하십시오.
- 검사에 부실 캐시 경고를 사용할 수 있는 경우 [!DNL CVT] 도구가 캐시된 레지스트리를 사용하도록 허용합니다.
- 새 원격 가져오기가 필요하지 않은 경우 `--no-cache`을(를) 제거하십시오.
- 레지스트리 캐시를 다시 사용하려면 [!DNL CVT] 도구가 `var/patch_metadata/`에 쓸 수 있는지 확인하십시오.

### 패치 차이를 가져오거나 확인할 수 없음

[!DNL CVT] 도구가 적용 가능한 패치를 하나 이상 테스트할 수 없는 경우 패치 비교 액세스를 확인하십시오.

**확인:**

- Adobe 패치 끝점에서 패치 비교를 다운로드할 수 없습니다.
- 인증된 패치 다운로드에 대한 필수 자격 증명이 누락되었거나 잘못되었습니다.
- `PATCH_DIFF_BASE_URL`이(가) 사용할 수 없는 patch-diff 소스를 가리키거나 올바른 HTTPS URL이 아닙니다.
- 캐시된 패치 차이가 없거나 읽을 수 없습니다.
- 다운로드한 패치 차이에 대해 SHA-256 확인이 실패합니다.
- [!DNL CVT] 도구는 `var/patch_metadata/.patch_diffs/`에 쓸 수 없습니다.

**경고 메시지:**

이 도구는 이 시나리오의 경고 출력 필드에 다음 문자열을 내보냅니다.

```shell-session
Patch 247p9-2026-05-001-EE requires authentication. Set credentials via COMPOSER_AUTH or auth.json.
Could not fetch patch 247p9-2026-05-001-EE (HTTP 401). Check credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch 247p9-2026-05-001-EE (HTTP 404).
Could not fetch or verify patch 247p9-2026-05-001-EE. Check network connectivity and credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch file for 247p9-2026-05-001-EE.
SHA-256 verification failed for patch 247p9-2026-05-001-EE; discarding download.
```

각 메시지의 패치 ID는 실제 레지스트리 항목 ID입니다(예: `247p9-2026-05-001-EE`). `SHA-256 verification failed`은(는) 새로 다운로드한 패치 파일이 필요한 체크섬과 일치하지 않음을 의미합니다. 이 도구는 캐싱 없이 삭제하고 이 실행에 대해 패치 `unknown`을(를) 분류합니다. 손상된 *local* 캐시 항목이 검색되었으며 경고 없이 동일한 실행 내에서 자동으로 다시 가져옵니다. 두 경우 모두 수동 캐시 정리가 필요하지 않습니다.

**작업:**

- 네트워크 연결을 확인하고 명령을 다시 시도하십시오.
- 인증된 패치 다운로드에 필요한 자격 증명이 구성되어 있는지 확인합니다.
- [!DNL CVT] 도구가 `var/patch_metadata/.patch_diffs/`에 쓸 수 있는지 확인하십시오.
- 패치가 알 수 없음으로 분류된 경우 경고 및 출력 세부 정보를 유지합니다.

### 누락되었거나 알 수 없는 패치가 보고됨

보고서에 예기치 않은 `missing_patches` 또는 `unknown_patches` 값이 포함된 경우 설치 및 출력 세부 정보를 검토하십시오.

**확인:**

- 월별 패치는 순서대로 적용되었습니다.
- Adobe Commerce B2B(business-to-business) 또는 Adobe Commerce 페이지 빌더와 같은 구성 요소별 패치가 없습니다.
- `composer.lock`에서 패치가 필요한 설치된 구성 요소 버전을 보고합니다.
- 패치 비교를 사용할 수 없거나 감지 결과에 결론이 존재합니다.

**경고 메시지:**

이 도구는 이 시나리오의 경고 출력 필드에 다음 문자열을 내보냅니다.

```shell-session
No file_name or sha256 for 247p9-2026-05-001-EE
Registry entry '247p9-2026-05-001-EE' requires unknown patch '247p9-2026-04-001-EE'; skipping.
descendant diffs unavailable for 247p9-2026-06-001-EE; dry-run for 247p9-2026-05-001-EE may be inaccurate
Failed to reverse-apply 247p9-2026-06-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
Failed to forward-apply prerequisite 247p9-2026-04-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
```

경고에 `may be inaccurate`이(가) 발생하면 시험 실행 검사가 계속 실행되지만 신뢰도가 저하됩니다. 패치는 `unknown_patches`일 필요는 없지만 `applied_patches` 또는 `missing_patches`에서 계속 분류할 수 있습니다.

특히 알 수 없는 패치의 경우 `var/log/patch_status.log`은(는) 일치하지 않는 파일과 청크를 나타내는 원시 패치 드라이 실행 출력(정방향 및 역방향)을 기록합니다.

&quot;패치를 찾을 수 없음&quot; 경고가 발생하면 [설치된 버전에 적용된 패치가 없음](#no-patches-apply-to-the-installed-version)을 참조하세요.

**작업:**

- `applied_patches`, `missing_patches` 및 `unknown_patches` 필드를 검토하십시오.
- 누락된 패치가 설치된 에디션 및 구성 요소에 적용되는지 확인합니다.
- 결과를 관련 보안 패치 릴리스 정보와 비교합니다.
- 검사된 코드베이스가 보고할 배포된 환경과 일치하는지 확인합니다.
- 알 수 없는 상태가 교정 계획을 차단하는 경우 Adobe Commerce 지원 센터에 문의하십시오.

### 출력이 생성되지 않음

[!DNL CVT] 도구가 완료되었지만 필요한 JSON 또는 CSV 출력이 누락된 경우 명령 구문 및 터미널 출력을 확인하십시오.

**작업:**

- CSV 출력이 필요하지 않은 경우 기본 JSON 출력을 사용합니다.
- CSV 출력을 생성하려면 `--format=csv`을(를) 사용하십시오.
- 명령 출력이 리디렉션되지 않았는지 또는 [!DNL CVT] 도구를 실행하는 셸, 스크립트 또는 스캐너에 의해 삭제되지 않았는지 확인합니다.
- `patch-status:`개의 오류 메시지에 대해 `stderr`을(를) 확인하십시오.
- 출력을 파일로 리디렉션하는 경우(예: `patch-status > report.json`) 셸에 해당 대상에 대한 쓰기 권한이 있는지 확인하십시오. 이 도구는 `stdout`에만 씁니다.
- [!DNL CVT] 도구가 `var/log/patch_status.log`에 쓸 수 있는지 확인하십시오.
- 문제 해결을 위해 명령 및 캡처 터미널 출력을 다시 실행합니다.

## 도움말 보기

Adobe Commerce 지원에 문의할 때 문제를 조사하는 데 필요한 세부 정보만 제공하십시오.

포함:

- Adobe Commerce 버전 및 에디션
- [!DNL CVT] 도구 버전
- [!DNL CVT] 도구 출력의 레지스트리 원본
- 관련 `applied_patches`, `missing_patches` 및 `unknown_patches` 값
- 관련 경고
- 오류 메시지 또는 명령 출력

공유 로그 또는 첨부 파일에 비밀, 자격 증명, 비공개 키 또는 관련 없는 고객 데이터를 포함하지 마십시오.

## 관련 항목

- [소개](intro.md)
- [패치 상태 보고서 생성](generate-report.md)
- [릴리스 정보](release-notes.md)
