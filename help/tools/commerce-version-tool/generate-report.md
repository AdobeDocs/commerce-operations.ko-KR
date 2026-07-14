---
title: 패치 상태 보고서 생성
description: ' [!DNL Commerce Version Tool] 을(를) 사용하여 JSON 또는 CSV 형식의 Adobe Commerce 패치 상태 보고서를 생성하는 방법에 대해 알아봅니다.'
TQID: 'https://experienceleague.adobe.com/-lC-20YMpbTM3tTZjbBO5zD5gb9n7cRah5Ycy8wQoyw'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: cb0391ae368b53a795535f3adb636628a339b963
workflow-type: tm+mt
source-wordcount: 590
ht-degree: 2%

---

# 패치 상태 보고서 생성

[!DNL Commerce Version Tool]&#x200B;([!DNL CVT])을(를) 사용하여 Adobe Commerce 설치에 대한 패치 상태 보고서를 생성합니다. 이 보고서는 적용, 누락 및 알 수 없는 월별 보안 패치를 식별하며 기본적으로 JSON 출력을 반환합니다.

## 사전 요구 사항

[!DNL CVT]을(를) 실행하기 전에 다음을 확인하십시오.

- Target 설치에서는 지원되는 Adobe Commerce 버전 및 에디션을 사용합니다.
- `composer.lock`이(가) 있으며 검사할 환경과 일치합니다.
- PHP 및 시스템 `patch` 바이너리를 사용할 수 있습니다.
- 명령을 실행하는 환경에서 프로젝트 파일을 읽을 수 있습니다.
- 캐시 파일 및 감사 로그 항목을 원하는 경우 도구는 `var/patch_metadata/` 및 `var/log/`에 쓸 수 있습니다.
- 자격 제어된 패치가 설치에 적용되는 경우 `COMPOSER_AUTH` 또는 `auth.json`을(를) 통해 자격 증명을 사용할 수 있습니다.

[!DNL CVT] 도구는 `COMPOSER_AUTH`, Adobe Commerce 프로젝트 `auth.json` 및 전역 작성기 `auth.json`에서 자격 제어된 패치 자격 증명을 확인합니다.

## 보고서 생성

Adobe Commerce 프로젝트 루트에서 다음을 실행합니다.

```bash
php vendor/bin/patch-status
```

다른 Adobe Commerce 설치를 확인하려면 `--root` 옵션을 사용합니다.

```bash
php vendor/bin/patch-status --root=/path/to/commerce
```

## 명령 옵션

JSON은 기본 출력 형식입니다. CSV 출력은 스캐너, 대시보드 및 규정 준수 보고서에 대해 지원됩니다.

| 옵션 | 설명 |
| --- | --- |
| `--root=PATH` | Adobe Commerce 설치 루트에 대한 경로를 지정합니다. 기본값은 현재 디렉터리입니다. |
| `--format=json\|csv` | 출력 형식을 설정합니다. 기본값은 `json`입니다. |
| `--no-cache` | 레지스트리 및 패치 비교 캐시를 무시하고 새 원격 페치를 강제로 수행하고, 원격 레지스트리를 사용할 수 없는 경우 오류가 발생하여 종료합니다. |
| `--version`, `-V` | 도구 버전을 인쇄합니다. |
| `--help`, `-h` | 도움말 메시지를 인쇄합니다. |

{style="table-layout:auto"}

## JSON 및 CSV 출력 검토

다음 샘플은 기본 JSON 출력을 보여 줍니다.

```bash
php vendor/bin/patch-status
```

```json
{
  "base_version": "2.4.7-p9",
  "installed_components": {
    "CE": "2.4.7-p9",
    "EE": "2.4.7-p9",
    "B2B": "1.5.2-p5"
  },
  "applied_patches": [
    "247p9-2026-05-001-CE",
    "247p9-2026-05-001-EE"
  ],
  "missing_patches": [
    "247p9-2026-06-001-CE",
    "247p9-2026-06-001-EE"
  ],
  "unknown_patches": [],
  "vulnerability_status": {
    "CVE-2026-12354": { "status": "PROTECTED" },
    "CVE-2026-67890": { "status": "VULNERABLE" }
  },
  "registry_source": "remote",
  "warnings": []
}
```

CSV 출력을 생성하려면 `--format=csv` 옵션을 사용하십시오.

```bash
php vendor/bin/patch-status --format=csv
```

CSV 출력은 CVE당 하나의 행을 생성하며 스프레드시트, 스캐너, 대시보드 및 규정 준수 툴링에 적합합니다.

## 보고서 결과 이해

보안 상태를 청구하기 전에 누락 및 알 수 없는 패치를 검토하십시오.

### 패치 상태 값

패치 상태 보고서는 패치 결과를 다음 값으로 그룹화합니다.

| 패치 상태 | 의미 |
| --- | --- |
| 적용됨 | [!DNL CVT] 도구는 Adobe Commerce 코드베이스에서 월별 보안 패치를 검색합니다. |
| 누락 | 이 패치는 설치된 Adobe Commerce 버전 또는 구성 요소에 적용되지만 [!DNL CVT] 도구에서 이를 감지하지 못합니다. |
| 알 수 없음 | 사용 가능한 레지스트리, 패치 비교 또는 검색 결과에서 패치 상태를 확인할 수 없습니다. |

{style="table-layout:auto"}

### CVE 상태 값

JSON 출력은 CVE 상태 값을 대문자로 보고합니다.

| CVE 상태 | 의미 |
| --- | --- |
| `PROTECTED` | 적용 가능한 패치는 CVE 또는 구성 요소에 대해 감지됩니다. |
| `VULNERABLE` | CVE 또는 구성 요소에 적용할 수 있는 패치가 없습니다. |
| `UNKNOWN` | [!DNL CVT] 도구는 사용 가능한 레지스트리 및 검색 데이터에서 CVE 상태를 확인할 수 없습니다. |
| `NOT_APPLICABLE` | CVE는 Adobe Commerce B2B(business-to-business), Adobe Commerce 페이지 빌더 또는 Adobe Commerce 인벤토리와 같이 설치되지 않은 구성 요소에 적용됩니다. |

{style="table-layout:auto"}

### 주요 출력 필드

보고서에는 다음 정보가 포함될 수 있습니다.

- **기본 Adobe Commerce 버전** - `composer.lock`에서 설치된 기본 버전이 검색되었습니다.
- **레지스트리 원본** - 패치 메타데이터가 `remote`, `cache` 또는 `stale_cache`에서 제공되었는지 여부입니다.
- **설치된 구성 요소** - `composer.lock`에서 Adobe Commerce 패키지 영역을 검색했습니다.
- **적용된 패치** - Adobe Commerce 코드베이스에서 검색된 월별 보안 패치입니다.
- **패치가 없음** - 적용되지만 검색되지 않는 월별 보안 패치입니다.
- **알 수 없는 패치** - [!DNL CVT] 도구에서 분류할 수 없는 패치입니다.
- **CVE별 취약성 상태** - CVE 범위가 보호되거나 취약하거나 적용할 수 없거나 알 수 없는 상태로 매핑되었습니다.
- **경고** - 보고서의 안정성 또는 완전성에 영향을 줄 수 있는 조건입니다.

## 패치 레지스트리 및 캐시

패치 레지스트리 파일에는 [!DNL CVT] 도구가 설치된 버전에 적용할 패치를 결정하는 데 사용하는 패치 메타데이터가 포함되어 있습니다. 이 도구는 사용 가능한 경우 새 레지스트리 캐시를 사용하고 필요한 경우 원격 레지스트리를 가져오며 네트워크를 사용할 수 없는 경우 경고와 함께 오래된 캐시를 사용할 수 있습니다. 새 원격 가져오기가 필요한 경우에만 `--no-cache`을(를) 사용하십시오.

## 관련 항목

- [소개](intro.md)
- [문제 해결](troubleshooting.md)
- [릴리스 정보](release-notes.md)
