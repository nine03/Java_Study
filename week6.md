컬렉션(Collection)

컬렉션은 안드로이드를 비롯한 자바 프로그램을 작성하는데 빼놓을 수 없는 중요한 도구이다. 자바의 JDK는 소위 자료 구조 과목에서 배운 많은 자료 구조들을 컬렉션으로 만들어 제공한다. 

컬렉션의 특징

- 요소(element)라고 불리는 가변 개수의 객체들의 저장소 
- 객체들의 컨테이너라고도 불린다.
- 고정 크기의 배열을 다루는 어려움을 해소할 수 있다.
- 다양한 객체를 삽입, 삭제 검색 할 수 있다.
- 컬렉션은 제너릭 기법으로 구현된다.

제너릭(Generics) 

특정 타입만 다루지 않고 여러 종류의 타입으로 변신할 수 있도록 클래스나 메소드를 일반화 시키는 기법이다. 

ex) 

<pre><code>
class Stack<E> {
  ...
  void push(E element) { ... }
  E pop() { ... } 
  ...
}
</pre></code>

제너릭 타입 매개변수 

컬렉션 클래스에서 타입 매개변수로 사용하는 문자는 다른 변수와 혼동을 피하기 위해 일반적으로 하나의 대문자를 사용한다.

<pre><code>
E : Element를 의미하며 컬렉션에서 요소임을 나타낸다.
T : Type을 의미한다.
V : Value를 의미한다.
K : Key를 의미한다.
</pre></code>

제너릭 컬렉션 활용 

Vector<E>

Vector<E>는 배열을 가변 크기로 다룰 수 있게 하고, 객체의 삽입, 삭제, 이동이 쉽도록 구성한 컬렉션 클래스이다. 벡터는 삽입되는 요소의 개수에 따라 자동으로 크기를 조절하고, 요소의 삽입과 삭제에 따라 자동으로 요소들의 자리를 이동한다.

벡터 생성

벡터를 생성할때, Vector<E>의 E에 요소로 사용할 타입을 지정해야 한다.

<pre><code>
Vector<Integer> v = new Vector<Integer>();

레퍼런스 변수 선언과 벡터 생성을 분리하여 코드를 만들 수 있으며, 벡터는 문자열만 다룬다. 

Vector<String> stringVector; // 제너릭 컬렉션에 대한 레퍼런스 변수 선언
StringVector = new Vector<String>(); // 문자열 벡터 생성

Vector<Integer> v = new Vector<Integer>(5); // 초기 용량이 5인 벡터 생성
</pre></code>

Vector<E> 클래스의 주요 메소드 

<pre><code>
boolean add(E element) : 벡터의 맨 뒤에 element추가
void add(int index, E element) : 인덱스 index에 element를 삽입
int capacity() : 벡터의 현재 용량 리턴 
boolean addAll(Collection < ? extends E > c) : 켈렉션 c의 모든 요소를 벡터의 맨 뒤에 추가 
void clear() : 벡터의 모든 요소 삭제
boolean contains(Object o) : 벡터가 지정된 객체 o를 포함하고 있으면 true리턴 
E elementAt(int index) : 인덱스 index의 요소 리턴 
E get(index) : 인덱스 index의 요소 리턴 
int indexOf(Object o) : o와 같은 첫 번째 요소의 인덱스 리턴, 없으면 -1 리턴 
boolean isEmpty() : 벡터가 비어 있으면 true리턴 
E remove(int index) : 인덱스 index의 요소 삭제
boolean remove(Object o) : 객체o와 같은 첫 번째 요소를 벡터에서 삭제
void removeAllElements() : 벡터의 모든 요소를 삭제하고 크기를 0으로 만든다.
int size() : 벡터가 포함하는 요소의 개수 리턴
Object[] toArray() : 벡터의 모든 요소를 포함하는 배열 리턴 
</pre></code>

벡터에 요소 삽입 

add() 메소드를 이용하면 벡터의 끝이나 중간에 요소를 삽입할 수 있다. 

<pre><code>
v.add(Integer.valueOf(5));
v.add(Integer.valueOf(4));
v.add(Integer.valueOf(-1));
</pre></code>

자동 박싱 기능

<pre><code>
v.add(5); // 5 -> new Integer(5)로 자동 박싱된다.
v.add(4); 
v.add(-1);

</pre></code>
벡터에는 null도 사입할 수 있기 때문에, 벡터를 검색할 때 null이 존재할 수 있음을 염두에 두어야 한다.

<pre><code>
v.add(null);
</pre></code>

add()를 이용하여 벡터의 중간에 객체를 삽입할 수 있다.

<pre><code>
v.add(2,100); // 인덱스 2의 위치에 정수 100을 삽입 
</pre></code>

벡터 내의 요소알아내기

벡터 내에 존재하는 요소를 알아내기 위해서 get()이나 elementAt메소드를 이용한다.
<pre><code>
Vector<Integer> v = new Vector<Integer>();
v.add(5);
v.add(4);
v.add(-1);
</pre></code>

get()이나 elementAt() 메소드는 인자로 주어진 인덱스에 있는 Integer 객체를 리턴한다.

<pre><code>
Integer obj = v.get(1); // 벡터의 1번째 Integer 객체를 얻어낸다.
int i = obj.intValue(); // obj에 있는 정수를 알아낸다. 이값은 4

int i = v.get(1); // 자동언박싱
</pre></code>

벡터의 크기와 용량 알아내기 

벡터의 크기란 벡터에 들어 있는 요소의 개수를 말하며, 벡터의 용량이란 수용할 수 있는 크기를 말한다.

<pre><code>
int len = v.size(); // 벡터의 크기. 벡터에 존재하는 요소 객체의 수 size() 메소드룰 호출한다.
</pre></code>

<pre><code>
int cap = v.capacity(); // 벡터의 용량
</pre></code>

<pre><code>
v.remove(1); // 인덱스 1의 워치에 있는 요소 삭제
</pre></code>

<pre><code>
Integer m = Integer.valueOf(100); // m은 객체 레퍼런스
v.add(m);
...
v.remove(m); // 레퍼런스 m의 요소 삭제
</pre></code>

벡터의 모든 요소를 삭제하는방법 
<pre><code>
v.removeAllElements();
</pre></code>

컬렉션과 자동 박싱/언박싱

자동 박싱(auto boxing)에 의해 int 타입을 값을 사용하면 자동으로 Integer 객체로 변환되어 삽입된다.
<pre><code>
v.add(4); // 정수 4가 Integer(4)로 자동 박싱된다.
v.add(-1); // 정수 -1이 Integer(-1)로 자동 박싱된다.
</pre></code>

컬렉션으로부터 값을 얻어내는 과정에서는 과정에서는 자동 언박싱(auto unboxing)이 일어난다.
<pre><code>
int k = v.get(0); // k = 4
</pre></code>

컬렉션을 매개변수로 받는 메소드 만들기
<pre><code>
public void printVector(Vector<Integer> v) {
    for(int i = 0; i < v.size(); i++) {
      int n = v.get(i); // 벡터의 i번째 정수
      System.out.println(n);
    }
}
</pre></code>

메소드 호출하는 코드 
<pre><code>
Vector<Integer> v = new Vector<Integer>(); // Integer 벡터 생성 
printVector(v); // 메소드 호출 
</pre></code>

자바의 타입 추론 기능 
<pre><code>
Vector<Integer> v = new Vector<Integer>(); // Java 7이전
Vector<Integer> v = new vector<>(); // Java 7부
var v = new Vector<Integer>(); // Java 10부터
</pre></code>

ArrayList<E>

ArrayList<E>는 가변 크기의 배열을 구현한 컬렉션 클래스로서 경로명은 java.util.ArrayList이며, Vector 클래스와 거의 동일하다. 크게 다른 점은 ArrayList는 스레드 간에 동기화를 지원하지 않기 때문에, 다수의 스레드가 동시에 ArrayList에 요소를 삽입하거나 삭제할 때 ArrayList의 데이터가 훼손될 우려가 있다. 하지만 멀티스레드 동기화를 위한 시간 소모가 없기 때문에, ArrayList는 Vector보다 속도가 빨라, 단일 스레드 응용에는 더 효과적이다.

ArrayList<E>  클래스의 주요 메소드

<pre><code>
boolean add(E element) : ArrayList의 맨 뒤에 element추가
void add(int index, E element) : 인덱스 index 위치에 element삽입
boolean addAll(Collection < ? extends E > c) : 컬렉션 c의 모든 요소를 ArrayList의 맨 뒤에 추가 
void clear() : ArrayList의 모든 요소 삭제
boolean contains(Object o) : ArrayList가 지정된 객체를 포함하고 있으면 true리턴
E elementAt(int index) : index 인덱스의 요소 리턴 
E get(int index) : index 인덱스의 요소 리턴 
int indexOf(Object o) : o와 같은 첫 번째 요소의 인덱스 리턴, 없으면 -1리턴
boolean isEmpty() : ArrayList가 비어있으면 true리턴
E remove(int index) : index 인덱스의 요소 삭제 
boolean remove(Object o) : o와 같은 첫 번째 요소를 ArrayList에서 삭제
int size() : ArrayList가 포함하는 요소의 개수 리턴
Object[] toArray() : ArratList의 모든 요소를 포함하는 배열 리턴 
</pre></code>

ArrayList의 생성
<pre><code>
ArrayList<String> a = new ArrayList<String>();
</pre></code>

ArrayList에 요소 삽입
<pre><code>
a.add("Hello");
a.add("Hi");
a.add("Java");
ArrayList에도 Vector와 마찬가지로 null을 삽입할 수 있다.
a.add(null);
</pre></code>

ArrayList 내의 요소 알아내기 

get()이나 elementAt() 메소드를 이용하면 ArrayList 내의 요소를 알아낼 수 있다.
<pre><code>
String str = a.get(1); // "Hi" 리턴
</pre></code>

ArrayList의 크기 알아내기

size() 메소드를 호출하면 현재 ArrayList에 들어 있는 요소의 개수를 알아낼 수 있다.
<pre><code>
int len = a.size(); // ArrayList에 들어 있는 요소의 개수
</pre></code>

ArrayList에서 요소 삭제

remove() 메소드를 이용하면 ArrayList 내 임의의 인덱스에 있는 요소를 삭제할 수 있다.
<pre><code>
a.remove(1); // 인덱스 1의 위치에 있는 요소 삭제
</pre></code>

레퍼런스를 이용하여 remove()를 호출할 수 있다.
<pre><code>
String s = new String("bye");
a.add(s);
...
a.remove(s); // a에서 문자열 s 삭제
</pre></code>

ArrayList에 있는 모든 요소를 삭제하려면 clear()를 호출한다.
<pre><code>
a.clear();
</pre></code>

컬렉션의 순차 검색을 위한 Iterator

Vector, ArrayList, LinkedList, Set과 같이 요소가 순서대로 저장된 컬렉션에서 요소를 순차적으로 검색할 때는 java.util 패키지의 Iterator<E> 인터페이스를 사용하면 편리하다.

<pre><code>
Vector<Integer> v = new Vector<Integer>(); // 요소가 Integer 타입인 벡터 
</pre></code>

벡터 v의 iterator()를 호출하여, 벡터 v의 각 요소를 순차적으로 검색할 수 있는 Iterator 객체를 얻어낸다.

<pre><code>
Iterator<Integer> it = v.iterator(); // 벡터 v의 요소를 순차 검색할 Iterator 객체 리턴 
</pre></code>

Iterator<E> 인터페이스의 메소드 
<pre><code>
boolean hsaNext() : 방문할 요소가 남아 있으면 true리턴
E next() : 다음 요소 리턴
void remove() : 마지막으로 리턴된 요소 제거 
</pre></code>

HashMap<K,V>

HashMap<K,V> 컬렉션은 결로명이 java.util.HashMap이며, key(키) 와 값(value)의 쌍으로 구성되는 요소를 다룬다. 
k는 키로 사용할 데이터 타입을 v는 값으로 사용할 데이터 타입의 타입매개변수이다.

<pre><code>
HashMap<String, String> h = new HashMap<String, String>(); // 해시맵 생성 
h.put("apple","사과"); // "apple" 키와 "사과" 값의 쌍을 h에 삽입
String kor = h.get("apple"); // "apple" 키로 값 검색. kor는 검색된 값, "사과"
</pre></code>

put(key,value) 

put(key,value) 메소드는 키와 값을 받아, 키를 이용하여 해시함수(Hash function)를 실행하고 해시 함수가 리턴하는 위치에 키와 값을 저장한다.

get(key)

get(key)은 다시 키를 이용하여 동일한 해시 함수를 실행하여 값이 저장된 위치를 알아내어 값을 리턴한다. 해시맵은 해시 함수를 통해 키와 값이 저장되는 위치를 결정하므로, 사용자는 그 위치를 알 수 없고, 삽입되는 순서와 들어 있는 위치 또한 관계가 없다.

해시맵의 장단점

1. 요소의 삽입, 삭제 시간이 매우 빠르다. 요소의 위치를 결정하는 해시 함수가 간단한 코드로 이루어지며, Vector<E> 나 ArrayList<E>와 달리 요소의 삽입 삭제 시 다른 요소들의 위치 이동이 필요 없기 때문이다.
2. 요소 검색은 더욱 빠르다. 해시맵의 get(key) 메소드가 호출되면 해시 함수가 key가 저장된 위치를 단번에 찾아내므로, Vector<E> 나 ArrayList<E>에서처럼 모든 요소들을 하나씩 비교하는 시간 낭비가 전혀 없기 때문이다.
3. 해시맵은 인덱스를 이용하여 요소에 접근할 수 없고 오직 키 로만 검색해야한다. 그러므로 해시맵은 빠른 삽입과 검색이 필요한 응용에 적합하다.

<pre><code>
void clear() : 해시맵의 모든 요소 삭제
boolean containsKey(Object key) : 지정된 키(key)를 포함하고 있으면 true리턴
boolean containsValue(Object value) : 지정된 값(value)에 일치하는 키가 있으면 true리턴
v get(Object key) : 지정된 키(key)의 값 리턴, 키가 없으면 null리턴
boolean isEmpty() : 해시맵이 비어 있으면 true리턴
Set<K> keySet() : 해시맵의 모든 키를 담은 Set<K> 컬렉션 리턴
V put(K key, V value) : key와 value 쌍을 해시맵에 저장
v remove(Object key) : 지정된 키(key)를 찾아 키와 값 모두 삭제
int size() : HashMap에 포함된 요소의 개수 리턴
</pre></code>

해시맵 생성

해시맵은 HashMap<K,V>에서 k에는 키로 v에는 값으로 사용할 구체적인 타입을 지정하여 생성한다.

<pre><code>
HashMap<String,String> h = new HashMap<String, String>();
// Java 7부터 HashMap<String,String> h = new HashMap<>(); 로 간략히 쓸 수 있다
// Java 10부터 var h = new HashMap<String, String>(); 로 간략히 쓸 수 있다.
</pre></code>

해시맵에 요소 삽입 

요소를 삽입할 때는 put() 메소드에 키 와 값을 전달한다.
<pre><code>
h.put("baby","아기"); // "baby"는 키, "아기"는 값
h.put("love","사랑");
h.put("apple","사과");
</pre></code>

키 로 값읽기

get() 메소드에 키 를 전달하면 값을 얻을 수 있다.
<pre><code>
String kor1 = h.get("love"); // kor1 = "사랑"
</pre></code>

키 로 요소 삭제

remove()메소드를 사용한다.
<pre><code>
h.remove("apple"); // put("apple","사과")로 삽입한 요소 삭제
</pre></code>

요소 개수 알아내기

size() 메소드를 사용한다.
<pre><code>
int n = h.size(); // 현재 h 내에 있는 요소의 개수 리턴
</pre></code>

해시맵의 전체 검색 

해시맵의 모든 키를 알아낸 후, 각 키에 대해 하나씩 값을 알아내는 방식으로 작성하면 된다.
HashMap의 keySet()메소드는 모든 키를 Set컬렉션으로 만들어 리턴한다.
<pre><code>
Set<String> keys = h.keySet(); // 해시맵 h에 있는 모든 키를 Set 컬렉션으로 리턴
Iterator<String> it = keys.iterator(); // Set의 각 문자열을 순차 검색하는 Iterator리턴
while(it.hasNext()) {
  String key = it.next(); // 키
  String value = h.get(key); // 값 
  System.out.println("(" + key + "," + value +")"); // 키와 값의 쌍 출력
}
</pre></code>

LinkedList<E>

LinkedList<E>는 List<E> 인터페이스를 구현한 클래스로서 경로명이 java.util.LinkedList이다. LinkedList는 요소들을 양방향으로 연결하여 관리한다는 점을 제외하고 Vector, ArrayList와 거의 같다.

Collections 클래스 활용

java.util 패키지에 포함된 Collections 클래스는 다음과 같이 걸렉션을 다루는 유용한 여러 메소드를 지원한다.

- sort() : 컬렉션에 포함된 요소들의 정렬
- reverse() : 요소를 반대 순으로 정렬
- max(), min() : 요소들의 최대값과 최소값 찾아내기
- binartSearch() : 이진 검색

제너릭 클래스 

제너릭 클래스를 작성하는 방법은 클래스 작성 방법과 유사한데, 클래스 이름 다음에 일반화된 타입(generic type)의 매개변수를 <와> 사이에 추가한다는 차이가 있다.

제네릭 클래스 작성

타입 매개변수 T를 가진 제너릭 클래스 

<pre><code>
public class MyClass<T> { // 제너릭 클래스 Myclass, 타입 매개변수 T
  T val; // 변수 val의 타입은 T
  void set(T a) {
    val = a; // T 타입의 값 a를 val에 지정
  }
  T get() {
      return val; // T 타입의 값 val리턴
  }
}
</pre></code>

제너릭 클래스에 대한 레퍼런스 변수 선언

<pre><code>
MyClass<String> s; // <T>를 String으로 구체화
List<Integer> li; // <E>를 Integer로 구체화
Vector<String> vs; // <E>를 String으로 구체화 
</pre></code>

제너릭 객체 생성 - 구체화(specialization)

제너릭 클래스에 구체적인 타입을 대입하여 구체적인 객체을 생성하는 과정을 구체화라고 부르며, 이과정은 자바 컴파일러에 의해 이루어진다.

<pre><code>
MyClass<String> s = new MyClass<String>(); // 제너릭 타입 T를 String으로 구체화
s.set("hello");
System.out.println(s.get()); // "hello" 출력

MyClass<Integer> s = new MyClass<Integer>(); // 제너릭 타입 T를 Integer로 구체화
n.set(5);
System.out.println(n.get()); // 숫자 5 출력 
</pre></code>

타입 매개변수 

제너릭 클래스 내에서 제너릭 타입을 가진 객체의 생성은 허용되지 않는다.

<pre><code>
public class MyVector<E> {
      E Create() {
          E a = new E(); // 컴파일 오류. 제너릭 타입의 객체 생성 불가
          return a;
      }
}
</pre></code>

제너릭과 배열 

제너릭에서는 배열에 대한 제한을 두고 있다. 제너릭 클래스 또는 인터페이스 타입의 배열은 선언할 수 없다.

<pre><code>
GStack<Integer>[] gs = new GStack<Integer>[10]; // 컴파일 오류 
</pre></code>

제너릭 타입의 배열 선언은 허용된다.

<pre><code>
public void myArray(T[] a) { ... } // 정상
</pre></code>

제너릭 메소드 

클래스의 일부 메소드만 제너릭으로 구현할 수도 있다. 

<pre><code>
class GenericMethodEx {
  static <T> void toStack(T[] a, GStack<T> gs) {
        for(int i = 0; i < a.length; i++) {
            gs.push(a[i]);
        }
  }
}
</pre></code>

타입 매개변수는 메소드의 리턴 타입 앞에 선언된다 위의 toStack()에서 <T>가 타입 매개변수의 선언이다. 제너릭 메소드를 호출할 때는 컴파일러가 메소드의 인자를 통해 타입을 유추할 수 있어 제너릭 클래스나 인터페이스와는 달리 타입을 명시하지않아도 된다. 

컴파일러가 toStack()의 호출문으로부터 타입 매개변수 T를 Object로 유추하는경우이다.

```
Object[] oArray = new Object[100];
GStack<Object> ObjectStack = new GStack<Object>();
GenericMethodEx.toStack(oArray, objectStack); // 타입 매개변수 T를 Object로 유추한다.
```

컴파일러가 toStack()의 호출문으로부터 타입 매개 변수 T를 String으로 유추하는 경우이다.

```
String[] sArray = new String[100];
GStack<String> stringStack = new GStack<String>();
GenericMethodEx.toStack(sArray,stringStack); // 타입 매개변수 T를 String으로 유추한다.
```

타입 매개변수 T를 Object로 유추한다.

```
GenericMethodEx.toStack(sArray,objectStack)
```

sArray는 String[] 타입이며, objectStack은 GStack<Object>이다.
Object가 String의 슈퍼클래스이므로 컴파일러는 Object 타입으로 유추한다.

제너릭의 장점
1. 동적으로 타입이 결정되지 않고 컴파일 시에 타입이 결정되므로 보다 안전한 프로그래밍 가능 
2. 런타임 타입 충돌 문제 방지
3. 개발 시 타입 캐스팅 절차 불필요
4. ClassCastException 방지

- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
