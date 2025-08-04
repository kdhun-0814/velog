<p><img alt="" src="https://velog.velcdn.com/images/kdhun-0814/post/f5cd8f2f-34a3-4f89-a7ac-eec6debd0b7d/image.png" /></p>
<h2 id="jpa로-저장된-데이터를-db에서-직접-확인하기">JPA로 저장된 데이터를 DB에서 직접 확인하기</h2>
<p>이전 과정에서 JPA의 <code>Entity</code>와 <code>Repository</code>를 활용해 자바 객체를 DB에 저장했다. 이제 데이터가 실제로 DB에 어떻게 저장되고 관리되는지 직접 확인해 보자.</p>
<h3 id="1-db의-테이블-구조-이해하기">1. DB의 테이블 구조 이해하기</h3>
<p>자바에서 <code>Article</code> <code>Entity</code>를 사용해 데이터를 저장하면, DB에는 <code>articles</code>라는 **테이블(Table)**이 자동으로 생성된다. 이 테이블은 데이터를 체계적으로 관리하는 기본 단위다.</p>
<p>테이블은 **로우(Raw)**와 **컬럼(Column)**으로 구성된다.</p>
<ul>
<li><strong>컬럼(열):</strong> 데이터의 종류를 나타낸다. (예: <code>id</code>, <code>title</code>, <code>content</code>)</li>
<li><strong>로우(행):</strong> 실제 데이터 한 줄을 의미한다. (예: <code>1</code>, <code>&quot;제목1&quot;</code>, <code>&quot;내용1&quot;</code>)</li>
</ul>
<p>우리가 만든 <code>Article</code> 엔티티는 다음과 같은 구조의 테이블로 관리된다.</p>
<table>
<thead>
<tr>
<th align="left"><code>id</code></th>
<th align="left"><code>title</code></th>
<th align="left"><code>content</code></th>
</tr>
</thead>
<tbody><tr>
<td align="left"><code>1</code></td>
<td align="left"><code>&quot;제목1&quot;</code></td>
<td align="left"><code>&quot;내용1&quot;</code></td>
</tr>
<tr>
<td align="left"><code>2</code></td>
<td align="left"><code>&quot;제목2&quot;</code></td>
<td align="left"><code>&quot;내용2&quot;</code></td>
</tr>
<tr>
<td align="left"><code>...</code></td>
<td align="left"><code>...</code></td>
<td align="left"><code>...</code></td>
</tr>
</tbody></table>
<p>DB에 저장된 데이터는 SQL(Structured Query Language)이라는 언어를 통해 <strong>CRUD</strong> 처리가 가능하다.</p>
<ul>
<li><code>SELECT</code>: 데이터 <strong>조회(Read)</strong></li>
<li><code>INSERT</code>: 데이터 <strong>삽입(Create)</strong></li>
<li><code>UPDATE</code>: 데이터 <strong>수정(Update)</strong></li>
<li><code>DELETE</code>: 데이터 <strong>삭제(Delete)</strong></li>
</ul>
<hr />
<h3 id="2-h2-db-웹-콘솔-접속하기">2. H2 DB 웹 콘솔 접속하기</h3>
<p>우리는 개발용으로 적합한 인메모리(in-memory) 데이터베이스인 <strong>H2 DB</strong>를 사용한다. H2는 웹 브라우저에서 DB를 직접 조작할 수 있는 <strong>웹 콘솔</strong> 기능을 제공한다.</p>
<h4 id="21-h2-db-웹-콘솔-활성화">2.1. H2 DB 웹 콘솔 활성화</h4>
<p><code>src/main/resources/application.properties</code> 파일에 다음 설정을 추가하여 H2 웹 콘솔을 활성화한다.</p>
<pre><code class="language-properties"># H2 Console 활성화
spring.h2.console.enabled=true

# H2 DB 접속 주소 고정 (선택 사항, 개발 편의를 위함)
spring.datasource.url=jdbc:h2:mem:testdb</code></pre>
<blockquote>
<p><strong>참고:</strong> <code>spring.h2.console.enabled=true</code>를 설정하면 <code>localhost:8080/h2-console</code>로 접속할 수 있다. <code>spring.datasource.url</code>을 <code>jdbc:h2:mem:testdb</code>로 고정하면 애플리케이션을 재시작해도 DB 접속 주소가 바뀌지 않아 편리하다.</p>
</blockquote>
<h4 id="22-콘솔-접속-및-테이블-확인">2.2. 콘솔 접속 및 테이블 확인</h4>
<ol>
<li><p>스프링 부트 애플리케이션을 실행한다.</p>
</li>
<li><p>웹 브라우저를 열고 <code>http://localhost:8080/h2-console</code>에 접속한다.
<img alt="" src="https://velog.velcdn.com/images/kdhun-0814/post/3c824d4e-6106-4e37-87fa-b2bd1a73d33c/image.png" /></p>
</li>
<li><p><code>JDBC URL</code> 입력란에 <code>application.properties</code> 파일에 설정한 <code>spring.datasource.url</code> 값(<code>jdbc:h2:mem:testdb</code>)을 입력하고 <strong><code>Connect</code></strong> 버튼을 클릭한다.</p>
<ul>
<li>만약 URL을 고정하지 않았다면, IntelliJ IDEA의 콘솔 로그에서 <code>h2</code>로 검색하여 <code>jdbc:h2:mem:...</code> 형태의 URL을 복사해 사용한다.
![]
(<a href="https://velog.velcdn.com/images/kdhun-0814/post/c74d9762-4a99-453c-b492-4082fbb5e933/image.png">https://velog.velcdn.com/images/kdhun-0814/post/c74d9762-4a99-453c-b492-4082fbb5e933/image.png</a>)</li>
</ul>
</li>
<li><p>접속에 성공하면 좌측 상단에 테이블 목록이 보인다. <code>ARTICLE</code>이라는 테이블을 클릭해 보자.
<img alt="" src="https://velog.velcdn.com/images/kdhun-0814/post/34e80614-025f-41d8-9446-78f4b42b0883/image.png" /></p>
<ul>
<li><code>ARTICLE</code> 테이블에는 <code>ID</code>, <code>CONTENT</code>, <code>TITLE</code> 컬럼이 생성되어 있음을 확인할 수 있다. 이는 우리가 <code>Article</code> 엔티티에 정의한 필드들이 자동으로 테이블 컬럼으로 매핑되었기 때문이다.</li>
</ul>
</li>
</ol>
<h4 id="23-저장된-데이터-조회하기">2.3. 저장된 데이터 조회하기</h4>
<p><code>ARTICLE</code> 테이블을 클릭하면 자동으로 <code>SELECT * FROM ARTICLE;</code>이라는 SQL 쿼리문이 생성된다. 이 쿼리문을 실행하면 테이블의 모든 데이터를 조회할 수 있다.</p>
<blockquote>
<p><code>SELECT * FROM ARTICLE;</code>은 <code>ARTICLE</code> 테이블의 모든 컬럼(<code>*</code>)에 있는 모든 로우를 조회하라는 뜻이다.</p>
</blockquote>
<h4 id="24-웹-페이지에서-데이터-추가-후-확인">2.4. 웹 페이지에서 데이터 추가 후 확인</h4>
<ol>
<li>웹 브라우저에서 <code>http://localhost:8080/articles/new</code>로 접속하여 게시글 작성 폼을 연다.</li>
<li><code>제목</code>과 <code>내용</code>을 입력하고 <strong><code>Submit</code></strong> 버튼을 클릭하여 데이터를 서버로 전송한다.</li>
<li>다시 H2 콘솔 화면으로 돌아와 <code>SELECT * FROM ARTICLE;</code> 쿼리문을 <strong><code>Run</code></strong> 버튼으로 다시 실행해 보자.</li>
<li>방금 입력한 데이터가 새로운 로우로 추가된 것을 확인할 수 있다.</li>
</ol>
<hr />
<h3 id="3-h2-콘솔에서-직접-sql로-데이터-추가하기">3. H2 콘솔에서 직접 SQL로 데이터 추가하기</h3>
<p>개발 과정에서는 H2 콘솔을 통해 직접 SQL 명령어를 실행하여 데이터를 추가, 수정, 삭제하는 경우도 많다.</p>
<ol>
<li><p>H2 콘솔 화면에서 SQL 입력창에 다음 <code>INSERT</code> 쿼리문을 입력해 보자.</p>
<pre><code class="language-sql">INSERT INTO article(id, title, content) VALUES (3, '새로운 게시글', 'H2 콘솔에서 직접 추가한 데이터입니다.');</code></pre>
<blockquote>
<p><code>INSERT INTO article (...)</code>은 <code>article</code> 테이블의 지정된 컬럼에 데이터를 삽입하라는 의미다.</p>
</blockquote>
</li>
<li><p><strong><code>Run</code></strong> 버튼을 클릭하면, <code>Update count: 1</code>이라는 메시지가 출력된다. 이는 데이터 1건이 성공적으로 추가되었다는 뜻이다.</p>
</li>
<li><p><code>SELECT * FROM ARTICLE;</code> 쿼리문을 다시 실행해 보면, 방금 추가한 데이터가 포함된 테이블을 확인할 수 있다.
<img alt="" src="https://velog.velcdn.com/images/kdhun-0814/post/88aa2bc2-2429-4341-884b-3da10922ccfc/image.png" />
이렇게 H2 DB 콘솔을 통해 JPA가 자바 객체를 DB 테이블에 어떻게 저장하는지 직접 확인할 수 있으며, SQL 명령어를 통해 DB를 관리하는 방법을 알수 있다.</p>
</li>
</ol>