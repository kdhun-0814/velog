<p> 1) <strong>Ad-hoc 네트워크</strong> 개요
<strong>Ad-hoc 네트워크</strong>는 <strong>고정된 인프라 없이</strong> 노드들이 <strong>동적으로 연결되는 네트워크</strong>로, 라우터, 스위치, AP(Access Point) 같은 <strong>중앙 장비 없이</strong> 장치들(노드)이 <strong>직접 통신하는 구조</strong>이다. 즉, 즉석에서 형성되고 해체될 수 있는 네트워크다.</p>
<hr />
<p> 2) <strong>Ad-hoc 네트워크의 핵심 특징</strong>
특징    설명
<strong>비인프라 네트워크</strong>    <strong>AP나 라우터 없이 노드 간 직접 통신</strong>
<strong>자율적(Self-organizing)</strong>    <strong>네트워크가 자동으로 형성 및 관리됨</strong>
<strong>동적 토폴로지(Dynamic Topology)</strong>    <strong>노드 이동 시 네트워크 구조가 계속 변경됨</strong>
<strong>멀티 홉(Multi-hop) 통신</strong>    <strong>중간 노드를 통해 데이터 전달 가능</strong>
<strong>주변 노드 간 협력</strong>    <strong>노드들이 서로 데이터를 중계해줌</strong>
<strong>빠른 네트워크 구축</strong>    <strong>군사, 재난 대응 등에서 즉각적인 네트워크 형성 가능</strong></p>
<hr />
<p> 3) <strong>Ad-hoc 네트워크의 주요 유형</strong>
<strong>MANET (Mobile Ad-hoc Network, 이동형 애드혹 네트워크)</strong></p>
<p><strong>노드들이 이동하면서 동적으로 네트워크를 형성</strong>
예시: 군사 작전, 재난 지역 네트워크, 차량 통신
<strong>VANET (Vehicular Ad-hoc Network, 차량 애드혹 네트워크)</strong></p>
<p><strong>차량 간 통신(V2V), 차량과 인프라 간 통신(V2I) 지원</strong>
예시: 자율주행 차량 네트워크
<strong>WSN (Wireless Sensor Network, 무선 센서 네트워크)</strong></p>
<p><strong>환경 모니터링, 스마트 농업 등에서 센서들이 Ad-hoc 방식으로 연결됨</strong>
예시: 스마트 팩토리, 사물인터넷(IoT)</p>
<hr />
<p> 4) <strong>Ad-hoc 네트워크 라우팅 프로토콜</strong>
<strong>라우팅 프로토콜의 분류</strong>
구분    설명    예시 프로토콜
<strong>Proactive (Table-driven) 방식</strong>    <strong>모든 노드가 미리 라우팅 정보를 저장</strong>
<strong>빠른 경로 탐색 가능</strong>, 오버헤드 증가    <strong>DSDV, WRP, CGSR</strong>
<strong>Reactive (On-Demand) 방식</strong>    <strong>필요할 때만 경로를 설정하여 오버헤드 감소</strong>, 초기 전송 지연 존재    <strong>DSR, AODV, TORA, ABR, SSR</strong>
<strong>Hybrid (혼합) 방식</strong>    <strong>Proactive과 Reactive 방식을 결합하여 최적화</strong>    <strong>ZRP</strong>
 (1) <strong>Proactive 방식 (Table-driven)</strong>
<strong>DSDV (Destination-Sequenced Distance Vector)</strong></p>
<p><strong>Bellman-Ford 알고리즘 기반</strong>
<strong>목적지까지의 최단 거리와 순차 번호(Sequence Number)를 저장</strong>
<strong>라우팅 루프 방지</strong>
 <strong>WRP (Wireless Routing Protocol)</strong></p>
<p><strong>인접 노드(Neighbor)에게만 라우팅 정보를 전파하여 오버헤드 감소</strong>
<strong>CGSR (Clusterhead Gateway Switch Routing)</strong></p>
<p><strong>계층적(Cluster-based) 라우팅 방식으로 노드를 그룹화하여 라우팅 효율 개선</strong>
(2) <strong>Reactive 방식 (On-Demand)</strong>
<strong>DSR (Dynamic Source Routing)</strong></p>
<p><strong>다중 경로 지원</strong>, 비대칭 링크 가능
<strong>경로 정보를 데이터 패킷에 포함 (Source Routing)</strong>
<strong>AODV (Ad-hoc On-demand Distance Vector)</strong></p>
<p><strong>Multicast 지원</strong>
<strong>데이터 패킷에 경로 정보 포함하지 않음 (Overhead 감소)</strong>
<strong>대칭 링크(양방향 링크)만 지원</strong>
<strong>주기적인 Hello 메시지 필요</strong>
<strong>TORA (Temporary Ordered Routing Algorithm)</strong></p>
<p><strong>다중 경로(Multipath) 지원</strong>
<strong>Multicast 가능</strong>
<strong>ABR (Associativity-Based Routing)</strong></p>
<p><strong>오래 지속되는 경로를 우선 선택</strong>
<strong>일부 노드만 재설정하여 효율 증가</strong>
<strong>SSR (Scalable Source Routing)</strong></p>
<p><strong>연결성이 강한(Stable) 경로를 선택</strong>
<strong>중간 노드에서 경로 재설정 불가능</strong>
(3) <strong>Hybrid 방식 (혼합)</strong>
<strong>ZRP (Zone Routing Protocol)</strong></p>
<p><strong>네트워크를 여러 개의 Zone(영역)으로 분할</strong>
<strong>Zone 내부는 Proactive 방식</strong>, <strong>Zone 간은 Reactive 방식 사용</strong>
<strong>Proactive 방식의 오버헤드 문제 해결</strong></p>
<hr />
<p>5) <strong>Ad-hoc 네트워크의 데이터 전달 방식</strong>
<strong>트리 기반(Tree-based) 전달 방식</strong></p>
<p><strong>계층적 구조를 형성하여 데이터 전송</strong>
<strong>네트워크의 특정 노드가 중심이 되어 데이터 흐름을 관리</strong>
<strong>장점: 데이터 전달 경로가 명확하여 빠른 전송 가능</strong>
<strong>단점: 특정 노드에 장애 발생 시 전체 네트워크 성능 저하 가능</strong>
<strong>메시 기반(Mesh-based) 전달 방식</strong></p>
<p><strong>노드 간 다중 경로를 형성하여 데이터 전달</strong>
<strong>특정 노드의 장애가 발생해도 다른 경로를 통해 데이터 전송 가능</strong>
<strong>장점: 네트워크 안정성이 높음</strong>
<strong>단점: 불필요한 데이터 중복 전송 가능, 오버헤드 증가</strong></p>
<hr />
<ol start="3">
<li></li>
</ol>
<p><strong>현재 상황 및 향후 전망</strong>
<strong>Ad-hoc 네트워크는 5G, 6G, IoT, 자율주행, 스마트 시티와 결합하여 점점 발전 중이다.</strong>
<strong>VANET(차량 네트워크)</strong> → <strong>자율주행 및 스마트 교통 시스템에 필수</strong>
<strong>WSN(무선 센서 네트워크)</strong> → <strong>스마트 팩토리, IoT 센서 네트워크 활용</strong>
<strong>드론 &amp; 군사 네트워크</strong> → <strong>실시간 정보 공유, 보안 강화</strong></p>