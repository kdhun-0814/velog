<h2 id="string">String</h2>
<h3 id="대소문자-구분">대/소문자 구분</h3>
<blockquote>
<p>str.lower()/str.upper()</p>
</blockquote>
<pre><code class="language-py">url = &quot;HTTP://WIKIDOCS.NET&quot;
url.lower()
#'http://wikidocs.net'
#
#
url = 'http://wikidocs.net'
url.upper()
#&quot;HTTP://WIKIDOCS.NET&quot;</code></pre>
<hr />
<h3 id="문자열-이어붙이기">문자열 이어붙이기</h3>
<blockquote>
<p>str.join(list)</p>
</blockquote>
<pre><code class="language-py">li = ['A', 'B', 'C', 'D', 'E']
'-'.join(li)
'**'.join(li)
'  '.join(li)
''.join(li)
# A-B-C-D-E'
# 'A**B**C**D**E'
# 'A  B  C  D  E'
# 'ABCDE'</code></pre>
<hr />
<h3 id="치환교체">치환(교체)</h3>
<blockquote>
<p>str.replace(교체당할문자열,교체할 문자열)
str.replace(old,new, (n: 교체당할 문자열갯수))</p>
</blockquote>
<pre><code class="language-py">ex_str = '111222333'
ex_str.replace('1','4')
# 출력 =&gt;'444222333'
ex_str.replace('1','4', 1)
# 출력 =&gt;'411222333'</code></pre>
<hr />
<h3 id="문자열-나누기">문자열 나누기</h3>
<blockquote>
<p>str.split('기준을 나눌 문자열' )</p>
</blockquote>
<pre><code class="language-py">A = '1,2,3'.split(',')
# 출력 =&gt; ['1', '2', '3']
#len(A) = 3 </code></pre>
<hr />
<h3 id="문자열-제거-및-공백-제거">문자열 제거 및 공백 제거</h3>
<blockquote>
<p>str.strip()#공백제거
str.strip(&quot;제거할 문자&quot;)</p>
</blockquote>
<pre><code class="language-py">ex_str = &quot;                   hello         &quot;
ex_str.strip()
#출력 =&gt;  'hello'
www.example.com'.strip('m')
#출력 =&gt; 'www.example.co'
</code></pre>