<p>알겠다. 요청한 대로 보내준 내용에서 이미지 링크로 추정되는 것들을 모두 살려서 다시 정리해 준다.</p>
<hr />
<h2 id="ip의-핵심-기능">IP의 핵심 기능</h2>
<p>IP 프로토콜의 두 가지 공식적인 기능은 <strong>주소 지정</strong>과 <strong>단편화</strong>이다.</p>
<ul>
<li><p><strong>주소 지정 (IP Addressing)</strong>
: IP 주소를 바탕으로 송신지와 수신지 대상을 지정하는 것을 의미한다.</p>
</li>
<li><p><strong>단편화 (IP Fragmentation)</strong>
: 전송하려는 패킷의 크기를 MTU(Maximum Transmission Unit) 이하의 여러 패킷으로 나누는 것을 말한다. MTU는 한 번에 전송 가능한 IP 패킷의 최대 크기이다.</p>
<img src="https://velog.velcdn.com/images/kdhun-0814/post/d9b361da-983b-4856-8917-0daa645d615a/image.png" width="500" />

</li>
</ul>
<p>단편화는 불필요한 트래픽을 늘리고 대역폭을 낭비하기 때문에, 가급적 피하는 것이 좋다. 쪼개진 패킷들을 하나로 합치는 과정에서 발생하는 부하도 성능 저하의 원인이다.</p>
<h3 id="ip-단편화-피하기">IP 단편화 피하기</h3>
<p>IP 단편화 없이 주고받을 수 있는 최대 크기인 **경로 MTU(Path MTU)**만큼의 데이터만 전송해야 한다. 이를 **경로 MTU 발견 (Path MTU Discovery)**이라 부르며, 이 과정을 통해 단편화를 회피한다.</p>
<p>실제로 대부분의 네트워크에서는 <strong>DF (Don't Fragment) 비트</strong>가 설정되어 있어서 단편화가 자주 일어나지 않는다.</p>
<hr />
<h3 id="ip-주소의-구조와-클래스">IP 주소의 구조와 클래스</h3>
<p>IP 주소는 크게 <strong>네트워크 주소</strong>와 <strong>호스트 주소</strong>로 구성된다.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/8e347443-8ad1-472a-beeb-1371534fdf0f/image.png" /></p>
<ul>
<li><strong>네트워크 주소:</strong> 호스트가 속한 특정 네트워크를 식별하는 부분이다.</li>
<li><strong>호스트 주소:</strong> 네트워크 내에서 특정 호스트를 식별하는 부분이다.</li>
</ul>
<p>IP 주소는 총 32비트로 이루어져 있으며, 네트워크 주소와 호스트 주소의 크기는 달라질 수 있다.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/edfc8c8a-fac7-431f-8c2a-f4ce4d2440f2/image.png" width="500" />
<img src="https://velog.velcdn.com/images/kdhun-0814/post/d2af3098-9907-408e-94fa-c70e80707f29/image.png" width="500" /></p>
<p>네트워크의 크기에 따라 IP 주소를 분류하는 기준이 바로 **클래스(Class)**이다.</p>
<ul>
<li><strong>클래스풀 주소체계 (Classful Addressing)</strong>
: 클래스를 기반으로 IP 주소를 관리하는 방식이다. 필요한 호스트 수에 따라 클래스를 선택하여 네트워크 크기를 조절할 수 있다.<img src="https://velog.velcdn.com/images/kdhun-0814/post/d0c6f8bd-c266-41a5-a17e-f8983e5fda99/image.png" />
  * **A 클래스:** 첫 비트가 `0`으로 시작하는 1옥텟이 네트워크 주소, 나머지 3옥텟이 호스트 주소다. 호스트 수가 가장 많다.
<img src="https://velog.velcdn.com/images/kdhun-0814/post/73af9f33-0010-4f2a-b267-b59fb7e0076e/image.png" />
  * **B 클래스:** 첫 비트가 `10`으로 시작하는 2옥텟이 네트워크 주소, 나머지 2옥텟이 호스트 주소다.
    <img src="https://velog.velcdn.com/images/kdhun-0814/post/6f5798fb-a273-4514-9f95-e35ef5cac266/image.png" />
  * **C 클래스:** 첫 비트가 `110`으로 시작하는 3옥텟이 네트워크 주소, 나머지 1옥텟이 호스트 주소다. 호스트 수가 가장 적다.
    <img src="https://velog.velcdn.com/images/kdhun-0814/post/3e57a225-ce8c-4276-9552-9915cb8b0aac/image.png" />
  * **주의:** 호스트 주소가 모두 0이면 **네트워크 주소**, 모두 1이면 **브로드캐스트 주소**로 사용되므로, 할당 가능한 호스트 수는 2개 부족하다.
    <img src="https://velog.velcdn.com/images/kdhun-0814/post/eb97319b-f405-4a35-9c24-42c23be70914/image.png" />
    <img src="https://velog.velcdn.com/images/kdhun-0814/post/021d7534-5b64-4d0a-a4b5-2fcfbfd59865/image.png" />

</li>
</ul>
<hr />
<h3 id="클래스풀-주소체계의-한계와-해결책">클래스풀 주소체계의 한계와 해결책</h3>
<p>클래스풀 주소체계는 정해진 크기만 허용해서 IP 주소 낭비가 심하고, 유연한 네트워크 구성이 불가능하다는 한계가 있다.</p>
<ul>
<li><strong>해결책:</strong> <strong>클래스리스 주소체계 (Classless Addressing)</strong>
: 클래스 개념에 얽매이지 않고 네트워크의 영역을 자유롭게 나누고 IP 주소를 할당하는 방식이다. 이 방식을 사용하면 더 유동적이고 정교한 네트워크 구획이 가능하다.<ul>
<li><strong>서브넷 마스크 (Subnet Mask):</strong> 클래스 없이 네트워크 주소와 호스트 주소를 구분하는 수단이다. 네트워크 주소 부분은 <code>1</code>로, 호스트 주소 부분은 <code>0</code>으로 표기한 비트열이다.<img src="https://velog.velcdn.com/images/kdhun-0814/post/e55290d6-e014-4bdd-8c38-8381d11fff02/image.png" /></li>
<li><strong>서브네팅 (Subnetting):</strong> 서브넷 마스크를 이용해서 네트워크를 더 작은 단위로 쪼개어 사용하는 것을 말한다.</li>
<li><strong>네트워크 주소 계산:</strong> IP 주소와 서브넷 마스크를 <strong>비트 AND 연산</strong>하면 네트워크 주소를 구할 수 있다.<img src="https://velog.velcdn.com/images/kdhun-0814/post/271bb9aa-2cd2-4e8f-a54b-cff199515c85/image.png" />
<img src="https://velog.velcdn.com/images/kdhun-0814/post/d788b6b8-3abe-4729-9c9b-6d3839ecee83/image.png" />
<img src="https://velog.velcdn.com/images/kdhun-0814/post/ba745f44-e8ef-4188-ac18-95cc413086c9/image.png" /></li>
<li><strong>CIDR 표기법:</strong> 서브넷 마스크를 더 간결하게 나타내는 방법이다. IP 주소 뒤에 <code>/</code>와 서브넷 마스크의 비트 1의 개수를 표기한다.<img src="https://velog.velcdn.com/images/kdhun-0814/post/2ca865b2-eb9a-4c34-81e0-0f69cfa3f5fd/image.png" />

</li>
</ul>
</li>
</ul>
<hr />
<h3 id="예약된-ip-주소">예약된 IP 주소</h3>
<p>특수한 목적을 위해 예약된 IP 주소들이 있다.</p>
<ul>
<li><strong>127.0.0.1 (루프백 주소, localhost):</strong> 자기 자신을 가리키는 특별한 주소다. 패킷이 이 주소로 전송되면 자기 자신에게 되돌아온다. 주로 테스트나 디버깅 용도로 사용한다.</li>
<li><strong>0.0.0.0:</strong><ul>
<li><strong><code>0.0.0.0/8</code>:</strong> 호스트가 IP 주소를 할당받기 전에 임시로 할당되는 주소이다.</li>
<li><strong><code>0.0.0.0/0</code>:</strong> '모든 임의의 IP 주소'를 의미한다. 주로 라우팅에서 어떤 IP 주소로 보낼지 결정하기 어려울 때 사용하는 기본 경로인 <strong>디폴트 라우트</strong>를 나타낸다.</li>
</ul>
</li>
</ul>