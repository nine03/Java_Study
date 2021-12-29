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
int len = v.size(); // 벡터의 크기. 벡터에 존재하는 요소 객체의 수
</pre></code>
- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
