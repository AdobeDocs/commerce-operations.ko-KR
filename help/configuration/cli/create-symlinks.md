---
title: LESS 파일에 대한 심볼릭 링크 만들기
description: LESS 파일에 대한 심볼릭 링크를 만드는 방법을 알아봅니다.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# LESS 파일에 대한 심볼릭 링크 만들기

{{file-system-owner}}

LESS 파일에 대한 심볼릭 링크를 만들려면:

명령 옵션:

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>개발 중에 이 명령은 의 LESS 파일에 대한 심볼릭 링크를 만듭니다. `var/view_preprocessed` 및 `pub/static` 개 폴더. 이 프로세스는 LESS 파일을 CSS 파일로 컴파일하지 않습니다.

다음 표에서는 이 명령의 매개 변수와 값에 대해 설명합니다.

| 매개 변수 | 값 | 필수? |
| --------- | ----- | --------- |
| `--type` | 소스 파일 유형: [간단히] (기본값: &quot;less&quot;)<br>현재 지원되는 파일 유형은 LESS뿐입니다. | 아니요 |
| `--locale` | 로케일 코드.<br>로케일 코드 목록을 표시하려면 다음을 입력합니다 `bin/magento info:language:list` | 아니요 |
| `--area` | 영역 (`adminhtml` 행정구역으로는, `frontend` 상점 앞에서). | 아니요 |
| `--theme` | 의 테마 이름 `<VendorName>/<theme-name>` 포맷. 예를 들어, `Magento/blank` 또는 `Magento/backend`. | 아니요 |
| `<file>` | CSS 확장명 없이 LESS로 변환할 CSS 파일의 공백으로 구분된 목록입니다. (기본값은 입니다. `css/styles-m css/styles-l`, adminhtml 유형 `css/styles css/styles-old`) | 아니요 |

예를 들어, 다음과 같은 프론트엔드 테마에 대해 LESS 파일을 만들려면 `VendorName/themeName` 다음에서 `en_US` 이름이 인 CSS 파일을 사용하는 로케일 `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`를 클릭하고 다음 명령을 입력합니다.

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

성공을 확인하기 위해 다음 메시지가 표시됩니다.

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

adminhtml에 대해 더 적은 파일을 생성하려면 다음을 수행합니다.

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
