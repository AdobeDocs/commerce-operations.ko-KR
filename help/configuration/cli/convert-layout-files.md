---
title: 레이아웃 파일 변환
description: Adobe Commerce 명령줄 도구를 사용하여 XML 레이아웃 파일을 변환하는 방법을 알아봅니다. XSLT 스타일시트 업데이트 및 파일 변환 프로세스를 살펴봅니다.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%
---
# XML 레이아웃 파일 변환

{{file-system-owner}}

해당 XSLT(Extensible Stylesheet Language Transformations) 스타일시트를 업데이트하는 경우 이 명령을 사용하여 레이아웃 XML 파일을 업데이트합니다.

- [레이아웃 지침](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions)
- [레이아웃 파일 유형](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-files-types-and-conventions)

명령 옵션:

```shell
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

위치:

- `{xml file}`—변환할 레이아웃 XML 파일의 전체 경로 및 파일 이름입니다(필수).
- `{xslt stylesheet}` - 변환에 사용할 XSLT 스타일시트 파일의 전체 경로 및 파일 이름입니다(필수).
- `-o|--overwrite`—기존 XML 파일을 덮어쓰려면 이 옵션을 포함합니다.
