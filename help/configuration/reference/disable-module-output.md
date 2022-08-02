---
title: 모듈 출력 비활성화
description: 모듈 출력을 비활성화하는 방법을 알아봅니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# 모듈 출력 비활성화

기본적으로 모듈 출력을 보기에 쓸 수 있도록 모든 모듈이 구성됩니다. 출력을 끄면 하드 종속성으로 인해 비활성화할 수 없는 모듈을 기본적으로 비활성화하는 방법이 제공됩니다.

예: `Customer` 모듈은 `Review` 모듈, `Review` 모듈을 사용하지 않도록 설정할 수 없습니다. 그러나 고객이 검토를 제공하지 않도록 하려면 `Review` 모듈.

>[!INFO]
>
>상인이 관리자를 사용하여 이전 릴리스에서 모듈 출력을 비활성화한 경우, 이러한 설정을 마이그레이션하도록 시스템을 수동으로 구성해야 합니다.

출력 비활성화는 다음 클래스에서 수행됩니다.

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>모듈 출력을 비활성화해도 모듈이 비활성화되지 않습니다. 모듈은 활성화 및 작동 상태로 유지되지만 블록, 페이지 또는 필드가 프런트 엔드 또는 백엔드에 렌더링되지 않습니다.

## 파이프라인 배포에서 모듈 출력 비활성화

파이프라인 배포 또는 기타 배포에서 상거래 애플리케이션의 여러 인스턴스를 사용하여 모듈 출력을 비활성화하려면 다음을 수행합니다.

1. 편집 `Backend` 모듈 `config.xml` 파일.
1. 구성 변경 사항을 내보냅니다.

### 편집 `Backend` 모듈 `config.xml` 파일

1. 원본 보관 `config.xml` 파일.
1. 다음과 유사한 라인을 `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` 파일, 바로 아래에 `<default>` 요소:

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

이 구성의 샘플 결과로, 고객은 더 이상 뉴스레터를 수신하기 위해 등록할 수 없습니다.

### 구성 변경 내용 내보내기

다음 명령을 실행하여 구성 변경 사항을 내보냅니다.

```bash
bin/magento app:config:dump
```

결과는 `<Magento_install_dir>/app/etc/config.php` 파일.

그런 다음 캐시를 지우면 새 설정이 활성화됩니다.

```bash
bin/magento cache:clean config
```

자세한 내용은 [구성 내보내기](../cli/export-configuration.md).

## 단순 배포에서 모듈 출력 비활성화

변경 사항을 배포하지 않아도 되므로 Commerce의 단일 인스턴스에서 모듈 출력을 비활성화하는 절차가 더 쉽습니다.

1. 원본 보관 `<Magento_install_dir>/app/etc/config.php` 파일.
1. 추가 `advanced` 및 `modules_disable_output` 섹션 `config.php` 파일(없는 경우):

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

이 예에서는 `Magento_Review` 모듈이 비활성화되어 고객이 더 이상 제품을 검토할 수 없습니다.
출력을 다시 활성화하려면 값을 `0`.
