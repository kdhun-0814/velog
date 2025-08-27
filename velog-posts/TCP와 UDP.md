<h3 id="tcp와-udp-개요">TCP와 UDP 개요</h3>
<p><strong>TCP</strong>는 신뢰성 있는 통신을 위한 <strong>연결형 프로토콜</strong>이며, <strong>UDP</strong>는 TCP보다 신뢰성은 낮지만 비교적 빠른 통신이 가능한 <strong>비연결형 프로토콜</strong>. 이들은 네트워크 계층의 IP를 보완하여 응용 계층의 프로세스를 식별하고 데이터를 전달한다.</p>
<ul>
<li><strong>IP의 한계</strong>: IP는 신뢰성을 보장하지 않는 '최선 노력(best-effort)' 프로토콜. 패킷의 전달 순서나 성공 여부를 보장하지 않는다.</li>
<li><strong>전송 계층의 역할</strong>: 전송 계층은 이러한 IP의 한계를 보완하여, 데이터의 정확한 전달을 보장하거나(TCP) 성능을 우선하여 통신(UDP)하도록 돕는다.</li>
</ul>
<hr />
<h3 id="tcp-transmission-control-protocol">TCP (Transmission Control Protocol)</h3>
<p>TCP는 통신을 시작하기 전에 <strong>연결을 수립</strong>하고, 데이터 송수신이 끝나면 <strong>연결을 종료</strong>하는 단계적인 통신 과정을 거침. 데이터 전송 중에는 재전송을 통한 오류 제어, 흐름 제어, 혼잡 제어 등의 기능을 제공하여 신뢰성을 보장.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/90b4dda2-453e-4850-95b0-786d4f96f51c/image.png" /></p>
<h4 id="tcp-세그먼트-구조">TCP 세그먼트 구조</h4>
<p>TCP는 데이터를 <strong>세그먼트(Segment)</strong> 단위로 전송. MSS(Maximum Segment Size)는 TCP로 전송할 수 있는 페이로드의 최대 크기이며, TCP 헤더 크기는 제외.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/a9e8bb00-a17a-46dc-89c2-9b7c0abbf13d/image.png" /></p>
<p>핵심 필드</p>
<ul>
<li><strong>포트 번호</strong>: 송수신 포트 번호를 통해 애플리케이션을 식별.</li>
<li><strong>순서 번호 (Sequence Number)</strong>: 세그먼트 데이터의 첫 바이트에 부여되는 번호로, 패킷의 올바른 순서를 보장.</li>
<li><strong>확인 응답 번호 (Acknowledgment Number)</strong>: 상대방이 보낸 세그먼트에 대한 응답으로, 다음에 수신하기를 기대하는 순서 번호를 명시.<img src="https://velog.velcdn.com/images/kdhun-0814/post/a0c4039f-5d08-4512-ad05-614b1bdd102e/image.png" /></li>
<li><strong>제어 비트 (Flags)</strong>: 세그먼트의 부가 정보를 나타내는 8비트 필드.<ul>
<li><strong>SYN</strong>: 연결 수립을 위한 비트</li>
<li><strong>ACK</strong>: 확인 응답을 나타내는 비트</li>
<li><strong>FIN</strong>: 연결 종료를 위한 비트<img src="https://velog.velcdn.com/images/kdhun-0814/post/358ce847-2bac-4b96-ab4c-06d845c7854a/image.png" /></li>
</ul>
</li>
<li><strong>윈도우 (Window)</strong>: 수신 윈도우 크기(한 번에 수신하고자 하는 데이터 양)를 명시하여 흐름 제어에 사용.</li>
</ul>
<h4 id="연결-수립-3-way-handshake">연결 수립: 3-way Handshake</h4>
<p>TCP는 3단계로 이루어진 '3-way handshake'를 통해 연결을 수립.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/8422318c-e4b1-4300-9acd-054426bde804/image.png" />
<img src="https://velog.velcdn.com/images/kdhun-0814/post/20e3adf7-b554-490c-aec0-590b8df0debb/image.png" /></p>
<h4 id="연결-종료-4-way-handshake">연결 종료: 4-way Handshake</h4>
<p>연결 종료는 각 호스트가 한 번씩 <code>FIN</code>과 <code>ACK</code>를 주고받는 과정으로, '4-way handshake'라고도 함.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/0bd8ad05-24fc-4716-abd2-b98e7d11a4d4/image.png" />
<img src="https://velog.velcdn.com/images/kdhun-0814/post/e7f68831-3bdf-4969-9a71-3214efa11a56/image.png" /></p>
<hr />
<h3 id="tcp의-상태-state">TCP의 상태 (State)</h3>
<p>TCP는 <strong>스테이트풀(Stateful) 프로토콜</strong>로서, 통신 과정의 각 단계를 상태로 관리. 이를 통해 연결의 신뢰성을 유지하고 데이터 흐름을 제어.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/d7d01034-1b99-438a-8aa8-7746a84f3ebe/image.png" /></p>
<p>주요 TCP 상태는 다음과 같습니다.</p>
<ul>
<li><strong>연결 수립 전</strong>: <code>CLOSED</code> (연결이 없는 상태), <code>LISTEN</code> (연결 대기 상태)</li>
<li><strong>연결 수립 중</strong>: <code>SYN_SENT</code> (연결 요청을 보낸 후 대기), <code>SYN_RECEIVED</code> (요청을 받은 후 응답을 보낸 상태)</li>
<li><strong>연결 확립</strong>: <code>ESTABLISHED</code> (연결이 확립되어 데이터 송수신이 가능한 상태)</li>
<li><strong>연결 종료 중</strong>: <code>FIN_WAIT_1</code>, <code>CLOSE_WAIT</code>, <code>FIN_WAIT_2</code>, <code>LAST_ACK</code>, <code>TIME_WAIT</code> 등 (연결 종료 과정의 세부 상태)<img src="https://velog.velcdn.com/images/kdhun-0814/post/32457b1d-3d14-4820-8b05-4b3203ed9873/image.png" />

</li>
</ul>
<hr />
<h3 id="udp-user-datagram-protocol">UDP (User Datagram Protocol)</h3>
<p>UDP는 TCP와 달리 비연결형, 비신뢰성 프로토콜이므로 연결 수립 및 해제, 재전송 등의 기능을 수행하지 않는다. 따라서 상태를 유지하지 않는 <strong>스테이트리스(Stateless)</strong> 형태. TCP에 비해 오버헤드가 적어 패킷을 빠르게 처리하며, 실시간 통신(스트리밍, 인터넷 전화 등)에 주로 사용.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/8ae7766f-bef5-4bef-9893-9f180419d1ae/image.png" /></p>
<hr />
<h3 id="tcp와-udp의-차이점">TCP와 UDP의 차이점</h3>
<img src="https://velog.velcdn.com/images/kdhun-0814/post/1094f5c0-8d10-4a60-999a-e328e1be20db/image.png" />