<h3 id="전송-계층-개요">전송 계층 개요</h3>
<p>전송 계층은 <strong>네트워크 계층</strong>과 <strong>응용 계층</strong> 사이에 위치하며, 두 가지 핵심 기능을 수행한다.</p>
<ol>
<li><strong>IP의 한계 보완</strong>: 신뢰성 있는 통신과 연결형 통신을 가능하게 함.</li>
<li><strong>응용 계층 프로세스 식별</strong>: 응용 포트 번호를 활용하여 데이터를 최종 목적지인 특정 애플리케이션에 전달함.<img src="https://velog.velcdn.com/images/kdhun-0814/post/3a690b2e-91ef-4217-b194-adf4f6e1dc1b/image.png" />

</li>
</ol>
<hr />
<h3 id="ip의-한계-비신뢰성-및-비연결형-통신">IP의 한계: 비신뢰성 및 비연결형 통신</h3>
<p>IP는 <strong>비신뢰성</strong> 및 <strong>비연결형</strong> 통신을 수행하는 프로토콜이다.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/5620a406-1630-4d8c-b923-e09bb5b6c7af/image.png" /></p>
<ul>
<li><strong>비신뢰성 통신</strong>: 패킷이 수신지까지 제대로 전송되었다는 보장을 하지 않는다. 통신 과정에서 패킷이 손상되거나 순서가 뒤바뀌어도 이를 확인하거나 재전송하지 않는다.</li>
<li><strong>비연결형 통신</strong>: 송수신 호스트 간에 사전 연결 수립 절차를 거치지 않고, 그저 패킷을 보내기만 한다.</li>
</ul>
<p>IP가 이러한 방식을 택한 이유는 모든 통신에 신뢰성과 연결성이 필요한 것이 아니며, 불필요한 절차를 생략하여 <strong>성능을 향상</strong>시키기 위함이다.</p>
<hr />
<h3 id="ip-한계를-보완하는-전송-계층-프로토콜">IP 한계를 보완하는 전송 계층 프로토콜</h3>
<p>전송 계층의 주요 프로토콜인 <strong>TCP</strong>와 <strong>UDP</strong>는 IP의 한계를 보완하거나 목적에 따라 다른 통신 방식을 제공한다.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/60fa2e8e-120b-41e2-9721-0c9c49062372/image.png" /></p>
<ul>
<li><strong>TCP (Transmission Control Protocol)</strong>
: <strong>연결형</strong> 통신과 <strong>신뢰성 있는</strong> 통신을 제공한다. 송수신하는 동안 연결을 유지하며, 재전송을 통한 오류 제어, 흐름 제어, 혼잡 제어 등 다양한 기능을 제공하여 데이터의 정확한 전달을 보장한다.</li>
<li><strong>UDP (User Datagram Protocol)</strong>
: <strong>비신뢰성</strong> 통신과 <strong>비연결형</strong> 통신을 제공한다. TCP보다 상대적으로 전송 속도가 빠르며, 데이터의 정확성보다 실시간성이 중요한 통신(예: 영상 스트리밍, 음성 통화)에 주로 사용된다.</li>
</ul>
<hr />
<h3 id="포트를-활용한-애플리케이션-식별">포트를 활용한 애플리케이션 식별</h3>
<p>패킷은 단순히 컴퓨터에 도달하는 것이 아니라, 해당 컴퓨터에서 실행 중인 특정 <strong>프로세스</strong>에 도달해야 한다. 이때 특정 프로세스를 식별하는 정보가 <strong>포트</strong>이다.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/72f26d3f-06d0-44f1-bfdd-f68b2704610a/image.png" />
패킷의 헤더에는 <strong>송신지 포트</strong>와 <strong>수신지 포트</strong>가 포함되어 송수신 호스트의 특정 애플리케이션을 식별한다. 포트는 16비트로 표현되어 <code>0</code>부터 <code>65535</code>까지 총 <code>2^16</code>개의 포트를 사용할 수 있다.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/bc0579d9-fd6f-4daa-b140-d2fde3157855/image.png" />
<img src="https://velog.velcdn.com/images/kdhun-0814/post/785d9dbe-7e6a-4a5b-a21d-e7b73fdeb169/image.png" /></p>
<p>포트는 용도에 따라 세 가지로 분류된다.</p>
<ul>
<li><strong>잘 알려진 포트(Well-known Ports)</strong>: <code>0</code>번부터 <code>1023</code>번까지의 포트로, HTTP(80), FTP(21) 등 범용적으로 사용되는 애플리케이션 프로토콜에 할당된다.<img src="https://velog.velcdn.com/images/kdhun-0814/post/6be7e9c3-71e4-47af-b9f0-57c5800adfc7/image.png" /></li>
<li><strong>등록된 포트(Registered Ports)</strong>: <code>1024</code>번부터 <code>49151</code>번까지의 포트로, 잘 알려진 포트에 비해서는 덜 범용적이다. 흔히 사용되는 애플리케이션 프로토콜에 할당하기 위해 사용된다.<img src="https://velog.velcdn.com/images/kdhun-0814/post/fb5466f2-8bc4-4de3-8d50-f771f15298d3/image.png" /></li>
<li><strong>동적/사설 포트(Dynamic/Private Ports)</strong>: <code>49152</code>번부터 <code>65535</code>번까지의 포트로, 특별히 관리되지 않으며 클라이언트가 임시로 사용한다.<img src="https://velog.velcdn.com/images/kdhun-0814/post/6acb21b9-d050-4ae8-9031-42548daae066/image.png" />

</li>
</ul>
<p>네트워크에서 특정 애플리케이션 프로세스를 식별하기 위해서는 <strong>IP 주소와 포트 번호</strong>가 함께 사용된다.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/c42125cf-b955-4fbc-95b2-91a097315427/image.png" /></p>