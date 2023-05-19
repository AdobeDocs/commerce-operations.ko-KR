---
title: 모듈 출력 비활성화
description: 모듈 출력을 비활성화하는 방법에 대해 알아봅니다.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# 모듈 출력 비활성화

기본적으로 모든 모듈은 모듈 출력을 뷰에 쓸 수 있도록 구성됩니다. 출력을 끄면 하드 종속성으로 인해 비활성화할 수 없는 모듈을 본질적으로 비활성화할 수 있습니다.

예를 들어 `Customer` 모듈은 다음에 따라 다릅니다. `Review` 모듈, 따라서 `Review` 모듈을 비활성화할 수 없습니다. 그러나 고객이 리뷰를 제공하지 않도록 하려면 의 출력을 끌 수 있습니다. `Review` 모듈.

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

Commerce 애플리케이션의 여러 인스턴스를 사용하여 파이프라인 배포 또는 다른 배포에서 모듈 출력을 비활성화하려면 다음을 수행합니다.

1. 편집 `Backend` 모듈 `config.xml` 파일.
1. 구성 변경 사항을 내보냅니다.

### 편집 `Backend` 모듈 `config.xml` 파일

1. 원본 보관 `config.xml` 파일.
1. 다음에 유사한 줄을 추가합니다. `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` 파일, 바로 아래 `<default>` 요소:

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   여기:

   - `<modules_disable_output>` 모듈 목록을 포함합니다.
   - `<Magento_Newsletter></Magento_Newsletter>` 출력을 비활성화할 모듈을 지정합니다.
   - `1` 은 의 출력을 비활성화하는 플래그입니다. `Magento_Newsletter` 모듈.

이 구성의 샘플 결과로 고객은 더 이상 뉴스레터를 수신하기 위해 등록할 수 없습니다.

### 구성 변경 사항 내보내기

다음 명령을 실행하여 구성 변경 사항을 내보냅니다.

```bash
bin/magento app:config:dump
```

결과는 다음에 기록됩니다. `<Magento_install_dir>/app/etc/config.php` 파일.

그런 다음 캐시를 지워 새 설정을 활성화합니다.

```bash
bin/magento cache:clean config
```

다음을 참조하십시오 [구성 내보내기](../cli/export-configuration.md).

## 단순 배포에서 모듈 출력 비활성화

단일 Commerce 인스턴스에서 모듈 출력을 비활성화하는 절차는 변경 사항을 배포하지 않아도 되므로 더 쉽습니다.

1. 원본 보관 `<Magento_install_dir>/app/etc/config.php` 파일.
1. 추가 `advanced` 및 `modules_disable_output` 섹션에 대한 섹션 `config.php` 파일(없는 경우):

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

이 예제의 출력 `Magento_Review` 모듈이 비활성화되어 고객이 더 이상 제품을 검토할 수 없습니다.
출력을 다시 활성화하려면 값을 로 설정합니다. `0`.
