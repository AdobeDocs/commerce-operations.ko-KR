---
title: LESS 파일에 대한 symlink 만들기
description: LESS 파일에 대한 symlink를 만드는 방법을 알아봅니다.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# LESS 파일에 대한 symlink 만들기

{{file-system-owner}}

LESS 파일에 대한 symlink를 생성하려면

명령 옵션:

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>개발 중에 이 명령은 `var/view_preprocessed` 및 `pub/static` 폴더. 이 프로세스는 LESS 파일을 CSS 파일로 컴파일하지 않습니다.

다음 표에서는 이 명령의 매개 변수와 값에 대해 설명합니다.

| 매개 변수 | 값 | 필수? |
| --------- | ----- | --------- |
| `--type` | 소스 파일 유형: [less] (기본값: &quot;less&quot;)<br>현재 LESS만 지원되는 파일 유형입니다. | 아니요 |
| `--locale` | 로케일 코드.<br>로케일 코드 목록을 표시하려면 다음을 입력합니다 `bin/magento info:language:list` | 아니요 |
| `--area` | 영역 (`adminhtml` 행정구역에 대해서는 `frontend` (상점) | 아니요 |
| `--theme` | 의 테마 이름 `<VendorName>/<theme-name>` 형식 지정 예, `Magento/blank` 또는 `Magento/backend`. | 아니요 |
| `<file>` | CSS 확장 없이 LESS로 변환할 공백으로 구분된 CSS 파일 목록입니다. 기본값은 입니다. `css/styles-m css/styles-l`, adminhtml 유형의 경우 `css/styles css/styles-old`) | 아니요 |

예를 들어, `VendorName/themeName` 에서 `en_US` CSS 파일을 사용하는 로케일 `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`를 입력하여 다음 명령을 입력합니다.

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

다음 메시지가 표시되어 성공을 확인합니다.

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

관리자용 LESS 파일을 만들려면 다음을 수행하십시오.

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
