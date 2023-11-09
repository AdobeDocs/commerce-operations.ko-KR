---
title: CSS 및 JS 리소스 파일 최적화
description: 관리자 또는 명령줄에서 Adobe Commerce 프로젝트에 대한 CSS 및 JavaScript(JS) 파일을 병합하고 축소하는 방법을 알아봅니다.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 2662ced484fb42bf2d32609e4e82364c1e47c8f0
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# 리소스 파일 최적화

더 반응형 상거래 사이트의 경우 CSS 및 JavaScript(JS) 리소스 파일을 최적화하고 렌더링 차단 리소스를 제거합니다.

- **CSS 및 JS 파일 최적화**—Adobe Commerce에서 개별 파일을 하나의 파일로 병합, 축소 및 번들로 구성하여 CSS 및 JavaScript(JS) 파일을 로드하는 데 필요한 시간을 줄입니다.
- **렌더링 차단 리소스 제거**—중요한 JS 및 CSS 기능을 인라인으로 제공하고 중요하지 않은 모든 JS/CSS 스타일을 연기합니다. 자세한 내용은 [렌더링 차단 리소스 제거](https://web.dev/render-blocking-resources/).

## 영향을 받는 제품 및 버전

[지원되는 모든 버전, 2.3 이상](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스
- Magento Open Source

## CSS 파일 병합 또는 축소

CSS 및 JavaScript(JS) 파일을 로드하는 데 걸리는 시간을 별도의 파일을 단일 파일로 병합, 축소 및 번들링하여 줄일 수 있습니다.

>[!IMPORTANT]
>
>클라우드 인프라의 Adobe Commerce은 항상 프로덕션 모드에서 실행되며, 달리 설정할 수 없으므로 명령줄 메서드를 사용하여 병합, 축소 및 번들링을 활성화해야 합니다.

배포에서 HTTP/2를 사용하는 경우 파일을 병합하거나 번들로 묶지 마십시오. HTTP/2는 정적 파일을 비동기식으로 다운로드합니다. 브라우저는 파일 컨텐츠를 처리하기 전에 병합된 파일 전체를 다운로드해야 합니다.

### 관리자 사용

CSS 병합 또는 축소를 활성화하려면 [!UICONTROL **관리자** > **스토어** > **설정** > **구성** > **고급** > **개발자** > **CSS 설정**].

### 명령줄 사용

클라우드 인프라에서 Adobe Commerce의 CSS 병합을 활성화하려면 다음을 수행하십시오.

1. 이 명령을 로컬에서 실행합니다.

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. 변경 내용 커밋 `app/etc/config.php` 파일 및 재배포.

클라우드 인프라에서 Adobe Commerce의 CSS 축소를 활성화하려면:

1. 이 명령을 로컬에서 실행합니다.

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. 변경 내용 커밋 `app/etc/config.php` 파일 및 재배포.

## JS 파일 축소

### 관리자 사용

다음에서 *관리자* 사이드바, 이동 **스토어** > **설정** > **구성** > **고급** > **개발자** > **JavaScript 설정**.

### 명령줄 사용

클라우드 인프라에서 Adobe Commerce의 JS 축소를 활성화하려면 다음을 수행하십시오.

1. 이 명령을 로컬에서 실행합니다.

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. 변경 내용 커밋 `app/etc/config.php` 파일 및 재배포.

## JS 파일 병합 및 번들

Commerce 관리에서 병합 또는 번들링을 설정할 수 있습니다(병합과 번들링을 동시에 활성화할 수 없음). [!UICONTROL **스토어** > **설정** > **구성** > **고급** > **개발자** > **JavaScript 설정**].

명령줄에서 Adobe Commerce 기본 제공 번들링(기본 번들링)을 활성화할 수도 있습니다.

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## 추가 정보

- [클라이언트측 최적화 설정](../../../performance/configuration.md#client-side-optimization-settings)
- [사용 안내서: 리소스 파일 최적화](https://docs.magento.com/user-guide/system/file-optimization.html)
- [프론트엔드 개발자 안내서: CSS 병합, 축소 및 사이트 성능](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [고급 JavaScript 번들](../../../performance/advanced-js-bundling.md)
