<h2 id="제어문">제어문</h2>
<h3 id="조건문">조건문</h3>
<blockquote>
<p>if 문
만약 어떠한 조건이 갖춰졌을때만 문잘을 실행시키고싶을때</p>
</blockquote>
<pre><code class="language-java">int score = 85;
if (score &gt;= 90) {
    System.out.println(&quot;A&quot;);
} else if (score &gt;= 80) {
    System.out.println(&quot;B&quot;);
} else {
    System.out.println(&quot;C or 낙제&quot;);
}</code></pre>
<blockquote>
<p>switch 문
조건식의 값이 <strong>정수일때</strong> case 별로 실행문을 실행시킬수 있다</p>
</blockquote>
<pre><code class="language-java">int menu = 1;
switch(menu) {
    case 1: System.out.println(&quot;햄버거&quot;); break;
    case 2: System.out.println(&quot;피자&quot;); break;
    default: System.out.println(&quot;없는 메뉴&quot;);
}</code></pre>
<hr />
<h3 id="반복문">반복문</h3>
<blockquote>
<p>For문
for(시작값;반복구간;증감값)
for (int i =0 ; i&lt;100;i++){
(실행문)
}
:  i가 0 부터 99까지 한번씩 실행된후 i는 1씩 증가된다</p>
</blockquote>
<pre><code class="language-java">public class Example{
    public static void main(String[] args){
        int sum =0;
        for(int i=0;i&lt;100;i++){
                sum= sum+i;
        }
    }
} </code></pre>
<blockquote>
<p>while문
while(조건식){
    실행문
}
:조건식이 참일때 반복 false 일때 종료</p>
</blockquote>
<pre><code class="language-java">public class Example{
    public static void main(String[] args){
        int sum =0;
        while(i&lt;100){
        sum=sum+i;
        i++;
        }
    }
} </code></pre>
<blockquote>
<p>break문과 continue문
실행문의 실행문을 중지하거나 계속 이어나갈때 사용한다</p>
</blockquote>
<pre><code>public class Example{
    public static void main(String[] args){
        int sum =0;
        while(i&lt;100){
        sum=sum+i;
        i++;
        if(i==50){
        break;
        }
        }
    }
} </code></pre><pre><code>public class Example{
    public static void main(String[] args){
        for(int i=0;i&lt;=10;i++){
            if(i%2!=0){
            continue;
            }
            System.out.println(i);
        }
    }
} 
// 출력결과: 2,4,6,8,10</code></pre>