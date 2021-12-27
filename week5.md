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


- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
