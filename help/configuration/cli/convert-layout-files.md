---
title: 레이아웃 파일 변환
description: XML 레이아웃 파일을 변환합니다.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# XML 레이아웃 파일 변환

{{file-system-owner}}

해당 XSLT(Extensible Stylesheet Language Transformations) 스타일시트를 업데이트할 경우 이 명령을 사용하여 레이아웃 XML 파일을 업데이트합니다.

- [레이아웃 지침](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [레이아웃 파일 형식](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

명령 옵션:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

위치:

- `{xml file}`- 변환할 레이아웃 XML 파일의 전체 경로 및 파일 이름입니다(필수).
- `{xslt stylesheet}`- 변환에 사용할 XSLT 스타일시트 파일의 전체 경로 및 파일 이름입니다(필수).
- `-o|--overwrite`- 기존 XML 파일을 덮어쓰려면 이 옵션을 포함합니다
