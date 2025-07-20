<p><a href="https://school.programmers.co.kr/learn/courses/30/lessons/181867">프로그래머스 x사이의 개수</a>
프로그래머스 lv0
<strong>- 문제 설명</strong>
문자열 myString이 주어집니다. myString을 문자 &quot;x&quot;를 기준으로 나눴을 때 나눠진 문자열 각각의 길이를 순서대로 저장한 배열을 return 하는 solution 함수를 완성해 주세요.
<strong>제한사항</strong>
1 ≤ myString의 길이 ≤ 100,000
myString은 알파벳 소문자로 이루어진 문자열입니다.
입출력 예</p>
<hr />
<table>
<thead>
<tr>
<th align="left"><code>myString</code></th>
<th align="left"><code>result</code></th>
</tr>
</thead>
<tbody><tr>
<td align="left"><code>&quot;oxooxoxxox&quot;</code></td>
<td align="left"><code>[1, 2, 1, 0, 1, 0]</code></td>
</tr>
<tr>
<td align="left"><code>&quot;xabcxdefxghi&quot;</code></td>
<td align="left"><code>[0, 3, 3, 3]</code></td>
</tr>
</tbody></table>
<blockquote>
<p><strong>오답코드</strong></p>
</blockquote>
<pre><code class="language-java">import java.util.*;
class Solution {
    public int[] solution(String myString) {
      ** String[] str=myString.split(&quot;x&quot;);**
        ArrayList&lt;Integer&gt; answer2 = new ArrayList&lt;&gt;();
        int sum =0;
        for(int i =0;i&lt;str.length;i++){
               answer2.add(str[i].length());
        }
        int []answer =new int[answer2.size()];
        for(int i =0;i&lt;answer2.size();i++){
            answer[i]=answer2.get(i);
        }
        return answer;
    }
}
//[1, 2, 1, 0, 1]</code></pre>
<p>기본 로직으로 봤을때는 전혀 문제가 없는거 같은데 코드를 돌려보면 <strong>split(&quot;x&quot;)부분이 문자열끝에 빈문자열을 포함하지 않는다</strong>는 치명적인 단점이 있다.</p>
<hr />
<h3 id="splitstr">split(str)</h3>
<p><strong>선행/중간 빈 문자열 포함</strong>: 문자열 <strong>시작이나 중간</strong>에 구분자가 연속될 경우 발생하는 <strong>빈 문자열은 결과 배열에 포함</strong>.
<strong>후행 빈 문자열 포함 불가:</strong> 문자열 끝에 구분자가 있거나, 문자열이 구분자로 끝나는 경우 발생하는 후행 <strong>빈 문자열은 결과 배열에서 제거.</strong></p>
<h3 id="splitstr--1">split(str, -1)</h3>
<ul>
<li><strong>모든 빈 문자열 포함:</strong> 문자열 시작, 중간, 끝에 구분자가 연속되거나 문자열이 구분자로 끝날 경우 발생하는 <strong>모든 빈 문자열이 결과 배열에 포함</strong>.<blockquote>
<p>정답코드</p>
<pre><code class="language-java">import java.util.*;
class Solution {
  public int[] solution(String myString) {
    ** String[] str=myString.split(&quot;x&quot;,-1);**
      ArrayList&lt;Integer&gt; answer2 = new ArrayList&lt;&gt;();
      int sum =0;
      for(int i =0;i&lt;str.length;i++){
             answer2.add(str[i].length());
      }
      int []answer =new int[answer2.size()];
      for(int i =0;i&lt;answer2.size();i++){
          answer[i]=answer2.get(i);
      }
      return answer;
  }
}
//[1, 2, 1, 0, 1, 0]</code></pre>
</blockquote>
<pre><code></code></pre></li>
</ul>