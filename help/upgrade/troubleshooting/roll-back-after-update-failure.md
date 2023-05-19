---
title: 모듈 업데이트 실패 후 롤백
description: 모듈 업데이트 오류가 발생한 후 Adobe Commerce 또는 Magento Open Source 업그레이드 문제를 해결합니다.
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# 모듈 업데이트 실패 후 롤백

모듈 업데이트가 실패하면 콘솔 로그에 다음과 유사한 메시지가 표시됩니다.

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

앞의 예에는 롤백할 구성 요소 버전이 없습니다. 구성 요소 공급업체에 문의하거나 직접 문제를 해결하십시오.

그동안 을 클릭하여 이전 버전으로 롤백할 수 있습니다. **롤백**&#x200B;이전에 백업하지 않았더라도 데이터를 복구합니다.
