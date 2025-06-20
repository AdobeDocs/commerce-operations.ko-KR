---
title: 모듈 출력 비활성화
description: 모듈 출력을 비활성화하는 방법에 대해 알아봅니다.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: fee09845777e23717e618ac57df4158d6b172d4f
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# 모듈 출력 비활성화

기본적으로 모든 모듈은 모듈 출력을 뷰에 쓸 수 있도록 구성됩니다. 출력을 끄면 하드 종속성으로 인해 비활성화할 수 없는 모듈을 본질적으로 비활성화할 수 있습니다.

예를 들어 `Customer` 모듈은 `Review` 모듈에 종속되므로 `Review` 모듈을 사용하지 않도록 설정할 수 없습니다. 그러나 고객이 리뷰를 제공하지 않도록 하려면 `Review` 모듈에서 출력을 끌 수 있습니다.

>[!INFO]
>
>판매자가 이전 릴리스에서 관리를 사용하여 모듈 출력을 비활성화한 경우 이러한 설정을 마이그레이션하도록 시스템을 수동으로 구성해야 합니다.

출력 비활성화는 다음 클래스에서 수행됩니다.

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>모듈 출력을 비활성화해도 모듈이 비활성화되지 않습니다. 모듈은 계속 활성화되고 작동하지만 블록, 페이지 또는 필드가 프론트엔드 또는 백엔드에 렌더링되지 않습니다.

## 파이프라인 배포에서 모듈 출력 비활성화

Commerce 애플리케이션의 여러 인스턴스를 사용하여 파이프라인 배포 또는 기타 배포에서 모듈 출력을 비활성화하려면 다음을 수행하십시오.

1. `Backend` 모듈의 `config.xml` 파일을 편집합니다.
1. 구성 변경 사항을 내보냅니다.

### `Backend` 모듈 `config.xml` 파일 편집

1. 원본 `config.xml` 파일을 보관합니다.
1. `<default>` 요소 바로 아래에 다음과 유사한 줄을 `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` 파일에 추가합니다.

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   여기:

   - `<modules_disable_output>`에 모듈 목록이 있습니다.
   - `<Magento_Newsletter></Magento_Newsletter>`은(는) 출력을 비활성화할 모듈을 지정합니다.
   - `1`은(는) `Magento_Newsletter` 모듈에 대한 출력을 비활성화하는 플래그입니다.

이 구성의 샘플 결과로 고객은 더 이상 뉴스레터를 수신하기 위해 등록할 수 없습니다.

### 구성 변경 사항 내보내기

다음 명령을 실행하여 구성 변경 사항을 내보냅니다.

```bash
bin/magento app:config:dump
```

결과가 `<Magento_install_dir>/app/etc/config.php` 파일에 기록됩니다.

그런 다음 캐시를 지워 새 설정을 활성화합니다.

```bash
bin/magento cache:clean config
```

[구성 내보내기](../cli/export-configuration.md)를 참조하십시오.

## 단순 배포에서 모듈 출력 비활성화

변경 사항을 배포하지 않아도 되므로 Commerce의 단일 인스턴스에서 모듈 출력을 비활성화하는 절차가 더 쉽습니다.

1. 원본 `<Magento_install_dir>/app/etc/config.php` 파일을 보관합니다.
1. `advanced` 및 `modules_disable_output` 섹션을 `config.php` 파일에 추가합니다(없는 경우).

   ```php
   'system' =>
     array (
       'websites' =>
       array (
         'base' =>
         array (
           'advanced' =>
           array (
             'modules_disable_output' =>
             array (
               'Magento_Review' => '1',
             ),
           ),
         ),
       ),
     ),
   ```

이 예에서는 `Magento_Review` 모듈에 대한 출력이 비활성화되어 고객이 더 이상 제품을 검토할 수 없습니다.

### 모듈 출력 다시 활성화

출력을 다시 사용하려면 모듈의 값을 `0`(으)로 설정하거나 `config.php` 파일에서 줄/모듈을 제거하십시오.
