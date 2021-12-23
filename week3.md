CRUD 

CRUD는 대부분의 컴퓨터가 소프트웨어가 가지는 기본적인 데이터 처리 기능인 Create(생성), Read(읽기), Update(갱신), Delete(삭제)를 묶어서 일컫는 말이다. 사용자 인터페이스가 갖추어야 할 기능을 가리키는 용어로서도 사용된다.

객체지향 언어의 특성

1. 캡슐화 (Encapsulation)

객체지향 프로그래밍을 할때 있어서 매우 중요한 특징으로 서로 연관이 있는 데이터와 알고리즘을 하나로 묶어서 하나의 캡슐과 같은 형태로 만드는것이다. 이때 서로 연관이 없는 다른 객체의 접근을 제한하기 위해서 접근 제한 수식자의 기능을 제공한다. 이 기능 덕분에 데이터와 알고리즘이 다른 정보로 인해서 손상이 되거나 오류가 발생할 가능성을 최소화시키는 것이 가능하며 데이터가 바뀌더라도 사용방법은 바뀌지 않아서 다른 객체에 영향을 끼치지 않는다 그리고 독립성이 유지되면서 객체 간의 결합도가 낮아져서 인터페이스가 간단해지는 효과를 얻을 수 있다.

2. 상속 (Inheritance)

상속이란 소프트웨어 개발자들이 클래스들 간의 관계를 정립하는데 있어서 상위 클래스와 하위 클래스를 구분하게 되는데 이때 상위 클래스의 모든 것을 하위 클래스가 이어 받는 것을 상속이라고 표현한다. 
ex) 상위 클래스는 A는 3개의 데이터 (a,b,c)와 함수 3개(funcA(),funcB(),funcC())를 가지고 하위 클래스 B는 2개의 데이터(d,e)와 함수 2개(funcD(),funcE()) 를 가지고있으며 하위 클래스 C는 2개의 데이터(f,g)와 함수 2개(funcF(),funcG())를 가지고 있다고 하면 B와C는 상위 클래스 A에 있는 데이터와 함수를 상속받아서 활용할 수 있다.

3. 다형성 (Polymorphism)

다형성이란 여러 개의 형태를 가진다는 의미이다. 하지만 프로그래밍 언어에서는 상속과 연관이 있는 개념으로 사용이 되며 하나의 객체가 다른 여러 객체로 재구성이 되는 것을 의미한다. 다형성을 나타냐는 예시로는 오버 로딩과 오버라이딩이 있다. 프로그래밍에서 오버 로딩이란 메서드 중복 정의 오버라이딩이랑 메서드 재정의를 의미한다.

메서드 오버 로딩이란 이름이 동일한 메서드가 하나의 클래스 안에서 중복해서 정의되어 있는 경우를 의미한다. 동일한 이름의 메서드가 있으면 구분을 할 수 없기 때문에 매개변수를 다르게 해서 메서드를 구분해 주게 된다.

![정리1](https://user-images.githubusercontent.com/60682087/147115400-4061fef1-956d-4a6f-b0e0-0c4a5017f4e7.png)

메서드 오버라이딩도 메서드 오버 로딩처럼 상속에서 발생하게 되는데 오버라이딩은 상위 클래스에서 정의를 한 메서드를 하위 클래스에서 상속을 받아왔을때 상위 클래스의 정의를 전부 무시하고 다시 재정의해서 사용하는 것을 의미한다.

4.추상화 (Abstraction)

추상화란 공통된 속성이나 기능을 묶어서 이름을 붙이는 것으로 객체지향적 관점에서 클래스를 정의하는 것이 추상화라고 볼수있다. 

예시)

어떤한 물건들이 있을때 이 물건들의 공통된 특성을 통해서 해당 물건들을 모두 포함하는 단어로 물건들을 설명하는 것을 추상화로 볼 수 있다.
추상화는 다른 객체들과 구분되는 핵심적인 특징들에만 집중하면서 복잡도를 관리할 수 있도록 하는 효과를 가져오게된다. 이때 주의할 점은 추상화는 문제 영역과 관점에 의존적이라는 것으로 어떤 영역에서 중요한 것이 다른 영역에서는 중요하지 않을 수도 있어서 하나의 대상이라도 목적에 따라서 여러 추상화 모델이 만들어지게 될 수 있다.

절차지향프로그래밍 

어떠한 명령어들을 어떠한 순서로 몇 번 실행시킬지를 생각해두고 하는 프로그래밍 컴퓨터의 처리과정과 비슷하다. 
실행 속도가 빠르다는 장점이 있다. 
코드가 길어질수록 이해하기 쉽지 않다는 단점이 있다.

객체지향프로그래밍

실제 세계에서의 소통방식을 프로그래밍으로 구현한 것과도 같다. 어떠한 대상에 필요한 변수들이나 함수들을 하나의 조립단위로 묶어 객체라고 부른다. 실행속도가 절차지향프로그래밍에 비해 느리지만, 코드가 길어져도 이해하기가 쉽다. 또한 변수의 이름이 겹칠 위험도 적다.

클래스

클래스란 객체를 정의해녾은것 또는 객체의 설계도, 틀 이라고 정의할 수 있다.
클래스는 객체를 생성하는데 사용되며, 객체는 클래스에 정의된 대로 생성된다.

객체

객체란 사전적인 정의로 실제 존재하는 것이다. 객체지향 이론에서는 사물과 같은 유형적인 것뿐만 아니라, 개념이나 논리와 같은 무형적인 것들도 객체로 간주한다. 프로그래밍에서의 객체는 클래스에 정의된 내용대로 메모리에 생성된 것을 뜻한다. 

필드(field)

필드(field) : 클래스 안에서 선언되는 멤버변수
지역 변수(local variable) : 메소드 블록 안에서 선언되는 변수 

<pre><code>
Class {
    Public int speed  { // 필드
    Void start(int s)  { //매개 변수
    Int t; // 지역 변수 
    }
  }
}
</pre></code>

필드를 선언 할 때는 접근 지정자, 필드의 타입, 필드의 이름 세가지를 정해줘야 한다. 접근 지정자에는 public과 private가 있으며, public은 모든 클래스로 부터 접근가능, private는 클래스 내부에서만 접근가능하다.

접근자와 설정자

접근자(accessor) : 필드 값을 반환한다. 일반적으로 게터(getter)라고 부르기도 한다.

설정자(mutator) : 필드 값을 설정한다. 일반적으로 세터(setter)라고 부르기도 한다.

<pre><code>
class Car {

    String color;

    public String getColor() //접근자
    {
        return color;
    }
    public void setColor(String c) //설정자
    {
        color = c;
    }
}

public class CarTest1{

    public static void main(String[] args) {

        Car myCar = new Car();

        myCar.setColor = "RED"; //설정자 사용
        System.out.println(myCar.getColor); //접근자 사용
    }
}
</pre></code>

필드의 접근 지정자

접근 지정자는 크게 클래스에 붙는 접근 지정자와 내부구성요소(멤버 + 생성자)에 붙는 접근 지정자로 나눌 수 있다.

클래스에 붙는 접근 지정자는 public, default가있다.

내부구성요소에는 붙는 접근 지정자는 public, protected, default, private가있다.

Public : 어디에서든 접근가능하다.

Private : 같은 클래스 혹은 같은 객체 안에서만 접근이 가능하다.

Protected : 같은 package안에서만 접근 가능하고, package가 달라도 상속 관계이면 접근이 가능하다.

Default : 같은 package 안에서만 접근이 가능하다.

클래스 구성

<pre><code>
public class Circle
// 필드(변수)
public int radius; // 원의 반지름 필드
public String name; // 원의 이름 필드

// 메소드
public Circle() { // 원의 생성자 메소드
}
public double getArea() { // 원의 면적 계산 메소드
    return 3.14 * radius * radius;
  }
}
</pre></code>

new 연산자와 객체 생성, 그리고 레퍼런스 변수
<pre><code>
public static void main(Stringv args[]) {
    Circle pizza; // Circle 객체에 대한 레퍼런스 변수 pizza  선언
    pizza = new Circle(); // Circle 객체 생성
    
    pizza.radius = 10; //  radius 필드에 10 저장
    pizza.name = "자바피자"; // name 필드에 "자바피자" 저장
    double area = pizza.getArea(); // pizza 객체의 면적 알아내기
}
</pre></code>

레퍼런스 변수 선언 
<pre><code>
Circle pizza; // 레퍼런스 변수 pizza 선언
</pre></code>

객체 생성 new 연산자
<pre><code>
pizza = new Circle();
Circle 타입 크기의 메모리 할당
Circle() 생성자 코드 실행
Circle pizza = new Circle();
</pre></code>

객체 멤버 접근
<pre><code>
객체 레퍼런스.멤버
ex) 
pizza.radius = 10;
int r = pizza.radius;
double area = pizza.get();
</pre></code>

생성자(Constructor)

생성자란 객체의 생성과 동시에 자동으로 호출되는 메소드이다. 내부나 외부 클래스에서 객체를 생성할때 new 연산자와 함께 사용되며 객체의 초기화를 담당한다.

New 연산자에 의해 생성자가 성공적으로 실행되면 Heap 영역에서 객체가 생성되고 객체의 주소는 리턴되어 클래스 변수에 저장되어 객체에 접근할때 이용한다. 인스턴스 변수의 초기화 작업에 주로 사용되며, 인스턴스 생성 시 실행되어야 할 작업을 위해서도 사용된다.

생성자의 특징

생성자의 이름은 클래스의 이름과 동일해야한다. 
생성자는 리턴타입(return type)이 없다.
생성자는 객체의 메모리가 생성된 직후에 호출된다.
생성자는 초기화를 위한 데이터를 인수로 전달 받을 수 있다.
생성자도 메소드 오버로딩이 가능하다.

생성자의 호출

New 키워드를 사용하여 객체를 생성할때 자동으로 생성자가 호출된다. 

기본 생성자(Default Constructor)

기본 생성자는 매개변수를 하나도 가지지 않고, 아무런 명령어도 포함하지 않는다. 자바 컴파일러는 컴파일 시 클래스에 생성자가 하나도 정의되어 있지 않을 경우에만 자동으로 기본 생성자를 추가한다.

생성자 오버로딩(Constructor Overloading)

생성자도 오버로딩할 수 있다. 생성자 오버로딩은 매개 변수를 변경하여 생성자를 여러개 선언하는것을 오버로딩이라고 한다.

외부에서 제공되는 다양한 데이터를 이용해서 객체를 초기화 하기 위해서는 생성자도 다양화 되어야 하기 때문에 생성자 오버로딩을 통해 매개변수를 달리하여 생성자를 여러개 선언하여 다양화 할 수 있다.

생성자의 이름은 클래스 이름과 동일하다
<pre><code>
public class Circle {
public Circle(int r, String n) { ... } // 생성자
}
</pre></code>

생성자는 여러개 오버로딩 할 수 있다
<pre><code>
public class Circle {
public Circle() { ... } // 매개 변수 없는 생성자
public Circle(int r, String n) { ... } // 2개의 매개 변수를 가진 생성자
}
</pre></code>

생성자는 new를 통해 객체를 생성할 때 한번만 호출된다
<pre><code>
Circle pizza = new Circle(10, "자바피자"); // 생성자 Circle(int r, String n) 호출
Circle donut = new Circle(); // 생성자 Circle() 호출
</pre></code>

생성자에 리턴 타입을 지정할 수 없다
<pre><code>
public Circle() { ... } // 리턴 타입 선언하지 않음
</pre></code>

생성자의 목적은 객체가 생성될 때, 필요한 초기 작업을 위함이다
<pre><code>
Circle pizza = new Circle(10,"자바피자"); // 생성자 Circle(int r, Sting n)호출
</pre></code>

기본 생성자
<pre><code>
class Circle {
    public Circle() {} // 기본 생성자. 매개변수 없고 아무 일 없이 단순 리턴
}
</pre></code>

기본 생성자가 자동으로 생성되는 경우
<pre><code>
Circle pizza = new Circle(); // 생성자 Circle() 호출
</pre></code>

기본 생성자가 자동으로 생성되지 않은 경우
<pre><code>
Circle pizza = new Circle(10);  // Circle(int r) 호출
public Circle(int r) {
    radius = r;
}
</pre></code>

this 레퍼런스

this는 현재 객체 자신에 대한 레퍼런스이다. 보다 정확히 말하면 현재 실행되고 있는 메소드가 속한 객체에 대한 레퍼런스이다. this는 컴파일러에 의해서 자동 관리되므로 개발자는 this를 사용하기만 하면된다.

<pre><code>
public class Circle {
    int radius;
    public Circle(int r) { this.radius = r; }
    public int getRadius() { return radius; }
}
</pre></cdoe>

this의 필요성
앞의 Circle 클래스에서 메소드 getRadius()는 다음과 같이 this를 사용하지 않았다.
클래스 내에서 멤버 radius를 접근할 때 굳이 this.radius로 할 필요가 없다.

<pre><code>
return radius; // return this.radius;와 동일 
</pre></code>

this는 언제 필요한가?

1. 지역변수나 매개변수와 인스턴스변수의 이름이 같은 경우 구별하려는 목적으로 사용한다.

2. 메소드가 객체 자기자신의 레퍼런스를 리턴해야 하는 경우 사용한다.

3. 다른 메소드 호출시 객체 자신의 레퍼런스를 전달할때 사용한다.

this() 
1. 클래스 내에 생성자가 다른 생성자를 호출 할때 사용한다.

2. 생성자 안에서만 사용 가능하다.

3. 생성자 내에서 다른 생성자의 기능이 필요할 때 사용한다.

4. 생성자가 두개 이상일 경우 사용 가능하다(생성자 오버로딩)

5. 다른 생성자 호출 시, 반드시 생성자의 첫번째 라인에서 호출 해야 한다.

6. 코드 재사용성을 높이는 방법.

this 사용 시 주의할 점 

this()는 반드시 생성자 코드에서만 호출할 수 있다.
this()는 반드시 같은 클래스 내 다른 생성자를 호출할 때 사용된다.
this()는 반드시 생성자의 첫 번째 문장이 되어야 한다.

<pre><code>
public Book() {
    System.out.println("생성자 호출됨");
    this(","); // 컴파일 오류. this()는 생성자의 첫 번째 문장이어야 함 
}
</pre></code>

객체 치환

<pre><code>
Circle ob1 = new Circle(1);
Circle ob2 = new Circle(2);

s = ob2; // s에 치환(대입)
ob1 = ob2; // 객체 치환
</pre></code>

객체 배열 
자바에서는 기본 타입 데이터뿐 아니라, 객체를 원소로 하는 객체 배열도 만들 수 있다. 객체 배열은 객체에 대한 레퍼런스를 원소로 갖는 배열이다.

<pre><code>
Circle [] c; // Circle 배열에 대한 레퍼런스 변수 c선언
c = new Circle[5]; // 레퍼런스 배열 생성
for(int i = 0; i < c.length; i++) { // c.length는 배열 c의 크기로서 5
    c[i] = new Circle(i); // 배열의 각 원소 객체 생성 
    System.out.print(int)(c[i].getArea()+ " "); // 배열의 원소 객체 사용
}
</pre></code>

배열 선언 및 생성 

배열에 대한 레퍼런스 선언

<pre><code>
Circle [] c;
</pre></code>

레퍼런스 배열 생성

<pre><code>
c = new Circle[5]; // Circle 객체에 대한 레퍼런스 5개 생성
</pre></code>

객체 생성

<pre><code>
for(int i = 0; i < c.length; i++) { // c.length는 배열 c의 크기로서 5
 c[i] = new Circle(i); // i 배열의 Circle 객체 생성
}
</pre></code>

배열의 원소 객체 접근

<pre><code>
for(int i = 0; i < c.length; i++) {
     System.out.print(int)(c[i].getArea()+ " ");
}
</pre></code>

메소드 (method)

메소드를 선언할때는 접근 지정자,반환형,매개변수,메소드 내부 내용이 필요하다.
매개변수의 자료형이 다르면 메소드의 이름은 같아도 된다. 이러한 메소드들을 중복 메소드라고 한다. 하지만 중복 메소드는 코드 해석을 어렵게 만들 수 있으므로 주의 깊게 사용해야 한다.

메소드 형식

<pre><code>
public int getSum(int i, int j) {
    int sum;
    sum + i + j;
    return sum;
}

public : 접근 지정자
int : 리턴 타입
getSum : 메소드 이름
int i, int j : 메소드 인자들

    int sum;      : 메소드 코드
    sum + i + j;  : 메소드 코드
    return sum;   : 메소드 코드
</pre></code>

인자 전달

자바의 메소드 호출 시 인자 전달방식(argument passing)은 값에 의한 호출(call by value)이다.

메소드 오버로딩 

자바에서 한 클래스 내에 이름이 같지만 매개변수의 타입이나 개수가 서로 다른 여러 개의 메소드를 중복 작성 할 수 있다. 

메소드 이름이 동일하여야 한다.
매개변수의 개수나 타입이 서로 달라야 한다.
메소드의 리턴 타입이나 접근 지정자는 메소드 오버로딩과 관계없다.

객체의 소멸

객체 소멸이란 new에 의해 생성된 객체 공간을 자바 가상  기께에게 돌려주어 가용 메모리(available memory)에 포함시키는 것이다.


가비지

가비지(garbage)란 자바 응용프로그램에서 더 이상 사용되지 않게 된 객체나 배열 메모리이다.

가비지 걸렉션(garbage collection)

가비지는 더 이상 참조되지 않기 때문에 가비지가 차지하고 있는 메모리 공간은 회수되어야 한다. 가비지가 많아지면 자바 플랫폼이 응용프로그램에게 할당해줄 수 있는 가용 메모리 양이 줄어들게 된다. 시간이 지날수록 자연히 가비지가 늘어나게 되며, 최악의 경우 자바 플랫폼의 가용 메모리가 0이 되면 자바 응용프로그램은 더 이상 실행 될 수 없게 된다. 이런 경우를 대비하여 자바 플랫폼은 가용 메모리가 일정 크기 이하로 줄어들면 자동으로 가비지를 회수하여 가용 메모리를 늘린다.

가비지 컬렉션 강제요청

<pre><code>
System.ge() // 가비지 컬렉션 강제 요청 
</pre></code>

접근 지정자 

패키지 

패키지는 디렉터리 혹은 폴더와 같은 개념이며, 개발자는 클래스 파일들을 여러 패키지에 분산 관리하는 것이 일반적이다.

접근 지정자(access specifier)

접근 지정자는 클래스나 멤버들을 다른 클래스에서 접근해도 되는 지의 여부를 선언하는 지시어이다.

- private, protected, prulbic, 접근 지정자 생략(디폴트 접근 지정)

클래스 접근 지정 

클래스 접근 지정이란 다른 클래스에서 이 클래스를 활용할 수 있는지 허용 여부를 지정하는 것으로 말한다.

public 클래스

클래스 이름 앞에 public으로 선언된 클래스로서, 패키지에 상관없이 다른 어떤 클래스에게도 사용이 허용된다.

<pre><code>
public class World { // public 클래스
    ...........
}
</pre></code>

디폴트 클래스(접근 지정자 생략)

접근 지정자 없이 클래스를 선언한 경우. 디폴트 접근 지정으로 선언된다.

<pre><code>
class Local { // 디폴트 클래스 
    .........
}
</pre></code>

public 멤버 

public 멤버는 패키지를 막론하고 모든 클래스들이 접근 가능하다.

private 멤버

private 멤버

private 접근 지정자는 비공개를 지시하는 것으로, private 멤버는 클래스 내의 멤버들에게만 접근이 허용된다

protected 멤버

protected 접근 지정자는 보호된 공개를 지시하는 것으로, 2가지 유형의 클래스에만 접근을 허용한다.
1. 같은 패키지의 모든 클래스에 접근이 허용된다.
2. 다른 패키지에 있더라도 자식 클래스의 경우 접근이 허용된다.

디폴트 멤버(default 또는 package - private)

접근 지정자가 생략된 멤버의 경우, 디폴트(default) 멤버라고 한다. 동일한 패키지 내에 있는 클래스들만 디폴트 멤버를 자유롭게 접근할 수 있다.

static 멤버

static 멤버의 선언 

<pre><code>
class StaticSample
int n; // non - static 필드
void g() {...} // non - static 메소드

static int m; // static 필드
static void f() {...} // static 메소드 
</pre></code>

non - static 멤베와 static 멤버의 차이점 

<pre><code>
non - static 선언 
class Sample {
    int n;
    void g() {...}
}

non - staticv 공간적 특성
멤버는 객체마다 별도 존재
- 인스턴스 멤버라고 부른다

non - static 시각적 특성
객체 생성 시에 멤버 생성됨
- 객체가 생길 때 멤버도 생성
- 객체 생성 후 멤버 사용 가능
- 객체가 사라지면 멤버도 사라짐

non - static 공유의 특징 
공유되지 않음
- 멤버는 객체 내에 각각 공간 유지 

static 선언 
class Sample {
    static int m;
    static voide g() {...]
}

static 공간적 특성 
멤버는 클래스당 하나 생성
- 멤버는 객체 내부가 아닌 별도의 공간(클래스 코드가 적재되는 메모리)에 생성
- 클래스 멤버라고 부른다.

static 시각적 특성
클래스 로딩 시에 멤버 생성
- 객체가 생기기 전에 이미 생성
- 객체가 생기기 전에도 사용 가능
- 객체가 사라져도 멤버는 사라지지 않는다.
- 멤버는 프로그램이 종료될 때 사라짐

static 공유의 특성 
동일한 클래스의 모든 객체들에 의해 공유된다.
</pre></code>

static 멤버의 생성
<pre><code>
StaticSample s1, s2;

s1 = new StaticSample();
s2 = new StaticSample();
</pre></code>

static 멤버 접근 
<pre><code>
객체.static필드
객체.static메소드
</pre></code>

static 메소드의 제약 조건 
static 메소드는, 객체 없이도 존재하기 떄문에, 객체와 함께 생성되는 non - static 멤버를 사용할 수 없고 static 멤버들만 사용 가능하다. 반면 non - static 메소드는 static 멤버들을 사용할 수있다.

<pre><code>
class StaticMethod {
    int n;
    void f1(int x) {n = x;} // 정상
    void f2(int x) {m = x;} // 정상
}
</pre></code>

final 클래스
final이 클래스 이름 앞에 사용되면 클래스를 상속받을 수 없음을 지정한다.

final 메소드 
final로 메소드를 선언하면 오버라이딩할 수 없는 메소드임을 선언한다. 자식 클래스가 부모 클래스의 특정 메소드를 오버라이딩하지 못하게 하고 무조건 상속받아 사용할 수 있다.

final 필드
final로 필드를 선언하면 필드는 상수가 된다.

- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
