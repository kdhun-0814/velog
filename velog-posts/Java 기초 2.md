<h3 id="자바의-입출력">자바의 입출력</h3>
<p>자바의 입출력에는 크게 두가지가 있다</p>
<blockquote>
<p>Scanner class
Scanner 클래스는 입력받은 데이터(바이트)를 다양한 타입으로 변환하여 반환하는 클래스이다. 간단하게 기본형과 String 타입을 정규표현식을 사용해 파싱(parse)할 수 있다.</p>
</blockquote>
<p><strong><em>데이터를 입력받을 경우 즉시 사용자에게 전송되며 입력받을 때마다 전송되어야 하기에 많은 시간이 소요된다.
버퍼의 사이즈가 1024byte(1KB) 이다.
java.util 패키지에 속한다. (java.util.Scanner)</em></strong></p>
<pre><code class="language-java">import java.util.Scanner; 
public class ScannerInput {    
public static void main(String[] args) {
// scanner 선언        
Scanner sc = new Scanner(System.in);
int a =sc.nextLine();
int a =sc.nextInt();
double a = sc.nextDouble();
String a =sc.next();
String a =sc.nextString();</code></pre>
<hr />
<blockquote>
<p>BufferReader
<strong>버퍼란?</strong> : 데이터를 전송하기전에 임시저장소역할을 하는곳
데이터를 한번에 읽어와 버퍼에 보관한 후 버퍼에서 데이터를 읽어오는 방식으로 동작하는 클래스이다. 즉 사용자가 입력한 문자 스트림을 읽는 것(read) 라고 한다.</p>
</blockquote>
<p><strong>java.io 패키지에 속한다. (import java.io.BufferedReader)
데이터를 파싱하지 않고 String으로만 읽고 가져온다.
Scanner보다 소요되는 시간을 절약할 수 있다.</strong>
<strong>Checked Exception으로 반드시 예외 처리를 명시해야한다.(I/O Exception을 throw하거나 try/catch 해야한다.)</strong></p>
<pre><code class="language-java">import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
public static void main(String[] args) throws IOException {
  BufferReader br = new BufferedReader(InputStreamReader(System.in));
  String st = br.readLine();

  int a = Integer.parseInt(br.readLine());
  int b = Integer.parseInt(st);
}</code></pre>