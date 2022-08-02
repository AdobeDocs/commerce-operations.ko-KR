---
title: Varnish ESI 블록
description: Edge Side Include와 이러한 정보를 사용하여 웹 페이지를 포함할 수 있는 방법에 대해 알아봅니다.
contributor_name: Goivvy LLC
contributor_link: https://www.goivvy.com/magento-optimization-service
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Varnish ESI 블록

Edge Side Includes (ESI)는 다른 웹 페이지에 웹 페이지를 포함하는 데 사용할 수 있는 특수 지시문입니다.

예:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

바니쉬가 컨텐츠를 `http://domain.com/index.php/page_cache/block/esi/blocks` 그리고 `<esi>` 태깅 합니다.

## 상거래 및 Varnish ESI

다음 조건이 충족되면 Commerce 프레임워크에서 ESI 태그를 생성합니다.

- 캐싱 응용 프로그램이 `Varnish Cache`
- XML 레이아웃 `block` 요소가 `ttl` 특성

### 예

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

위의 예에서 `block` 요소는 컨텐츠를 `esi.phtml` 템플릿을 홈 페이지로 추가하면 Varnish가 30초마다 자동으로 업데이트됩니다.

## 제한 사항

현재 Varnish는 HTTPS를 통해 ESI를 지원하지 않으므로 HTTP로 자동 전환합니다.

`Magento\PageCache\Observer\ProcessLayoutRenderElement`:

```php
    private function _wrapEsi(
        \Magento\Framework\View\Element\AbstractBlock $block,
        \Magento\Framework\View\Layout $layout
    ) {
    ....
        // Varnish does not support ESI over HTTPS must change to HTTP
        $url = substr($url, 0, 5) === 'https' ? 'http' . substr($url, 5) : $url;
        return sprintf('<esi:include src="%s" />', $url);
    }
```
