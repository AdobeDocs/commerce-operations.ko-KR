---
title: '"다음 [!UICONTROL Elasticsearch] tab"'
description: 에 대해 알아보기 [!UICONTROL Elasticsearch] 탭 [!DNL Observation for Adobe Commerce].
source-git-commit: 2427a18ea67833bc50912ef78be29d4320b5b205
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 다음 [!UICONTROL Elasticsearch] 탭

## [!UICONTROL Cluster Status Summary]:

![클러스터 상태 요약](../../assets/tools/cluster-status-summary.jpg)

선택한 기간 동안 **[!UICONTROL Cluster Status Summary]** 프레임은 [!DNL Elasticsearch] 클러스터가 통과되었습니다. 이 예에서는 선택한 기간 동안 클러스터가 녹색 상태가 한 번 되고 선택한 기간 동안 노란색 상태가 되었습니다.

## [!UICONTROL Active Primary Shards]

![활성 기본 샤드](../../assets/tools/active-primary-shards.jpg)

다음 **[!UICONTROL Active Primary Shards]** 프레임에는 선택한 계정의 활성 기본 샤드의 수에 따라 숫자가 다르게 표시됩니다 [!DNL Elasticsearch] 서비스.

From [!DNL Elasticsearch]: 최종 안내서 [2.x]:

&quot;In [동적으로 업데이트할 수 있는 인덱스](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html)사드는 루센 색인이고 [!DNL Elasticsearch] 인덱스는 섀드의 컬렉션입니다. 애플리케이션이 인덱스에 대해 말하고 [!DNL Elasticsearch] 요청을 적절한 섀드로 라우팅합니다. 샤드는 저울의 단위이다. 표시할 수 있는 가장 작은 인덱스는 단일 샤드가 있는 인덱스입니다. 이러한 정보는 사용자의 요구 사항에 충분할 수 있습니다. 하나의 공유는 많은 데이터를 보유할 수 있지만 확장시킬 수 있는 기능은 제한됩니다.&quot;

인덱스를 만들 때 해당 인덱스로 여러 개의 섀드가 만들어집니다. 기본적으로 5개의 기본 섀드가 각 새 인덱스에 할당되며, 즉, 인덱스를 5개의 노드에 분산할 수 있습니다(노드당 하나의 공유). 복제 샤드도 있습니다. 주로 페일오버용입니다. 복제본 섀드는 읽기 요청을 제공할 수 있습니다.

## [!UICONTROL Active Shards in Cluster]

![클러스터의 활성 공유](../../assets/tools/active-shards-in-cluster.jpg)

**[!UICONTROL Active Shards in Cluster]** - 모든 운영 및 복제본 섀드가 [!DNL Elasticsearch] 클러스터

## [!UICONTROL Index health - this will show the index name and color status]

![인덱스 상태](../../assets/tools/index-health.jpg)

이 프레임에는 인덱스 이름과 인덱스 색상 상태 수가 표시됩니다. 표를 아래로 스크롤하면 동일한 인덱스 이름이 노란색 및 빨간색 색상 상태로 표시됩니다. 27 인덱스 이름 뒤에 오는 숫자는 상태 색상의 수입니다. 0이면 선택한 기간 동안 해당 색상 상태에 있는 인덱스의 인스턴스가 없습니다.

## [!UICONTROL Elasticsearch Status by node information]

![Elasticsearch 상태](../../assets/tools/elasticsearch-status-by-node.jpg)

다음 **[!UICONTROL Elasticsearch Status by node information]** 프레임이 [!DNL Elasticsearch] 노드별 클러스터 상태 이 옵션은 [!DNL Elasticsearch] 클러스터에서 선택한 일정 동안 어떤 상태를 반환하고 있습니다.

## [!UICONTROL Elasticsearch index information]

![Elasticsearch 인덱스 정보](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

이 **[!UICONTROL Elasticsearch index information]** 테이블에는 인덱스 이름, 인덱스 이름, 노드, 인덱싱된 문서 수, 인덱스 상태 및 특정 시간에 대한 인덱스 크기(MB)가 표시됩니다.

## [!UICONTROL Elasticsearch process CPU %]

![Elasticsearch 프로세스 CPU](../../assets/tools/elasticsearch-process-cpu.jpg)

다음 **[!UICONTROL Elasticsearch process CPU %]** 프레임은 프로세스 CPU%를 [!DNL Elasticsearch] 선택한 기간에 대해 처리합니다.

## [!UICONTROL Elasticsearch Memory garbage collection]

![Elasticsearch 메모리 가비지](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] 는 Java 프로세스입니다. 할당된 메모리에서 낮은 속도로 실행되면 메모리를 확보하기 위해 가비지 수집을 시작합니다. 가비지 수집이 빈번한 경우 할당된 메모리에 너무 많은 색인이나 파지가 있을 수 있음을 나타냅니다. 색인과 파형을 정리할 수 있는 기회가 있을 수도 있고 [!DNL Elasticsearch] 메모리가 더 필요할 수 있습니다.

## [!UICONTROL Elasticsearch Index information]

![Elasticsearch 인덱스 정보](../../assets/tools/elasticsearch-index-information-2.jpg)

인덱스가 만들어지고 업데이트되면 인덱스 상태가 변경될 수 있습니다.

## [!UICONTROL Elasticsearch Index Size]

![Elasticsearch 인덱스 크기](../../assets/tools/elasticsearch-index-size.jpg)

다음 **[!UICONTROL Elasticsearch Index Size]** 프레임은 선택한 일정의 인덱스 이름과 크기를 나타냅니다. 사이트가 색인화하는 방식에 문제가 있음을 나타낼 수 있습니다.

## [!UICONTROL Elasticsearch Errors]

![Elasticsearch 오류](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

다음 **[!UICONTROL Elasticsearch Errors]** 프레임에는 오류가 표시됩니다 [!DNL Elasticsearch] 공간이 부족한 것처럼 모든 섀드가 실패하는 경우, 검색에 매개 변수 문제가 있는 경우 버전 오류 및 모든 노드를 사용할 수 없는 경우 노랑에서 빨간색 상태로 전환하십시오.

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Elasticsearch 할당되지 않은 샤드](../../assets/tools/elasticsearch-unassigned-shards.jpg)

할당되지 않은 섀드로 인해 클러스터가 녹색 상태에서 노란색 상태로 이동합니다.
