---
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---
# 통신이 안전한지 확인

이 섹션에서는 HTTP 기본 인증이 작동하는지 확인하는 두 가지 방법에 대해 설명합니다.

* 사용 `curl` 클러스터 상태를 가져오려면 사용자 이름과 암호를 입력해야 하는지 확인하는 명령
* Admin에서 HTTP 기본 인증 구성

## 사용 `curl` 클러스터 상태를 확인하는 명령

다음 명령을 입력합니다.

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

예를 들어 검색 엔진 서버에서 명령을 입력하고 프록시가 포트 8080을 사용하는 경우:

```bash
curl -i http://localhost:8080/_cluster/health
```

인증 실패를 나타내는 다음 메시지가 표시됩니다.

```terminal
HTTP/1.1 401 Unauthorized
Date: Tue, 23 Feb 2016 20:35:29 GMT
Content-Type: text/html
Content-Length: 194
Connection: keep-alive
WWW-Authenticate: Basic realm="Restricted"
<html>
<head><title>401 Authorization Required</title></head>
<body bgcolor="white">
  <center><h1>401 Authorization Required</h1></center>
</body>
</html>
```

이제 다음 명령을 시도하십시오.

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

예:

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

이번에는 다음과 유사한 메시지로 명령이 성공합니다.

```terminal
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## 관리자에서 HTTP 기본 인증 구성

에 설명된 것과 동일한 작업 수행 [검색 엔진 구성](../configuration/search/configure-search-engine.md) *제외* 클릭 **[!UICONTROL Yes]** 다음에서 **[!UICONTROL Enable HTTP Auth]** 제공된 필드에 사용자 이름과 암호를 나열하고 입력합니다.

클릭 **[!UICONTROL Test Connection]** 제대로 작동하는지 확인한 다음 **[!UICONTROL Save Config]**.

계속하기 전에 캐시를 플러시하고 다시 인덱싱해야 합니다.
