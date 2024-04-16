---
title: Adobe Commerce 소프트웨어 다운로드
description: Adobe Commerce 소프트웨어를 다운로드하는 방법을 알아봅니다.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Adobe Commerce 소프트웨어 다운로드

전 세계 24만 명의 상인이 당사의 전자 상거래 소프트웨어를 신뢰하고 있습니다. 설치를 시작하는 데 도움이 되는 몇 가지 정보를 수집했습니다.

## 소프트웨어를 가져오는 방법

흥미로운 새로운 기능 및 릴리스의 가용성을 확인하고 이를 통해 얻는 방법에 대해 알아보십시오. [제품 가용성 페이지](https://devdocs.magento.com/release/availability.html).

Adobe Commerce 또는 Magento Open Source 설치를 시작하려면 다음 표를 참조하십시오.

<table>
    <tbody>
        <tr>
            <th>사용자 요구 사항</th>
            <th>설명</th>
            <th>높은 수준의 설치 및 업그레이드 단계</th>
            <th>시작 링크</th>
        </tr>
    <tr>
        <td><p>통합자, 패키지</p></td>
        <td><p>설치된 모든 구성 요소를 완벽하게 제어하고, 애플리케이션 서버에 액세스할 수 있으며, 고도로 기술적이며, Magento Open Source을 다른 구성 요소와 다시 패키징할 수 있습니다.</p>
        </td>
        <td><ol><li>작성기 만들기 <em>프로젝트</em> 에는 사용할 구성 요소 목록이 포함되어 있습니다.</li>
            <li>작성기를 사용하여 패키지 종속성 업데이트, 사용 <code>composer create-project</code> 를 클릭하여 Composer 메타패키지를 가져옵니다.</li>
            <li>를 사용하여 응용 프로그램을 설치합니다. <a href="../advanced.md">명령줄</a>.</li>
        <li>를 사용하여 애플리케이션 및 확장을 업그레이드합니다.  <a href="../../upgrade/implementation/perform-upgrade.md">명령줄</a>.</li></ol></td>
        <td><p><a href="../composer.md">메타패키지 가져오기</a></p></td>
    </tr>
    <tr>
        <td><p>기여 개발자</p></td>
        <td><p>Magento Open Source 코드베이스에 기여하고 버그를 파일링하며 애플리케이션을 사용자 정의합니다. 고도로 기술적이고 자체 개발 서버가 있으며 작성기 및 GitHub를 이해합니다.</p>
            <p>본인 <em>할 수 없음</em> 프로덕션 환경에서 애플리케이션을 사용합니다.</p>
      <p>다음을 사용하여 업그레이드해야 합니다. <a href="../../upgrade/developer/git-installs.md">작성기 및 Git 명령</a>.</p></td>
        <td><ol><li>GitHub 저장소를 복제합니다.</li>
            <li>작성기를 사용하여 패키지 종속성을 업데이트합니다.</li>
            <li>다음을 사용하여 응용 프로그램 설치 <a href="../advanced.md">명령줄</a>.</li>
            <li>다음을 사용하여 애플리케이션 업그레이드 <a href="../../upgrade/developer/git-installs.md">작성기 및 Git 명령</a>.</li>
            <li>아래의 코드를 사용자 지정합니다. <code>app/code</code> 디렉토리.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">GitHub 리포지토리 복제</a></p></td>
    </tr>
    </tbody>
</table>

## 유용한 정보

페이지 왼쪽에 있는 링크를 사용하여 설치의 각 부분에서 항목을 탐색합니다.

## 필요한 서버 권한

UNIX 시스템에는 `root` 웹 서버, PHP와 같은 소프트웨어를 설치하고 구성할 수 있는 권한. 이 소프트웨어를 설치하려면 다음을 확인하십시오. `root` 액세스 권한.

실행 *아님* 웹 서버 docroot에 응용 프로그램을 `root` 웹 서버가 해당 파일과 상호 작용하지 못할 수 있으므로 사용자.

필요 사항 `root` 만들기 권한 [파일 시스템 소유자](file-system/overview.md) 웹 서버의 그룹에 해당 소유자를 추가합니다. 파일 시스템 소유자를 사용하여 `bin/magento` 명령줄 및 cron job을 설정하는 명령이며, 이 명령을 사용하여 작업을 예약합니다.
