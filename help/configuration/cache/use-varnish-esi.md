---
title: 바니시 ESI 차단
description: ESI(Edge Side Includes) 및 Adobe Commerce의 웹 페이지를 포함하는 방법에 대해 알아봅니다. ESI 블록 구현 및 최적화에 대해 살펴봅니다.
badge: label="콘스탄틴 G 기여." type="Informative" url="https://github.com/goivvy" tooltip="콘스탄틴"
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '136'
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

바니시는 `http://domain.com/index.php/page_cache/block/esi/blocks`의 콘텐츠를 가져와서 `<esi>` 태그를 이 태그로 바꿉니다.

## Commerce 및 바니시 ESI

Commerce 프레임워크는 다음 조건이 충족되면 ESI 태그를 생성합니다.

- 캐싱 응용 프로그램이 `Varnish Cache`(으)로 설정되어 있습니다.
- XML 레이아웃 `block` 요소가 `ttl` 특성과 함께 추가되었습니다.

### 예

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

위의 예에서 `block` 요소는 `esi.phtml` 템플릿의 콘텐츠를 홈 페이지에 추가하고 Vannish는 30초마다 자동으로 업데이트합니다.

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
