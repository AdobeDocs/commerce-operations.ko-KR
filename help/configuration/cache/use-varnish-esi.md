---
title: 바니시 ESI 차단
description: Edge Side 포함 및 이를 사용하여 웹 페이지를 포함하는 방법에 대해 알아봅니다.
badge: label="콘스탄틴 G.에서 제공." type="정보" url="https://github.com/goivvy" tooltip="콘스탄틴 G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# 바니시 ESI 차단

ESI(Edge Side Includes)는 다른 웹 페이지에 웹 페이지를 포함하는 데 사용할 수 있는 특수 지시문입니다.

예:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

니스 페치 내용물 `http://domain.com/index.php/page_cache/block/esi/blocks` 및 바꾸기 `<esi>` 태그로 묶습니다.

## 상거래 및 바니시 ESI

상거래 프레임워크는 다음 조건이 충족되면 ESI 태그를 생성합니다.

- 캐싱 응용 프로그램이 로 설정되어 있습니다. `Varnish Cache`
- XML 레이아웃 `block` 요소가 와 함께 추가됨 `ttl` 속성

### 예

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

위의 예에서 `block` 요소가 다음에서 컨텐츠를 추가합니다. `esi.phtml` 템플릿을 홈 페이지에 추가하고 Vannish에서 30초마다 자동으로 업데이트합니다.

## 제한 사항

현재 Varnish 는 HTTPS에서 ESI를 지원하지 않으므로 자동으로 HTTP로 전환합니다.

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
