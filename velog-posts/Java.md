<h2 id="자바의-기본구조">자바의 기본구조</h2>
<blockquote>
<hr />
<pre><code class="language-java">/* 클래스 블록 */
public class 클래스명 {

   /* 메서드 블록 */
    [public|private|protected] [static] (리턴자료형|void) 메서드명1(입력자료형 매개변수, ...) {
        명령문(statement);
        ...
    }

   /* 메서드 블록 */
    [public|private|protected] [static] (리턴자료형|void) 메서드명2(입력자료형 매개변수, ...) {
        명령문(statement);
        ...
    }
</code></pre>
</blockquote>
<pre><code>...</code></pre><p>}</p>
<pre><code>- - -

**클래스 블록**
public은 자바의 접근제어자로 누구나 다 접근 가능하다는 의미다
클래스는 하나의 **객체**로 선언이 된다.
```java
pulic class TestJava{

}
</code></pre><p><strong>메서드 블록</strong></p>
<pre><code class="language-java"> (public|private|protected) static void MethodJava(int ex, ...) {
        int k=ex;
        ...
    }

}
</code></pre>
<p>메서드 블록은 클래스 블록 안에 있으면 {}(중괄호)로 영역을 구분한다.</p>
<p>public , private , protected은 접근의 허용성을 의미한다.</p>
<p>static : 클래스를 만들지 않아도 '클래스명.매서드명'으로 호출이 가능하다</p>
<p>void : 메서드의 리턴 자료형으로 void는 리턴값이 없음을 의미한다.</p>
<p>String[] args: 메서드의 매개 변수로 , args변수는 String[]배열 자료형임을 의미한다.args는 
argument의 줄임말로, 인수를 의미한다.args대신 다른 이름을 사용해도 상관없다.</p>
<p> <strong>실행문</strong>
실행문 구절에는 반드시 세미콜론(;)을 붙여야 한다.
<img alt="" src="https://velog.velcdn.com/images/kdhun-0814/post/6b920ef0-5dc7-4b15-b519-74c32c200d53/image.png" /></p>
<p>ex)<a href="https://wikidocs.net/191">https://wikidocs.net/191</a> (참고 문헌 :점프투자바)</p>
<hr />