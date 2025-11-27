<hr />
<h3 id="📂-my_cse-git--github-연동-구축-리포트">📂 [MY_CSE] Git &amp; GitHub 연동 구축 리포트</h3>
<h4 id="1-저장소-초기화-및-재설정-repository-reset">1. 저장소 초기화 및 재설정 (Repository Reset)</h4>
<ul>
<li><strong>상황:</strong> 기존의 꼬인 설정과 연결 오류(<code>remote origin already exists</code>)를 해결하기 위해 완전 초기화를 진행했습니다.</li>
<li><strong>조치:</strong> 윈도우 데스크탑에서 <code>.git</code> 폴더를 강제 삭제하여 깃 기록을 백지화하고, <code>git init</code>으로 깨끗한 상태에서 다시 시작했습니다.</li>
<li><strong>결과:</strong> 엉켜있던 버전 관리 기록이 사라지고, <strong>깔끔한 'First Commit' 상태</strong>로 재탄생했습니다.</li>
</ul>
<h4 id="2-파일-필터링-설정-gitignore">2. 파일 필터링 설정 (.gitignore)</h4>
<ul>
<li><strong>목적:</strong> 프로젝트와 상관없는 시스템 파일(<code>DS_Store</code>, <code>Thumbs.db</code>)과 빌드 파일이 1,000개 이상 업로드되는 것을 방지.</li>
<li><strong>조치:</strong> 프로젝트 루트에 <code>.gitignore</code> 파일을 생성하여 <strong>Flutter, Python, Windows, macOS</strong> 관련 불필요한 파일들을 자동으로 무시하도록 설정했습니다.</li>
<li><strong>결과:</strong> <code>git add .</code>를 해도 <strong>진짜 필요한 소스코드 파일만</strong> 깔끔하게 올라갑니다.</li>
</ul>
<h4 id="3-운영체제-간-호환성-확보-windows-↔-mac">3. 운영체제 간 호환성 확보 (Windows ↔ Mac)</h4>
<ul>
<li><strong>이슈:</strong> 윈도우(CRLF)와 맥(LF)의 줄바꿈 문자 차이로 인해 코드를 수정하지 않아도 수정된 것으로 인식하는 문제.</li>
<li><strong>조치:</strong> Git이 자동으로 줄바꿈 형식을 변환해주도록 경고 메시지(<code>LF will be replaced by CRLF</code>)를 확인하고 그대로 진행하여 호환성을 확보했습니다.</li>
<li><strong>구조:</strong><ul>
<li><code>app/</code> 폴더: Flutter 앱 소스코드 (정상 업로드 됨)</li>
<li><code>ai_server/</code> 폴더: 빈 폴더 상태 (파일 생성 시 추적 시작됨)</li>
</ul>
</li>
</ul>
<h4 id="4-동기화-워크플로우-확립-the-golden-rule">4. 동기화 워크플로우 확립 (The Golden Rule)</h4>
<p>두 대의 컴퓨터(데스크탑/맥북)를 오가며 개발하기 위한 <strong>절대 규칙</strong>을 세웠습니다.</p>
<ol>
<li><strong>메인 기지(Windows):</strong> <code>git push</code>를 통해 코드를 깃허브(원격 저장소)에 업로드 완료.</li>
<li><strong>보조 기지(Mac):</strong> 기존 폴더를 삭제하고 <code>git clone</code>을 통해 윈도우의 최신 상태를 그대로 복제 예정.</li>
<li><strong>작업 루틴:</strong><ul>
<li>💻 <strong>개발 시작 전:</strong> <code>git pull</code> (무조건 서버의 최신 코드를 내 컴퓨터로 당겨오기)</li>
<li>⌨️ <strong>개발 진행:</strong> 코드 작성 및 수정</li>
<li>🚀 <strong>개발 종료 후:</strong> <code>git add .</code> → <code>git commit</code> → <code>git push</code> (내 작업을 서버에 저장하고 퇴근)</li>
</ul>
</li>
</ol>
<hr />
<p>네, <strong>&quot;완전 처음부터 끝까지&quot;</strong>, 메모장으로 파일을 만들어서 깃허브에 올리는 과정을 아주 상세하게 알려드릴게요.</p>
<p>이 과정은 <strong>새로운 프로젝트를 시작하는 정석 방법</strong>입니다. 천천히 따라 해보세요.</p>
<hr />
<h3 id="1단계-깃허브-홈페이지에서-창고-만들기">1단계: 깃허브 홈페이지에서 '창고' 만들기</h3>
<p>내 컴퓨터의 파일을 받아줄 인터넷상의 저장소(레포지토리)를 먼저 만들어야 합니다.</p>
<ol>
<li><a href="https://github.com/">GitHub</a> 로그인.</li>
<li>우측 상단 <code>+</code> 버튼 → <strong>New repository</strong> 클릭.</li>
<li><strong>Repository name</strong>에 원하는 이름 입력 (예: <code>Practice_Test</code>).</li>
<li>다른 건 건드리지 말고 맨 아래 <strong>Create repository</strong> 초록색 버튼 클릭.</li>
<li>생성된 화면에 나오는 <strong>HTTPS 주소</strong>를 복사해 둡니다.<ul>
<li>(예: <code>https://github.com/내아이디/Practice_Test.git</code>)</li>
</ul>
</li>
</ol>
<hr />
<h3 id="2단계-내-컴퓨터에-폴더-만들고-파일-작성하기-메모장">2단계: 내 컴퓨터에 폴더 만들고 파일 작성하기 (메모장)</h3>
<p>이제 윈도우 바탕화면에서 작업할 폴더를 만들고 코드를 짜봅시다.</p>
<ol>
<li><strong>바탕화면</strong> 빈 곳에 우클릭 → <strong>새로 만들기</strong> → <strong>폴더</strong>.<ul>
<li>폴더 이름: <code>Practice_Test</code> (깃허브 이름이랑 똑같이 하는 게 헷갈리지 않아요)</li>
</ul>
</li>
<li>**메모장(Notepad)**을 엽니다. (시작 메뉴에서 '메모장' 검색)</li>
<li>메모장에 아무 내용이나 적습니다. (예: Python 코드)<pre><code class="language-python">print(&quot;안녕하세요 깃허브!&quot;)
print(&quot;이것은 메모장으로 만든 코드입니다.&quot;)</code></pre>
</li>
<li><strong>저장하기 (가장 중요!)</strong>:<ul>
<li>메모장 왼쪽 상단 <strong>파일</strong> → <strong>다른 이름으로 저장</strong>.</li>
<li>저장 위치: 방금 바탕화면에 만든 <code>Practice_Test</code> 폴더 안으로 들어갑니다.</li>
<li>파일 이름: <code>main.py</code> (<strong>뒤에 .txt를 지우고 .py로 적어야 합니다</strong>)</li>
<li>파일 형식: <strong>모든 파일 (<em>.</em>)</strong> 로 변경.</li>
<li><strong>저장</strong> 버튼 클릭.</li>
</ul>
</li>
</ol>
<p><em>(이제 <code>Practice_Test</code> 폴더 안에 <code>main.py</code> 파일이 하나 생겼습니다.)</em></p>
<hr />
<h3 id="3단계-터미널-열고-명령-내리기">3단계: (터미널) 열고 명령 내리기</h3>
<p>이제 깃(Git)에게 &quot;이 폴더를 관리해 줘&quot;라고 명령할 차례입니다.</p>
<ol>
<li><p><strong>명령 프롬프트(CMD)</strong> 또는 <strong>PowerShell</strong>을 엽니다.</p>
</li>
<li><p>방금 만든 폴더로 이동합니다. (아래 명령어를 입력하고 엔터)</p>
<pre><code class="language-cmd">cd Desktop\Practice_Test</code></pre>
<p><em>(경로가 <code>C:\Users\사용자명\Desktop\Practice_Test&gt;</code> 로 바뀌었는지 확인하세요)</em></p>
</li>
<li><p><strong>Git 초기화 (시동 걸기)</strong></p>
<pre><code class="language-cmd">git init</code></pre>
<p><em>(&quot;Initialized empty Git repository...&quot; 메시지가 뜨면 성공)</em></p>
</li>
<li><p><strong>파일 장바구니에 담기</strong></p>
<pre><code class="language-cmd">git add .</code></pre>
<p><em>(아무 메시지도 안 뜨는 게 정상입니다. 묵묵히 담은 겁니다.)</em></p>
</li>
<li><p><strong>저장 기록 남기기 (커밋)</strong></p>
<pre><code class="language-cmd">git commit -m &quot;메모장으로 첫 파일 생성&quot;</code></pre>
<p><em>(&quot;1 file changed...&quot; 메시지가 뜨면 성공)</em></p>
</li>
<li><p><strong>기본 가지(Branch) 이름 설정</strong></p>
<pre><code class="language-cmd">git branch -M main</code></pre>
</li>
<li><p><strong>깃허브와 연결하기 (아까 복사한 주소 붙여넣기)</strong></p>
<pre><code class="language-cmd">git remote add origin https://github.com/본인아이디/Practice_Test.git</code></pre>
<p><em>(에러 메시지 없으면 성공)</em></p>
</li>
<li><p><strong>깃허브로 쏘기 (업로드)</strong></p>
<pre><code class="language-cmd">git push -u origin main</code></pre>
</li>
</ol>
<hr />