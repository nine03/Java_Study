상속 (Inheritance)

상속은 부모의 재산을 자식이 물려 받는 것이다. 하지만, 객체 지향언어에서 상속은 재산 상속이 아니라 부모의 생물학적 특성을 물려받는 유전에 가깝다.

객체 지향에서 상속은 부모 클래스에 만들어진 필드와 메소드를 자식 클래스가 물려받는 것이다. 상속 선언만 하면, 자식 클래스는 부모 클래스에 만들어진 필드와 메소드를 만들지 않고도 만든 것과 같은 효과를 얻는다.

상속은 클래스 사이의 상속이지 객체 사이의 상속이 아니라는 점이다. 자식 객체는 자식 클래스와 부모 클래스에 만들어진 모든 멤버를 가지고 생선된다.

- 클래스의 간결화 - 멤버의 중복 작성 불필요
- 클래스 관리 용이 - 클래스들의 계층적 분류
- 소프트웨어의 생산성 향상 - 클래스 재사용과 확장 용이

자바의 상속 선언

자바에서는 부모 클래스를 슈퍼 클래스(super class), 상속받는 자식 클래스를 서브 클래스(sub class)라고 부르며, 상속을 선언할 때 확장한다는 뜻을 가진 extends키워드를 사용한다.

<pre><code>
public class Person { // 슈퍼 클래스
    ...
}
public class Student extends Person { // 서브 클래스  Person을 상속받는 클래스 student선언
    ...
}
public class StudentWorker extends Student {
      // Student를 상속받는 클래스 StudentWorker 선언 
      ...
}
</pre></code>

상속과 객체 

<pre><code>
class Point {
  private int x,y; // 한점을 구성하는 x,y 좌표 
  public void set(int x, int y) {
    this.x = x;
    this.y = y;
    }
    public void showPoint() { // 점의 좌표 출력
    System.out.println("(" + x + ","+ y + ")");
    }
 }
 class ColorPoint extends Point { // Point를 상속받은 ColorPoint 선언
    private String color; // 점의 색
    public void setColor(String color) {
    this.color = color;
    }
    public void showColorPoint() { // 컬러 점의 좌표 출력
      System.out.print(color);
      showPoint(); // Point 클래스의 showPoint() 호출
    }
 }
 public class ColorPointEx {
    public static void main(String [] args) {
      Point p = new Point(); // Point 객체 생성
      p.set(1,2); // Point 클래스의 set() 호출
      p.showPoint();
      
      ColorPoint cp = new ColorPoint(); // ColorPoint 객체 생성
      cp.set(3,4); // Point 클래스의 set() 호출
      cp.setColot("red"); // ColorPoint 클래스의 setColor() 호출
      cp.showColorPoint(); // 컬러와 좌표 출력
    }
 }
</pre></code>

상속 선언 
<pre><code>
class ColorPoint extends Point  {
        ...
}
</pre></code>

서브 클래스 객체 생성 

<pre><code>
Point p = new Point();
ColorPoint cp = new ColorPoint(); // 서브 클래스 객체 생성 
</pre></code>

서브 클래스에서 슈퍼 클래스 멤버 접근 

서브 클래스는 슈퍼 클래스의 private 멤버를 제외하고 모든 멤버를 접근 할 수 있다.

자바 상속의 특징

- 자바에서는 클래스의 다중 상속을 지원하지 않는다.
자바는 클래스를 여러 개 상속받는 다중상속(multiple inheritance)을 지원하지 않는다. 그러므로 extends 다음에는 클래스 이름을 하나만 지정 할 수 있다.

- 자바에서는 상속 횟수에 제한을 두지 않는다.

- 자바에서 계층 구조의 최상위에 Object 클래스가 있다.

슈퍼클래스의 private 멤버

슈퍼 클래스의 멤버가 private으로 선언되면 서브 클래스를 포함하여 다른 어떤 클래스에서도 접근할 수 없다. private은 오직 현재 클래스의 멤버들에게만 접근을 허용한다.

슈퍼클래스의 디폴트 멤버

슈퍼 클래스의 멤버가 디폴트로 선언되면, 패키지에 있는 모든 클래스가 접근 가능하다. 서브 클래스라도 다른 패키지에 있다면, 슈퍼 클래스의 디폴트 멤버는 접근할 수 없다.

슈퍼클래스의 public 멤버

슈퍼 클래스의 멤버가 public으로 선언되면, 깉은 패키지에 있든 다른 패키지에 있든 모든 클래스에서 접근할 수 있다.

슈퍼 클래스의 protected 멤버

슈퍼 클래스의 protected 멤버는 다음 두 가지 경우에 접근을 허용한다.
- 같은 패키지에 속한 모든 클래스들 
- 같은 패키지든 다른 패키지든 상속받는 서브 클래스

서브 클래스와 슈퍼 클래스의 생성자 호출 및 실행 

서브 클래스와 슈퍼 클래스는 각각 생성자를 가지고있다. 서브 클래스의 객체가 생성되면 이 객체 속에 서브 클래스와 멤버와 슈퍼 클래스의 멤버가 모두 들어 있다. 생성자의 목적은 객체 초기화에 있으므로 서브 클래스의 생성자는 생성된 객체 속에 들어 있는 서브 클래스의 멤버 초기화나 필요한 초기화를 수행하고, 슈퍼 클래스의 생성자는 생성된 객체 속에 있는 슈퍼 클래스의 멤버 초기화나 필요한 초기화를 각각 수행한다.

서브 클래스의 생성자가 먼저 호출되지만, 결국 슈퍼 클래스의 생성자가 먼저 실행되고 서브 클래스의 생성자가 나중에 실행된다. 컴파일러는 서브 클래스의 생성자에대해, 슈퍼 클래스의 생성자를 호출한 뒤 자신의 코드를 실행하도록 컴파일한다. 이것은 당연한 조치로서, 슈퍼 클래스가 먼저 초기화된 후, 이를 활용하는 서브 클래스가 초기화되어야 되기 떄문이다.

서브 클래스에서 슈퍼 클래스 생성자 선택

서브 클래스의 개발자가 서브 클래스의 각 생성자에 대해, 함께 실행될 슈퍼 클래스의 생성자를 지정하여야 한다. 하지만 개발자가 슈퍼 클래스의 생성자를 명시적으로 지정하지 않는 경우, 컴파일러는 자동으로 슈퍼 클래스의 기본 생성자를 호출하도록 컴파일한다.

슈퍼 클래스의 기본 생성자가 자동 선택되는 경우

개발자의 명시적 지시가 없으면, 서브 클래스의 생성자가 기본 생성자이든 매개변수를 가진 것이든, 슈퍼 클래스에 만들어진 기본 생성자가 선택된다. 이 선택은 자바 컴파일러에 의해 강제로 이루어진다.

super()를 이용하여 명시적으로 슈퍼 클래스의 생성자 선택

서브 클래스의 생성자에서 슈퍼 클래스의 생성자를 명시적으로 선택하는 것이 원칙이다. 지금까지는 개발자가 명시적으로 선택하지 않았을 때, 컴파일러가 자동으로 슈퍼 클래스의 기본 생성자를 호출한다.

서브 클래스의 생성자에서 super()를 이용하면, 슈퍼 클래스 생성자를 명시적으로 선택할 수 있다. super()는 슈퍼 클래스 생성자를 호출하는 코드이다. 괄호 안에 인자를 전달하여 슈퍼 클래스의 생성자를 호출할 수도 있다.

IS - A 관계(is a relationship inheritance)는 일반적인 개념과 구체적인 개념의 관계이다. 

일반 클래스를 구체화 하는 상황에서 상속을 사용한다.
상속을 사용하면 많은 장점이 있지만, 하위 클래스가 상위 클래스에 종속되기 때문에 이질적인 클래스 간에는 상속을 사용하지 않는 것이 좋다. 다순히 코드를 재사용할 목적으로 서로 관련이 없는 개념의 클래스를 상속 관계로 사용하지 않는것이 좋다.

HAS - A 관계(has a relationship association)는 일반적인 포함 개념의 관계이다.

캐스팅(casting)

캐스팅이란 타입 변환을 말하며 형변환이라고도 한다. 자바의 상속 관계에 있는 부모와 자식 클래스 간에 서로 간의 형변환이 가능하다.

업캐스팅(upcasting)

자바에서 서브 클래스는 슈퍼 클래스의 속성을 상속받기 때문에, 서브 클래스의 객체는 슈퍼 클래스의 멤버를 모두 가진다. 그러므로 서브 클래스의 객체를 슈퍼 클래스의 객체로 취급할 수 있다. 서브 클래스의 객체에 대한 레퍼런스를 슈퍼 클래스의 타입으로 변환하는 것을 업캐스팅이라고한다.

<pre><code>
Person p;
Students s = new Student();
p = s; // 업캐스팅
</pre></code>

다운캐스팅(downcasting)

다운캐스팅은 자신의 고유한 특성을 읽은 서브 클래스의 객체를 다시 복구 시켜주는 것을 말한다. 업캐스팅된 것을 다시 원상태로 돌리는 것을 말한다.

<pre><code>
Person p = new Student("이재문"); // 업캐스팅

Student s = (Student)p; // 다운캐스팅, (Student)의 타입 변환을 반드시 표시
</pre></code>

instanceof 연산자

레퍼런스가 가리키는 개체가 어떤 클래스 타입인지 구분하기 위해, 자바에서는 instanceof 연산자를 두고 있다.

<pre><code>
레퍼런스 instanceof 클래스명 
</pre></code>

메소드 오버라이딩(method overriding)

메소드 오버라이딩은 슈퍼 클래스와 서브 클래스의 메소드 사이에 발생하는 관례로서, 슈퍼 클래스에 선언된 메소드와 같은 이름, 같은 리턴 타입, 같은 매개 변수 리스트를 갖는 메소드를 서브 클래스에서 재작성하는 것이다. 서브 클래스이 개발자는 슈퍼 클래스에 있는 메소드로 목적하는 바를 이룰 수 없을 때 동일한 이름의 메소드를 서브 클래스에 다시 작성할 수 있다.

슈퍼 클래스의 메소드를 무시하고 서브 클래스에서 오버라이딩된 메소드가 무조건 실행되도록 한다는 것인데, 이런 처리를 동적 바인딩이라고 부르며, 메소드 오버라이딩은 동적 바인딩(Dynamic Binding)을 유발시킨다.

동적 바인딩(Dynamic Binding)

다형성을 사용하여 메소드를 호출할때, 발생하는 현상이다. <br>
실행시간(run time) 즉, 파일을 실행하는 시점에 성격이 결정된다. <br>
실제 참조하는 객체는 서브 클래스이니 서브 클래스의 메소드를 호출한다. <br>

정적 바인딩(Static Binding)

컴파일(Compile) 시간에 성격이 결정된다. <br>
변수의 타입이 슈퍼 클래스이니 슈퍼클래스의 메소드를 호출한다. <br>

오버라이딩된 메소드 호출 

<pre><code>
Line line = new Line();
line.draw();
</pre></code>

오버라이딩은 슈퍼 클래스에 선언된 메소드를, 각 서브 클래스들이 자신만의 내용으로 새로 구현하는 기능이다.오버라이딩은 상속을 통해 하나의 인터페이스에 서로 다른 내용 구현이라는 객체 지향의 다형성을 실현하는 도구이다.

메소드 오버라이딩의 제약 사항

- 슈퍼 클래스의 메소드와 동일한 원형으로 작성한다.

슈퍼 클래스의 메소드와 동일한 이름, 동일한 매개변수 타입과 개수, 동일한 리턴 타입을 갖는 메소드를 작성해야 한다. 

- 슈퍼 클래스 메소드의 접근 지정자보다 접근의 범위를 좁여 오버라이딩 할 수 없다.
접근 지정자는 public, protected, 디폴트, private 순으로 접근의 범위가 좁아진다. 슈퍼 클래스에 protected로 선언된 메소드는 서브 클래스에서 protected나 public으로만 오버라이딩할 수 있고, public으로 선언된 메소드는 서브 클래스에서 public으로 오버라이딩할 수 있다.

- static이나 private 또는 final로 선언된 메소드는 서브 클래스에서 오버라이딩할 수 없다.

동적 바인딩(dynamic binding)은 실행할 메소드를 컴파일 시(compile time)에 결정하지 않고 실행 시(run time)에 결정하는 것을 말한다. 자바에서는 동적 바인딩을 통해 오버라이딩된 메소드가 항상 실행되도록 보장한다.

<pre><code>
Shape a = new Shape();
a.paint(); // paint()는 Shape의 draw()를 호출한다.
</pre></code>

자바에서 오버라이딩된 메소드가 있다면 동적 바인딩을 통해 오버라이딩된 메소드가 무조건 실행된다.

super 키워드
<pre><code>
super.슈퍼클래스의멤버
</pre></code>

super는 자바 컴파일러에 의해 지원되는 것으로 슈퍼 클래스에 대한 레퍼런스이다.

<pre><code>
name : "Circle";  // Circle 클래스의 name에 "Circle" 기록
super.name = "shape"; // Shape 클래스의 name에 "Shape" 기록
Ssuper.draw(); // Shape 클래스의 draw() 호출. 정적 바인딩
</pre></code>

오버라이딩(overriding)

오버라이딩은 슈퍼 클래스의 메소드를 이름, 매개변수 타입과 개수, 리턴 타입을 모두 동일하게 서브 클래스에 재작성하는 경우이다.

오버로딩(overloading)

오버로딩은 한 클래스나 상속 관계에 있는 클래스들 사이에 메소드의 이름은 같지만, 매개변수 타입이나 개수가 다르게 메소드를 작성하는 경우이다.

메소드 오버로딩 선언

같은 클래스나 상속 관계에서 동일한 이름의 메소드 중복 작성

메소드 오버로딩 관계 

동일한 클래스 내 혹은 상속 관계

메소드 오버로딩 목적 

이름이 같은 여러 개의 메소드를 중복 작성하여 사용의 편리성 향상. 다형성 실현

메소드 오버로딩 조건 

메소드 이름은 반드시 동일하고, 매개변수 타입이나 개수가 달라야 성립

메소드 오버로딩 바인딩

정적 바인딩. 호출될 메소드는 컴파일 시에 결정 

메소드 오버라이딩 선언

서브 클래스에서 슈퍼 클래스에 있는 메소드와 동일한 이름의 메소드 재작성

메소드 오버라이딩 관계

상속 관계

메소드 오버라이딩 목적 

슈퍼 클래스에 구현된 메소드를 무시하고 서브 클래스에서 새로운 기능의 메소드를 재정의하고자함. 다형성 실현

메소드 오버라이딩 조건 

메소드의 이름, 매개변수 타입과 개수, 리턴 타입이 모두 동일하여야 성립

메소드 오버라이딩 바인딩

동적 바인딩, 실행 시간에 오버라이딩된 메소드 찾아 호출

추상 메소드(abstract method)

추상 메소드란 선언은 되어 있으나 코드가 구현되어 있지 않은, 즉 껍데기만 있는 메소드이다. 추상 메소드를 작성하려면 abstract 키워드와 함께 원형만 선언하고 코드는 작성하지 않는다.

<pre><code>
public abstract String getName();
public abstract void setName(String s);
</pre></code>

- 추상 메소드를 포함하는 클래스 
<pre><code>
abstract class Shape { // 추상 클래스 선언
    public Shape() { }
    public void paint() { draw(); }
    abstract public void draw(); // 추상메소드 선언
}
</pre></code>

- 추상 메소드가 없지만 abstract로 선언한 클래스
<pre><code>
abstract class MyComponent { // 추상 클래스 선언
    String name;
    public void load(String name) {
      this.name = name;
    }
}
</pre></code>

추상 클래스는 객체를 생성할 수 없다.

응용프로그램은 추상 클래스의 객체(인스턴스)를 생성할 수 없다. 추상 클래스는 본디 객체를 생성할 목적으로 만드는 클래스가 아니다. 추상 클래스에는 실행 코드가 없는 미완성 상태인 추상 메소드가 있을 수 있기 때문에이다.

추상 클래스의 상속

추상 클래스를 단순히 상속 받는 서브 클래스는 추상 클래스가 된다. 추상 클래스의 추상 메소드를 그대로 상속받기 때문이다. 그러므로 서브 클래스에 abstract를 붙여 추상 클래스임을 명시해야 컴파일 오류가 발생하지 않는다.
<pre><code>
abstract class Shape { // 추상 클래스
    public Shape() { }
    public void paint() { draw(); } 
    abstract public void draw(); // 추상 메소드
}
abstract class Line extends Shape { // 추상 클래스. draw()를 상속받기 때문
    public String toString() { return "Line"; }
}
</pre></code>

추상 클래스의 구현

추상 클래스의 구현이란 슈퍼 클래스에 선언된 모든 추상 메소드를 서브 클래스에서 오버라이딩하여 실행 가능한 코드로 구현하는 것을 말한다.

추상 클래스는 추상 메소드를 통해 서브 클래스가 구현할 메소드를 명료하게 알려주는 인터페이스의 역할을 하고, 서브 클래스는 추상 메소드를 목적에 맞게 구현하는 다형성을 실현할 수 있다.

인터페이스(interface)

하나의 시스템을 구성하는 2개의 구성 요소(하드웨어, 소프트웨어) 또는 2개의 시스템이 상호작용할 수 있도록 접속되는 경계(boundary), 이 경계에서 상호 접속하기 위한 하드웨어, 소프트웨어, 조건, 규약 등을 포괄적으로 가리키는 말이다.

인터페이스는 RS- 232 인터페이스, USB 인터페이스, SATA 인터페이스 하드디스크 등 컴퓨터 주변 장치에서 많이 사용하는 용어이다.

자바의 인터페이스

자바의 인터페이스는 interface 키워드를 사용하여 클래스를 선언하듯이 선언한다.

<pre><code>
interface PhoneInterface { // 인터페이스 선언
    public static final in TIMEOUT = 10000; // 상수 필드, public static final 생략 가능
    public abstract void sendCall(); // 추상 메소드, public abstract 생략 가능
    public abstract void receiveCall(); // 추상 메소드, public abstract 생략 가능
    public default void printLogo() { // default 메소드, public 생략 가능
        System.out.println("** phone **");
        }; // 디폴트 메소드
    }
</pre></code>

인터페이스 구성

필드(멤버 변수)를 만들 수 없다.

- 상수와 추상 메소드

- default 메소드

- private 메소드

- static 메소드

추상 메소드는 public abstract로 정해져 있으며, 생략될 수 있고, 다른 접근 지정으로 지정될 수 없다. default, private, static 메소드들은 모두 인터페이스 내에 코드가 작성되어 있어야 한다. default 메소드의 접근 지정은 public으로 고정되어 있다. private 메소드는 인터페이스 내에서만 호출 가능하다. static 메소드의 경우 접근 지정이 생략되면 public이며, private으로 지정될 수 있다.

인터페이스는 객체를 생성할 수 없다
인터페이스에 구현되지 않은 추상 메소드를 가질 수 있기 때문에 객체를 생성할 수 없다.

인터페이스 타입의 레퍼런스 변수는 선언 가능하다
<pre><code>
PhoneInterface galaxy; // galaxy는 인터페이스에 대한 레퍼런스 변수 
</pre></code>

인터페이스끼리 상속된다
인터페이스는 다른 인터페이스를 상속할 수 있다.

인터페이스를 상속받아 클래스를 작성하면 인터페이스의 모든 추상 메소드를 구현하여야 한다
자바의 인터페이스는 상속받을 서브 클래스에게 구현할 메소드들의 원형을 모두 알려주어, 클래스가 스스로 목적에 맞게 메소드를 구현하도록 하는 것이 목적이다.

인터페이스 구현 

인터페이스 구현이란 implements 키워드를 사용하여 인터페이스의 모든 추상 메소드를 구현한 클래스를 작성하는 것을 말한다.

<pre><code>
class SamsungPhone implements PhoneInterface { // 인터페이스 구현
        // PhoneInterface의 모든 추상 메소드 구현
        public void sendCall() { System.out.println("띠리리리링"); }
        public void receiveCall() { System.out.println("전화가 왔습니다."); }
        // 메소드 추가 작성
        public void flash() { System.out.println("전화기에 불이 켜졌습니다."); }
}
</pre></code>

인터페이스 상속 

클래스 인터페이스를 상속받을 수 없고, 인터페이스끼리만 상속이 가능하다. 상속을 통해 기존 인터페이스에 새로운 규격을 추가한 새로운 인터페이스를 만들 수 있으며, 인터페이스의 상속은 extends 키워들 사용한다.

인터페이스의 다중 상속

<pre><code>
interface MusicPhoneInterface extends MobilePhoneInterface, MP3Interface { // 다중 상속
    void playMP3RingTone(); // 추상 메소드
}
</pre></code>

다중 인터페이스 구현
클래스는 하나 이상의 인터페이스를 구현할 수 있다. 이 경우 콤마로 각 인터페이스를 구분하여 나열하며, 각 인터페이스에 선언된 모든 추상 메소드를 구현하여야 한다.

클래스 상속과 함께 인터페이스 구현
클래스를 상속 받으면서 동시에 인터페이스를 구현할 수 있다.

인터페이스와 추상 클래스는 유사하다 
- 객체를 생성할 수 없고, 상속을 위한 슈퍼 클래스로만 사용된다.
- 클래스의 다형성을 실현하기 위한 목적이다.

추상 클래스 목적

추상 클래스는 서브 클래스에서 필요로 하는 대부분의 기능을 구현하여 두고 서브 클래스가 상속받아 활용할 수 있도록 하되, 서브 클래스에서 구현 할 수밖에 없는 기능만 추상 메소드로 선언하여, 서브 클래스에서 구현하도록 하는 목적(다형성)

추상 클래스 구성
- 추상 메소드와 일반 메소드 모두 포함
- 상수, 변수 필드 모두 포함

인터페이스 목적 

인터페이스는 객체의 기능을 모두 공개한 표준화 문서와 같은 것으로, 개발자에게 인터페이스를 상속받는 클래스의 목적에 따라 인터페이스의 모든 추상 메소드를 만들도록 하는 목적(다형성)

인터페이스 구성
- 변수 필드(멤버 변수)는 포함하지 않음
- 상수, 추상 메소드, 일반 메소드, default 메소드, static 메소드 모두 포함 
- protected 접근 지정 선언 불가
- 다중 상속 지원

템플릿 메소드 패턴(Template Method Pattern)

특정 작업을 처리하는 일부분을 서브 클래스로 캡슐화하여 전체적인 구조는 바꾸지 않으면서 특정 단계에서 수행하는 내용을 바꾸는 패턴이다.

![6d96f34afbd9baf4c5f701110a2b98f](https://user-images.githubusercontent.com/60682087/147710645-84514d83-978a-450d-be5f-fe9f5ce19e2b.png)

템플릿 메소드 패턴 장단점 

장점

1. 중복코드를 줄일 수 있다.
2. 자식 클래스의 역할을 줄여 핵심 로직의 관리가 용이하다.
3. 좀더 코드를 객체지향적으로 구성할 수 있다.

단점

1. 추상 메소드가 많아지면 클래스 관리가 복잡해진다.
2. 클래스간의 관계와 코드가 꼬여버릴 염려가 있다.

MVC 패턴 

모델-뷰-컨트롤러(Model-View-Controller)는 소프트웨어 공학에서 사용되는 소프트웨어 디자인 패턴이다. 이 패턴을 성공적으로 사용하면, 사용자 인터페이스로부터 비즈니스 로직을 분리하여 애플리케이션의 시각적 요소나 그 이면에서 실행되는 비즈니스 로직을 서로 영향없이 쉽게 고칠 수 있는 어플리케이션을 만들 수 있다.

![1](https://user-images.githubusercontent.com/60682087/147466386-a95498a7-5ae5-47d6-aac5-fff79a1754c7.png)

View 

모델을 표현하는 방법을 제공하는 사용자 인터페이스 
일반적으로 화면에 표시하기 위해 필요한 상태 및 데이터를 모델에서 직접 가져온다.

Model

모든 데이터, 상태 및 어플리케이션 로직이 들어있다.
뷰와 컨트롤러에서 모델의 상태를 조작하거나 가져오기 위한 인터페이스를 제공하고 모델에서 자신의 상태 변화에 대해서 옵저버들에게 알려주긴한다.

Controller

뷰와 모델 사이에 위치하며 사용자로부터 입력을 받아 그것이 모델에게 어떤 의미가 있는지 파악한다. 
단순히 모델한데 전달하는 역할만 하는 것이 아니라 사용자가 입력한 것을 분석하여 그것을 바탕으로 모델을 조작하는 임무를 맡고 있다.

뷰에서 컨트롤러의 역할을 직접 맡아도 되지만, 그렇게 하지 않는 것이 좋다.
첫번째로 뷰가 두가지 역할을 맡기 때문에 코드가 복잡해지고 유지보수에도 좋지 않다.
두번째로 뷰를 모델에서 너무 밀접하게 연관시켜야 한다는 문제가 있기 때문에 뷰를 다른 모델하고 연결해서 재사용하기가 어려워 진다.

컨트롤러는 뷰와 모델의 결합을 끊어주는 역할을 한다.
뷰와 컨트롤러는 느슨하게 결합시켜 놓으면 더 유연하고 확장하기 좋은 디자인을 만들 수 있다.

사용자는 뷰하고만 접촉할 수 있다.
뷰는 모델을 보여주는 창이라 할 수 있다.
재생 버튼을 누른다든가 하는 식으로 뷰에 대해서 어떠한 행동을 하면 뷰에서 컨트롤러한데 사용자가 어떤 일을 했는지 알려준다.

컨트롤러에서 모델한데 상태를 변경하라는 요청을 한다.
컨트롤러에서는 사용자의 행동을 받아 해석한다.
사용자가 버튼을 누른다든가 하는 어떤 행동을 하면 컨트롤러에서 그것이 무엇을 의미하는지 분석하고 그 행동에 따라서 모델을 어떤식으로 조작해야 하는지 결정한다.

컨트롤러에서 뷰를 변경해 달라고 요청할 수 있다.
컨트롤러에서 뷰로부터 어떤 행동을 받았을 때, 그 행동의 결과로 뷰를 바꿔달라 할 수 있다. 예를 들어 컨트롤러에서 인터페이스에 있는 어던 버튼이나 메뉴를 활성화 또는 비활성화 시킬 수 있다.

상태가 변경되면 모델에서 뷰한데 그 사실을 알린다.
사용자의 행동 때문이든 다른 내부적인 변화 때문이든 모델에서 무엇인가가 변경되면 모델에서 뷰한데 상태가 변경 되었음을 알린다.

뷰에서 모델한데 상태를 요청한다. 
뷰에서 화면에 표시할 상태는 모델로부터 직접 가져온다.
예를 들어 모델에서 뷰한데 새로운 곡이 재생되기 시작했다고 알려주면 뷰에서는 모델한데 곡 제목을 요청하고 그것을 받아 화면에 표시한다.
컨트롤러에서 뷰를 바꾸라는 요청을 했 을 때도 뷰에서 모델한데 상태를 알려달라고 요청 할 수 있다.

뷰와 컨트롤러 

![2](https://user-images.githubusercontent.com/60682087/147466514-eda08ff4-2d82-4b63-982d-1be6ed686d5b.png)

뷰와 컨트롤러는 고전적인 스트래티지 패턴으로 구현되어 있다. 때문에 뷰 객체를 여러 전략을 써서 설정할 수 있으며 컨트롤러가 전략을 제공한다. 뷰에서는 애플리케이션의 컽모습에만 신경을 쓰고, 인터페이스의 행동에 대한 결정은 모두 컨트롤러에게 맡긴다. 스트래티지 패턴을 이용하므로 뷰를 모델로부터 분리시키는 데에는 도움이 된다.

뷰

![3](https://user-images.githubusercontent.com/60682087/147466543-d12c6f7b-d341-4ea8-9b85-724bd305239d.png)

뷰에 속하는 디스플레이는 여러 단계로 겹쳐져 있는 일련의 원도우, 패널, 버튼, 텍스트, 레이블 등으로 구성된다. 각 디스플레이 항목은 복합 객체 또는 잎 이 될 수있다. 컨트롤러에서 뷰한데 화면을 갱싱해 달라고 요청하면 최상위 뷰 구성요소 한데만 갱신해 달라고 요청하면 된다. 나머지 컴포지트 패턴에 의해 자동으로 처리 된다.

모델

![4](https://user-images.githubusercontent.com/60682087/147466582-ab25dd29-a2a6-4a0d-90a9-14b30c6ac8fa.png)

모델에서 옵저버 패턴을 써서 상태가 변경되었을 때 그 모델하고 연관된 객체들에게 연락을 한다. 옵저버 패턴을 이용해서 뷰 및 컨트롤러로부터 완전히 독립시킬 수 있다. 한 모델에서 서로 다른 뷰를 사용할 수 있고, 여러 개의 뷰를 동시에 사용하는 것도 가능하다.

MVC와 웹 환경 

웹의 등장으로 여러 개발자들이 MVC를 브라우저/서버 모델에 맞게 변형 시켜서 사용하기 시작했다. 모델2방식을 가장 많이 쓰는데 서블릿과 JSP기술을 사용하여 일반적인 GUI와 마찬가지로 모델,뷰,컨트롤러를 분리해서 디자인 할 수 있다.

![5](https://user-images.githubusercontent.com/60682087/147466630-c09da1c1-f5ab-44ca-8bb6-8b826ea2567b.png)

1.사용자가 HTTP요청을 하면 서블릿에서 그 요청을 수신한다.

사용자가 웹 브라우저를 이용해 HTTP요청을 한다. 보통 사용자 ID와 비밀번호 같은 폼 데이터가 함께 전달된다. 서블릿에서는 이런 폼 데이터를 받아 파싱한다.

2.서블릿이 컨트롤러 역할을 한다.

서블릿은 컨트롤러 역할을 맡아서 사용자 요청을 처리하고, 대부분의 경우에 모델에 어떤 요청을 하게된다. 요청을 처리한 결과는 일반적으로 자바 형태로 포장된다.

3.뷰는 JSP에 의해 표현된다. JSP에서 모델의 뷰를 나타내는 페이지만 만들어 주면된다.

4.그 페이지를 만드는 과정에서 다음 단계의 작업을 위해 몇 가지 더 제어해야 할 일이 있을 수도 있다.

5. 뷰에서 HTTP를 통해서 브라우저 한데 페이지를 전달한다.

페이지가 브라우저한데 전달되면 , 그 웹페이지가 사용자의 화면에 표시된다. 사용자가 또 다른 요청을 할 수 있으며, 새로운 요청도 지금까지의 과정과 같은 방식으로 처리한다. 

모델2의 장점 

제작 책임까지도 분리시켜주기 떄문에 모델2의 장점은 단순히 디자인적인 면에서 각 구성요소를 분리해주는 것에 그치지 않는다.  모델 2가 등장하면서 개발자들은 서블릿에만 전념하면 되고, 웹 자작자들은 간단한 모델2 스타일의 JSP만 다루면 되는 환경이 조성되었다. 그래서 웹 자작자들은 HTML과 간단한 자바빈즈만 만지면된다.

디자인 패턴과 모델2 

모델2는 MVC를 웹에 맞게 적용시킨 것이다. 

![6](https://user-images.githubusercontent.com/60682087/147466692-5014d28f-772d-42a4-8361-e3413b70585b.png)

1.옵저버 패턴 

고전적인 의미에서 본다면 뷰는 더 이상 모델의 옵저버라고 할 수 없다. 모델한데 등록해서 모델의 상태가 바꿔었다는 연락을 받는다는가 하지 않기 때문이다. 하지만 여전히 모델의 상태가 바뀔 때 컨트롤러를 통해서 간접적으로 나마 연락을 받긴 한다. 게다가 컨트롤러에서는 뷰한데 빈을 건내주기 때문에 뷰에서 모델의 상태를 알아낼 수 있다.

브라우저 모델을 생각해 보면, 뷰에서는 브라우저로 HTTP응답을 할 때만 모델의 상태에 대한 정보가 필요하다. HTTP 응답을 하지않는 상황에서는 모델로부터 연락을 받아봤자 할 일이 없다. 페이지를 만들어서 브라우저로 보낼 때만 모델의 상태를 반영하여 뷰를 생성하는 것이 의미 있는 행동이 된다.

2.스트래티지 패턴 

컨트롤러 서블릿이 여전히 전략 객체로 쓰인다. 하지만 고전적인 MVC에서 처럼 뷰 객체에 컨트롤러 객체에 대한 레퍼런스가 들어가는 방식으로 구현되지 않는다. 그럼에도 불구하고 컨트롤러 서블릿이 뷰의 행동을 구현하는 객체라는 점과 다른 행동을 원하는 경우에는 다른 컨트롤러로 바꿀 수 있다는 점에서 보면 여전히 스트래티지 패턴을 따른다고 볼 수 있다.

3.컴포지트 패턴 

GUI와 마찬가지로 웹의 뷰도 결국은 중첩된 그래픽 구성요소로 이루어진다. 이경우 HTML코드를 통해 웹 브라우저에서 랜더링 된다는 차이점이 있긴 하지만, 그밑엔 결국 복합 객체 형태의 객체 시스템이 있을 가능성이 매우 높다. 

시퀀스 다이어그램(Sequence Diagram)

시퀀스 다이어그램은 특정 행동이 어떠한 순서로 어떤 객체와 어떻게 상호작용을 하는지 표현하는 행위 다이어그램이다. 현재 존재하는 시스템이 어떠한 시나리오로 움직이고 있는지를 나타내는데 장점을 가지고있다. 시퀀스 다이어그램을 이용하면 API등의 유즈 케이스를 디테일하게 알 수 있고 타 시스템의 API 호출등의 로직을 모델링 할 수 있어 시나리오를 파악하기 좋다. <br>

LIfeline 

모델링 되는 인스턴스를 나타낸다. Lifeline은 네모와 점선으로 이루어져 있으며 네모가 객체의 관점으로 표현했다면 클래스이고 서비스 관점으로 표현했으면 컴포넌트가 된다. 점선은 시간의 경과를 나타낸다.

![정리1](https://user-images.githubusercontent.com/60682087/147577131-ccd4e441-e560-4d5a-8fa2-bbd42f9831ed.png)

Activation

Activation은 Lifeline의 인스턴스가 다른 인스턴스와 상호 작용을 하며 활성화 되어 있는 것을 나타낸다. Activation은 직사각형의 막대로 Lifeline의 점선 가운데에 표시한다.

![정리2](https://user-images.githubusercontent.com/60682087/147577164-2f8c2b05-d6f8-4d45-9a7f-0e21b01ef0ed.png)

Message 

메시지는 인스턴스 간 주고 받은 데이터를 나타낸다. 일반적으로 요청과 응답으로 나타낸다. 메시지는 아래와 같은 유형을 가진다.

유형   내용

동기 메시지(Sync message) 요청을 보낸 후 반환이 올때까지 대기 <br>
비동기 메시지(Async message) 요청을 보낸 다음 반환을 기다리지 않고 다른 작업을 수행 <br>

자체 메시지(Self message) 자기 자신에게 요청을 보냄 <br>
반환 메시지(Reply/Return message) 요청에 대해 메시지를 반환 <br> 

동기 메시지

동기 메시지는 실선과 꽉 찬 화살표로 표현을 한다. 동기 메시지 이므로 요청을 보낸 후 결과가 올 때까지 기다린다.

![정리3](https://user-images.githubusercontent.com/60682087/147577366-13261829-1e23-4ef9-8288-fadde1110189.png)

비동기 메시지 

비동기 메시지는 실선과 선으로 이뤄진 화살표로 표현한다. 비동기 메시지이므로 요청을 보낸 후 결과를 기다리지 않는다.

![정리4](https://user-images.githubusercontent.com/60682087/147577401-7c235996-6720-4bce-8644-442501484609.png)

자체 메시지

자체적으로 작업을 처리할 때 자체 메시지를 사용한다. 자체 메시지는 본인의 LifeLine으로 회귀하는 화살표를 그린다.

![정리5](https://user-images.githubusercontent.com/60682087/147577444-1b59fa40-6f8c-4f36-b10e-ae3d6878ec32.png)

반환 메시지 

동기 메시지에서 표현했던 것과 같이 요청에 대한 결과를 반환한다. 점선과 선으로 이뤄진 화살표로 표현한다.

![정리6](https://user-images.githubusercontent.com/60682087/147577483-311b3dca-aec9-41bf-ae21-7858f658d7e2.png)

흐름 제어

위의 표현으로도 충분히 시퀀스 다이어그램을 그릴 수 있다.  로직에서는 if,for,while과 같은 흐름을 제어하는 표현식이 있는데 시퀀스 다이어그램은 시간 순으로 인스턴스 간 상호작용을 표현하기 때문에 흐름을 제어하는 표현들이 필요할 수 있다. 여기서 사용하는 요소가 Guard와 Sequence Fragment이다.

Guard

Guard는 단일 메시지에 대해 조건을 명시할 수 있는 방법이다. 사용방법은 메시지의 앞쪽에 [ ] 대괄호로 감싼 후 조건을 명시한다. 예를 들어 가격이 10,000원 이상이라고 하면 [price > 10000] 이라고 명시한다. 아래는 가격이 10000원 이상이라면 배송비를 무료로 처리하도록 하는 예시이다. 만약 가격이 10000원 미만이면 해당 메시지는 호출되지 않는다.

![정리7](https://user-images.githubusercontent.com/60682087/147577565-edbf17e2-84ee-41ad-89a3-2fa065160a79.png)

Sequence Fragment

Sequence Fragment는 범위로 조건을 명시할 수 있다. 특정 부분에 대해서 메시지를 반복하거나 조건을 명시할 때 사용된다.

Alternative 

Alternative는 alt로 줄여서 사용한다. alt는 조건문인 if/else문을 Guard를 사용해 표현할 수 있다. 즉 조건에 따라 선택 사항이 여러 개일 경우 사용된다. 아래는 가격이 10000원 이상이면 배송비를 무료로 처리하고 그렇지 않으면 배송비를 유료로 사용하는 것을 표현한 예시이다.

![정리8](https://user-images.githubusercontent.com/60682087/147577611-933fbd39-5870-4d07-ab91-6078257b295b.png)

Option

Option은 opt로 줄여서 사용한다. opt는 조건문인 if문 Guard를 사용해 표현할 수  있다. 즉 조건에 따라 선택 사항이 단 한개일 경우에 사용된다. 아래는 가격이 10000원 일상이라면 배송비를 무료로 처리하고 고객이 추가 할인 쿠폰을 요청한 다음 쿠폰을 제공하는 예시이다. 만약 가격이 10000원 미만이라면 해당 로직을 타지않는다.

![정리9](https://user-images.githubusercontent.com/60682087/147577655-5ab88446-843f-4ce1-8fbf-f32028317d13.png)

Opt를 보면 Guard만 사용한 것과 유사해보인다. opt를 사용했는데 처리하는 내용이 1개라면 Guard와 동일한 효과를 나타낸다. 두개의 차이는 Guard는 A라면 B한다. 와 같이 1개에 대해 1가지의 결과를 보여주는 반면, opt는 A라면 B도 하고 C도하고 등등을 한다. 와 같이 1개에 대해 여러 결과를 나타낼수있다.

Loop

Loop은 단어의 의미 그대로 for, while과 같은 반복문을 표현한다. 아래는 입력된 시간이 2020-08-01보다 작을때 반복문을 실행하고 그 하위 조건으로 처리를 하는 예시이다.

![정리10](https://user-images.githubusercontent.com/60682087/147577735-fcb8f23f-e311-4b41-bd3d-0f4c8e7f51dd.png)

Parallel

Parralel은 단어 그대로 병렬 처리를 의미하며 par로 줄여서 사용한다. 아래는 상품 주문이 들어왔을때 상품 확인과 배송 여부 확인을 병렬로 진행하는것을 표현한 예시이다.

![정리11](https://user-images.githubusercontent.com/60682087/147577915-5696d3e7-6432-436f-b150-0dd5cbf09bbc.png)

- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
