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

다형성을 사용하여 메소드를 호출할때, 발생하는 현상이다.
실행시간(run time) 즉, 파일을 실행하는 시점에 성격이 결정된다.
실제 참조하는 객체는 서브 클래스이니 서브 클래스의 메소드를 호출한다.

정적 바인딩(Static Binding)

컴파일(Compile) 시간에 성격이 결정된다.
변수의 타입이 슈퍼 클래스이니 슈퍼클래스의 메소드를 호출한다.

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

추상 클래스를 단순히 상속 받는 서브 클래스는 추상 클래스가 된다. 추상 클래스의 추상 메소드를 그대로 상속받기 때문이다. 그러므로 서브 클래스에 abstract를 붙여 부상 클래스임을 명시해야 컴파일 오류가 발생하지 않는다.
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

- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
