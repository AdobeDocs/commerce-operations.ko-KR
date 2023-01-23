---
title: CSS 및 JS 리소스 파일 최적화
description: 관리자 또는 명령줄에서 Adobe Commerce 프로젝트용 CSS 및 JS(JavaScript) 파일을 병합하고 축소하는 방법을 알아봅니다.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: e6e8a2d7ef059265dbcbfcd6be117828a639f6d6
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# 리소스 파일 최적화

응답형 상거래 사이트를 위해 CSS 및 JS(JavaScript) 리소스 파일을 최적화하고 렌더링 차단 리소스를 제거합니다.

- **CSS 및 JS 파일 최적화**- 별도의 파일을 하나의 파일로 병합, 축소 및 번들로 포함하도록 Adobe Commerce을 구성하여 CSS 및 JS(JavaScript) 파일을 로드하는 데 필요한 시간을 줄입니다.
- **렌더링 차단 리소스 제거**- 중요한 JS 및 CSS 기능을 인라인으로 전달하고 모든 비중요 JS/CSS 스타일을 추론해 보십시오. 자세한 내용은 [렌더링 차단 리소스 제거](https://web.dev/render-blocking-resources/).

## 영향을 받는 제품 및 버전

[지원되는 모든 버전, 2.3 이상](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스
- Magento Open Source

## CSS 파일 병합 또는 축소

별도의 파일을 하나의 파일로 병합, 축소 및 번들링하여 CSS 및 JS(JavaScript) 파일을 로드하는 데 걸리는 시간을 줄일 수 있습니다.

>[!IMPORTANT]
>
>클라우드 인프라의 Adobe Commerce은 항상 프로덕션 모드에서 실행되며, 그렇지 않으면 설정할 수 없으므로 명령줄 메서드를 사용하여 병합, 축소 및 번들링을 활성화해야 합니다.

### 관리자 사용

CSS 병합 또는 축소를 활성화하려면 [!UICONTROL **관리** > **스토어** > **설정** > **구성** > **고급** > **개발자** > **CSS 설정**].

### 명령줄 사용

클라우드 인프라에서 Adobe Commerce에서 CSS 병합을 사용하려면

1. 로컬에서 이 명령 실행:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. 변경 내용을 `app/etc/config.php` 파일 및 재배포

클라우드 인프라에서 Adobe Commerce에서 CSS 축소를 사용하려면

1. 로컬에서 이 명령 실행:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. 변경 내용을 `app/etc/config.php` 파일 및 재배포

## JS 파일 축소

### 관리자 사용

설정 *관리* 사이드바, 다음 위치로 이동 **스토어** > **설정** > **구성** > **고급** > **개발자** > **JavaScript 설정**.

### 명령줄 사용

클라우드 인프라에서 Adobe Commerce에서 JS 축소를 사용하려면

1. 로컬에서 이 명령 실행:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. 변경 내용을 `app/etc/config.php` 파일 및 재배포

## JS 파일 병합 및 번들

상거래 관리자에서 병합 또는 번들링을 설정할 수 있습니다(병합과 번들링을 동시에 사용할 수 없음). [!UICONTROL **스토어** > **설정** > **구성** > **고급** > **개발자** > **JavaScript 설정**].

명령줄에서 Adobe Commerce 기본 제공 번들(기본 번들링)을 활성화할 수도 있습니다.

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## 추가 정보

- [클라이언트측 최적화 설정](../../../performance/configuration.md#client-side-optimization-settings)
- [사용 안내서: 리소스 파일 최적화](https://docs.magento.com/user-guide/system/file-optimization.html)
- [프런트 엔드 개발자 안내서: CSS 병합, 축소 및 사이트 성능](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [고급 JavaScript 번들](../../../performance/advanced-js-bundling.md)

