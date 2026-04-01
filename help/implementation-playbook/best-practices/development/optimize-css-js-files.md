---
title: CSS 및 JS 리소스 파일 최적화
description: 관리자 또는 명령줄에서 Adobe Commerce 프로젝트에 대한 CSS 및 JavaScript(JS) 파일을 병합하고 축소하는 방법을 알아봅니다.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: a08560eb307638a36fdc52224c41bdf2c5d47763
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# 리소스 파일 최적화

보다 반응형 Commerce 사이트의 경우 CSS 및 JavaScript(JS) 리소스 파일을 최적화하고 렌더링 차단 리소스를 제거합니다.

- **CSS 및 JS 파일 최적화** - Adobe Commerce에서 파일을 축소하고 번들로 구성하도록 구성하여 CSS 및 JavaScript(JS) 파일을 로드하는 데 필요한 시간을 줄입니다.
- **렌더링 차단 리소스 제거** - 중요한 JS 및 CSS 기능을 인라인으로 제공하고 중요하지 않은 모든 JS/CSS 스타일을 지연하는 것이 좋습니다. 자세한 내용은 [렌더링 차단 리소스 제거](https://web.dev/render-blocking-resources/)를 참조하십시오.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전, 2.3 이상](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## CSS 파일 병합 또는 축소

별도의 파일을 단일 파일로 병합, 축소 및 번들링하여 CSS 및 JavaScript(JS) 파일을 로드하는 데 걸리는 시간을 줄일 수 있습니다.

>[!IMPORTANT]
>
>클라우드 인프라의 Adobe Commerce은 항상 프로덕션 모드에서 실행되며, 달리 설정할 수 없으므로 명령줄 메서드를 사용하여 병합, 축소 및 번들링을 활성화해야 합니다.

배포에서 HTTP/2를 사용하는 경우 파일을 병합하거나 번들로 묶지 마십시오. HTTP/2는 정적 파일을 비동기식으로 다운로드합니다. 브라우저는 파일 컨텐츠를 처리하기 전에 병합된 파일 전체를 다운로드해야 합니다.

### 관리자 사용

CSS 병합 또는 축소를 활성화하려면 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL CSS Settings]**(으)로 이동하십시오.

### 명령줄 사용

클라우드 인프라에서 Adobe Commerce의 CSS 병합을 활성화하려면 다음을 수행하십시오.

1. 이 명령을 로컬에서 실행합니다.

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. `app/etc/config.php` 파일에 변경 내용을 커밋하고 다시 배포합니다.

클라우드 인프라에서 Adobe Commerce의 CSS 축소를 활성화하려면:

1. 이 명령을 로컬에서 실행합니다.

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. `app/etc/config.php` 파일에 변경 내용을 커밋하고 다시 배포합니다.

## JS 파일 축소

### [!UICONTROL Admin] 사용 중

[!UICONTROL Admin] 사이드바에서 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**(으)로 이동합니다.

### 명령줄 사용

클라우드 인프라에서 Adobe Commerce의 JS 축소를 활성화하려면 다음을 수행하십시오.

1. 이 명령을 로컬에서 실행합니다.

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. `app/etc/config.php` 파일에 변경 내용을 커밋하고 다시 배포합니다.

## JS 파일 번들

Commerce [!UICONTROL Admin]에서 번들을 활성화할 수 있습니다. **[!UICONTROL Stores]** > ***[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**.

>[!NOTE]
>
>병합과 번들링을 동시에 활성화할 수 없습니다.

명령줄에서 Adobe Commerce 기본 제공 번들링(기본 번들링)을 활성화할 수도 있습니다.

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## JS 파일 병합(권장되지 않음) {#merge-js-files}

>[!WARNING]
>
>**[!UICONTROL Merge JavaScript Files]**&#x200B;을(를) 사용하지 않는 것이 좋습니다. 이 설정은 페이지의 **[!UICONTROL HEAD]** 섹션에서 동기적으로 로드된 JavaScript에 대해서만 디자인되었으며 번들링 및 [!DNL RequireJS] 논리가 제대로 작동하지 않을 수 있습니다. 이전 버전과의 호환성을 위해서만 유지되며 HTTP/2가 활성화된 경우 성능 이점을 제공하지 않습니다.
>
>**[!UICONTROL Merge JavaScript Files]**&#x200B;을(를) 활성화했지만 문제가 발생하면 패치를 적용하기 전에 비활성화해 보십시오. 병합을 사용하지 않도록 설정할 수 없으면 [ACSD-67908](../../../tools/quality-patches-tool/patches-available-in-qpt/v1-1-73/acsd-67908.md)을(를) 참조하세요.

## 추가 정보

- [클라이언트측 최적화 설정](../../../performance/configuration.md#client-side-optimization-settings)
- [구성 모범 사례](../../../performance/configuration.md#bundling-tips)의 *번들 팁*—타사 번들 도구, HTTP/2 및 더 이상 사용되지 않는 JS 및 CSS 병합에 대한 지침
- [사용 안내서: 리소스 파일 최적화](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [프론트엔드 개발자 안내서: CSS 병합, 축소 및 사이트 성능](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [고급 JavaScript 번들](../../../performance/advanced-js-bundling.md)
