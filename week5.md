패키지(Package)

패키지란 서로 관련 있는 클래스나 인터페이스의 컴파일된 클래스 파일들을 한 곳에 묶어 놓은 것이다. 그러므로 패키지는 디렉터리와 연관되는데, 하나의 패키지는 관련된 클래스 파일들이 들어 있는 디렉터리로 보면된다.

모듈(Module)

자바는 개발자들에게 많은 클래스들을 패키지 형태로 제공하는데, JDK 9부터는 패키지들을 모듈이라는 단위로 묶어, 100개에 가까운 모듈을 제공한다.
모듈은 Java 9에서 처음 도입된 개념으로, 패키지는 서로 관련 있는 클래스나 인터페이스의 컴파일된 파일들을 한 곳에 담는 컨테이너이고, 모듈은 패키지들을 담는 컨테이너로 모듈 파일로 저장한다.

import문

<pre><code>
1. 다음과 같이 클래스마다 경로명을 알려줄 수 있다.
import 패키지.클래스; // 클래스의 경로명을 컴파일러에게 알려주는 문 

2. 한 패키지에 있는 여러 클래스를 import 하고자 하는 경우, 다음과 같이 *를 사용하여 한번에 선언할 수 있다.
import 패키지.*;
</pre></code>

패키지 선언 

자바소스파일이 컴파일되어 생기는 클래스 파일은 반드시 패키지에 소속되어야 한다. 클래스가 소속될 패키지명은 다음과 같이 package 키워드를 이용하여 소스 파일의 첫 줄에 선언한다.
<pre><code>
package 패키지명;
</pre></code>

패키지의 특징
- 패키지 계층 구조 <br>
JDK 패키지 역시 디렌터리 계층 구조로 만들어진다. 클래스 파일들을 분류하여 패키지 계층 구조로 만들면 좋을 것이다. 상속 관계에 있는 클래스나 인터페이스의 경우, 서브 클래스 파일을 슈퍼 클래스 파일에 저장된 패키지의 서브 디렉터리에 패키지를 만들어 저장하여 계층화시키면 더욱 관리하기 쉽다.

- 패키지별 접근 제한 <br>
디폴트(default) 접근 지정으로 선언된 클래스나 멤버는 동일 패키지 내의 클래스들이 자유롭게 접근하도록 허용한다. 패키지에 포함된 클래스들끼리는 자유롭게 접근하게 하고, 다른 패키지의 클래스들은 접근을 막음으로써 패키지를 접근 권한의 범위로도 이용할 수 있다.

- 동일한 이름의 클래스를 다른 패키지에 작성 가능 <br>
같은 패키지 내에서는 동일한 이름을 가진 클래스나 인터페이스가 존재할 수 없다. 그러나 다른 패키지에서 가능하다. 클래스 이름은 패키지명을 포함한 전체 경로명을 사용하기 때문이다. 이것은 파일 시스템이 같은 이름을 가진 파일이 다른 디렉터리에 있으면 서로 다른 파일로 인지하는 것과 같다.

- 소프트웨어의 높은 재사용성 <br>
클래스와 인터페이스를 잘 분류하여 패키지로 관리하면, 나중에 같거나 유사한 기능을 수행하는 클래스나 인터페이스는 재작성할 필요 없이 프로그램에 포함하여 쉽게 사용할 수 있다. 

주요 패키지 
- Java.lang <br>
이 패키지에는 System을 비롯하여 문자열, 수학 함수, 입출력 등과 같이 자바 프로그래밍에 필요한 기본적인 클래스와 인터페이스를 제공한다. 이 패키지의 클래스들은 특히 import문을 사용하지 않아도 자동으로 임포트된다.

- Java.util <br>
날짜, 시간, 벡터, 해시맵 등 다양한 유틸리티 클래스와 인터페이스를 제공한다.

- Java.io <br>
키보드, 모니터, 프린터, 파일 등에 입출력 하는 클래스와 인터페이스를 제공한다.

- Java.awt 와 Javax.swing <br>
자바 AWT(Abstract Windowing Toolkit)와 swing패키지로서 GUI 프로그래밍에 필요한 클래스와 인터페이스를 제공한다. 

Object 클래스 

Object는 java.lang패키지에 속한 클래스이며, 모든 클래스에 강제로 상속된다. Object 만이 아무 클래스도 상속받지 않는 유일한 클래스로 계층 구조 상 최상위 클래스이다. 그러므로 Object 클래스에는 모든 클래스에서 상속받아 사용할 공통 기능이 구현되어 있다.

Object 생성 

<pre><code>
Object obj = new Object();
</pre></code>

Object 클래스의 주요 메소드 
<pre><code>
booleam equals(Object obj) : obj가 가리키는 객체와 현재 객체를 비교하여 같으면 true리턴
Class getClass() : 현 객체의 런타임 클래스를 리턴
int hashCode() : 현 객체에 대한 해시 코드 값 리턴
String toString() : 현 객체에 대한 문자열 표현을 리턴
void notify() : 현 객체에 대해 대기하고 있는 하나의 스레드를 깨운다.
void notifyAll() : 현 객체에 대해 대기하고 있는 모든 스레드를 깨운다.
void wait() : 다른 스레드가 깨울 때까지 현재 스레드를 대기하게 한다.
</pre></code>

ex)
<pre><code>
class Point {
  private int x,y; 
  public Point(int x,int y) {
      this.x = x;
      this.y = y;
  }
}

public class ObjectPropertyEx {
  public static void print(Object obj) {
    System.out.println(obj.getClass().getName());  // 클래스 이름 
    System.out.println(obj.hashCode()); // 해시 코드 값
    System.out.println(obj.toString()); // 객체를 문자열로 만들어 출력 
    System.out.println(obj); // 객체 출력
  }
  
  public static void main(String[] args) {
    Point p = new Point(2,3);
    print(p);
  }
}
</pre></code>

getClass()

Class 클래스는 주어진 객체의 클래스에 관한 정보를 담는 클래스이다. Object의 getClass() 메소드를 호출하면 바로 이 Class 객체를 리턴하는데, 다음과 같이 Class객체의 getName() 메소드를 이용하면 obj 레퍼런스가 가리키는 객체의 클래스 타입을 알아 낼수있다.

<pre><code>
System.out.println(obj.getClass().getName());
</pre></code>

hashCode()

객체는 생성될 때 객체를 유일하게 구분할 수 있는 정수 id 값이 할당된다. 이 값을 해시코드라고 부르고, Object의 hashCode() 메소드는 객체 안에 담겨진 해시코드 값을 리턴한다.

toString()

Object의 toString()은 객체를 문자열로 변환하여 리턴하는 메소드이다. 

<pre><code>
Point a = new Point(2,3);
System.out.println(a.toString());

클래스에 toString() 만들기
public String toString(); // public으로 선언해야 함에 특히 주의
</pre></code>

== 연산자 

ex)

<pre><code>
Point a = new Point(2,3);
Point a = new Point(2,3);
Point c = a; 
if(a == b) // false 
        System.out.println("a == b");
if(a == c) // true
        System.out.println("a == c");
</pre></code>

boolean equals(Object obj)

ex)

<pre><code>
String a = new String("Hello");
String b = new String("Hello");
if(a == b) // false
  System.out.println("a == b");
if(a.equals(b)) // true
  System.out.println("a와 b는 둘 다 Hello입니다.");
</pre></code>

Wrapper 클래스

int, char, double 등 8개의 기본 타입을 객체로 다루기 위해 JDK에 만들어진 8개 클래스를 통칭하여 Wrapper 클래스라한다. Byte, short, Integet, Long, Character, Double, Float, Boolean 클래스가 기본 타입에 해당되는 값을 객체로 다룰 수 있게 하는 Wrapper클래스이다. Wrapper 클래스들은 java.lang패키지에서 제공한다.

Wrapper 클래스의 객체 생성
<pre><code>
Integer i = Integer.valueOf(10);  // 정수 10개의 객체화
Character c = Character.valueOf('c');  // 문자 'c'의 객체화 
Double d = Double.valueOf(3.14);
Boolean b = Boolean.valueOf(true);
</pre></code>

Wrapper 클래스의 활용 
<pre><code>
static int bitCount(int i) : 정수 i의 이진수 표현에서  1의 개수 리턴 
float flatValue() : float 타입으로 값 리턴 
int intValue() : int 타입으로 값 리턴
long longValue() : long 타입으로 값 리턴
short shortValue() : short 타입으로 값 리턴 
static int parseInt(String s) : 문자열 s를 10진 정수로 변환한 값 리턴
static int parseInt(String s, int radix) : 문자열 s를 지정된 진법의 정수로 변환한 값 리턴
static String toBinaryString(int i) : 정수 i를 이진수 표현으로 변환한 문자열 리턴
static String toHexString(int i) : 정수 i를 16진수 표현으로 변환한 문자열 리턴
static String toOctalString(int i) : 정수 i를 8진수 표현으로 변환한 문자열 리턴
static String toString(int i) : 정수 i를 문자열로 변환하여 리턴
static Integer ValueOf(int i) : 정수 i를 담은 Integer 객체 리턴
static Integer valueOf(String s) : 문자열 s를 정수로 변환하여 담고 있는 Integer 객체 리턴 
</pre></code>

Wrapper 객체에 들어 있는 기본 타입 값 알아내기 

<pre><code>
Integer i = Integer.valueOf(10);
int ii = i.intValue(); // ii = 10

Double d = Double.valueOf(3.14);
double dd = d.doubleValue(); // dd = 3.14

Boolean b = Boolean.valueOf(true);
boolean bb = b.booleanValue(); // bb = true
</pre></code>

문자열을 기본 타입으로 변환 

<pre><code>
int i = Integer.parseInt("123")  // i = 123
boolean b = Boolean.parseBoolean("true");  // b = true
double d = Double.parseDouble("3.14");  // d = 3.14
</pre></code>

parseInt(), parseBoolean(), parseDouble() 메소드는 모두 static 타입이므로 Wrapper 클래스의 이름으로 바로 메소드를 호출한다.

박싱(boxing)

박싱은 int나 float같은 값을 객체 안에 넣어주는 일이다.

언박싱(unboxing)

언박싱은 이렇게 넣었던 int나 float값을 다시 빼내는 일을 뜻한다.

자동 박싱(auto boxing)

자동 박싱은 Java 컴파일러가 기본 유형과 해당 객체 래퍼 클래스간에 수행하는 자동 변환이다.  

자동 언박싱(auto unboxing)

자동 언박싱은 래퍼 클래스 객체를 다시 원시 유형으로 변환하는 자동 박싱과 반대이다. 이것은 JVM에 의해 자동으로 수행되므로 특정 작업에 래퍼 클래스를 사용한 다음 기본 형식으로 인해 처리 속도가 빨라지므로 기본 형식으로 다시 변환 할 수 있다.

<pre><code>
Integer ten = 10; // 자동 박싱. Integer ten = Integer.valueOf(10); 로 자동 처리된다.
int n = ten;  // 자동 언박싱. int n = ten.intValue();로 자동처리된다.
</pre></code>

String 클래스

java.lang 패키지에 포함된 클래스로서 String 클래스는 문자열을 나타낸다.  스트링 리터럴은 자바 컴파일러에 의해 모두 String 객체로 처리된다.

<pre><code>
String str1 = "abcd"; // String 스트링 리터럴로 String 객체 생성 

char data[] = {'a','b','c','d'}; // String 클래스의 생성자를 이용하여 String 객체 생성
String str2 = new String(data);
String str3 = new String("abcd"); // str2와 str3은 모두 "abcd" 문자열 
</pre></code>

생성자 

<pre><code>
String() : 빈 스트링 객체 생성
String(char[] value) : char 배열에 있는 문자열을 스트링 객체로 생성
String(String original) : 매개변수로 주어진 문자열과 동일한 스트링 객체 생성
String(StringBuffer buffer) : 매개변수로 주어진 스트링 버퍼의 문자열을 스트링 객체로 생성 
</pre></code>

스트링 리터럴

스트링 리터럴은 자바 내부에서 리터럴 테이블로 특별히 관리하여, 동일한 리터럴을 공유시킨다.

new String() 

new String()으로 생성된 스트링은 new를 이용하여 생성되는 다른 객체와 동일하게 힙 메모리에 생성된다. 

스트링 객체는 수정이 불가능하다. 

<pre><code>
String s = new String("Hello");
String t = s.concat("Java"); // 스트링s에 "Java" 를 덧붙인 새로운 스트링 객체 리턴 
</pre></code>

String 활용 

<pre><code>
char charAt(int index) : index 인덱스에 있는 문자 값 리턴 
int codePointAt(int index) : index 인덱스에 있는 유니코드  값 리턴 
int compareTo(String anotherString) : 두 스트링을 사전 순으로 비교하여 두 스트링이 같으면, 0 현 스트링이 anotherString보다 먼저 나오면 음수, 아니면 양수 리턴
String concat(String str) : 현재 스트링 뒤에 str 스트링을 덧붙인 새로운 스트링 리턴
boolean contains(CharSequence s) : s에 지정된 문자들을 포함하고 있으면 true 리턴 
int length() : 스트링의 길이 리턴
String replace(Charsequence target, Charsequence replacement) : target이 지정하는 일련의 문자들을 replacement가 지정하는 문자들로 변경한 스트링 리턴 
String[]split(String regex) : 정규식 regex에 일치하는 부분을 중심으로 스트링을 분리하고, 분리된 스트링들을 배열로 저장하여 리턴 
String subString(int beginIndex) : beginIndex 인덱스 부터  시작하는 서브 스트링 리턴
String toLowerCase() : 소문자로 변경한 스트링 리턴 
String toUpperCase() : 대문자로 변경한 스트링 리턴 
String trim() : 스트링 앞뒤의 공백 문자들을 제거한 스트링 리턴 
</pre></code>

ex)

문자열 비교 int compareTo(String anotherString)

<pre><code>
String java = "Java";
String cpp = "C++";
int res = java.compareTo(cpp);
if(res == 0)
      System.out.println("the same");
else if(res < 0)
      System.out.println(java + "<" + cpp);
else 
      System.out.println(java + ">" + cpp);
</pre></code>

문자열 연결 String concat(String str)

<pre><code>
System.out.print("abcd" + 1 + true + 3.13e^-2 + 'E' + "fgh");
"I love".concat("Java");
</pre></code>

공백 제거 String trim()

<pre><code>
String a ="  abcd    def   ";
String b ="   xyz\t";
String c = a.trim(); // c = "abcd   def". 문자열 중간에 있는 공백은 제거되지 않음
String d = b.trim(); // d = "xyz" . 스페이스와 '\t' 제거됨
</pre></code>

문자열의 문자 char charAt(int index)

<pre><code>
String a = "class";
char c = a.charAt(2); // c = 'a'
</pre></code>

StringBuffer 클래스

StringBuffer 클래스도 java.lang 패키지에 포함되어 있으며, String 클래스와 같이 문자열을 다룬다. String 객체의 경우 내부의 문자열을 수정할 수 없지만, StringBuffer 객체는 문자열을 저장하는 가변 버퍼를 가지고 있기 때문에 저장된 문자열의 수정이 가능하다.

ex)

<pre><code>
StringBuffer sb = new StringBuffer("java");
</pre></code>

StringBuffer 클래스 생성자

<pre><code>
StringBuffer() : 초기 버퍼의 크기가 16인 스트링 버퍼 객체 생성 
StringBuffer(charSequence seq) : seq가 지정하는 일련의 문자들을 포함하는 스트링 버퍼 생성 
StringBuffer(int capacity) : 지정된 초기 크기를 갖는 스트링 버퍼 객체 생성 
StringBuffer(String str) : 지정된 스트링으로 초기화된 스트링 버퍼 객체 생성 
</pre></code>

StringBuffer의 활용 

<pre><code>
StringBuffer append(String str) : str 스트링을 스트링 버퍼에 덧붙인다.
StringBuffer append(StringBuffer sb) : sb 스트링 버퍼를 현재의 스트링 버퍼에 덧붙인다. 이 결과 현재 스트링 버퍼의 내용이 변한다
int capacity() : 스트링 버퍼의 현재 크기 리턴
StringBuffer delete(int start, int end) : start 위치에서 end 위치 앞까지 부분 문자열 삭제 
StringBuffer insert(int offset, String str) : str 스트링을 스트링 버퍼의 offset 위치에 삽입
StringBuffer replace(int start, in end, String str) : 스트링 버퍼 내의 start 위치의 문자부터 end가 지정하는 문자 앞의 서브 스트링을 str로 대치
StringBuffer reverse() : 스트링 버퍼 내의 문자들을 반대 순서로 변경 
void setLength(int newLength) : 스트링 버퍼 내 문자열 길이를 newLength로 재설정, 현재 길이보다 큰 경우 널 문자('')로 채우며 작은 경우는 기존 문자열이 잘린다.
</pre></code>

StringTokenizer 클래스 
- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
