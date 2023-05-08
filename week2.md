반복문 (循环语句)

for문 (for 语句)
<pre><code>
for문 문법
for(초기문; 조건식; 반복 후 작업) {
           작업문
}
</pre></code>

초기문 (初始化)

for 문에서 초기문은 주로 조건식에서 사용하는 변수를 초기화한다. (在for循环中，初始化主要初始化条件表达式中使用的变量。)

(设置初始条件，只执行一次。可以为零一，一个或多个变量设置初值。)

초기문 특징 (初始化 特征)

- 초기문은 시작할 때 한번만 수행된다. (初始化在开始时只执行一次。)
- 콤마(,)로 분리하여 여러 문장을 나열할 수 있다. (可以将几个句子分成逗号（，）来列出。)
- 초기문은 빈 상태로 두어도 되지만 끝에 세미콜론(;)은 있어야한다. (初始化可以保留为空，但结尾应该有分号(;)。)

조건식 (条件表达式)

조건식에는 논리형 변수나 논리연산을 사용한다. (条件表达式使用逻辑变量或逻辑运算。)
(循环条件表达式，用来判断是否继续循环。在每次执行循环体前先执行此表达式，决定是否继续执行循环。)

반복 후 작업 (循环变量增值)

for 문의 작업문이 실행된후  반복 후 작업문이 실행된다.
(作为循环的调整，列如使循环变量增值，它是在执行完循环体后才进行的。)

while 문 (while 语句)

while 문의 조건식은 for 문의 경우와 동일하며, true인 동안 작업문의 실행 반복하고, false가 되면 while문을 벗어난다. (while语句的条件表达式与for语句的条件表达式相同，在true期间重复执行语句，在false期间保留while语句。)

<pre><code>
while 문 문법
while(조건식) {
      작업문;
}
</pre></code>

do - while 문 (do - while 语句)

do - while 문의 조건식은 while 문과 동일하며 조건식이 없으면 컴파일 오류가 발생한다. (do while语句的条件表达式与while语句相同，如果没有条件表达式，则会发生编译错误。)

<pre><code>
do - while 문 문법
do {
      작업문;
} while(조건식);
</pre></code>

continue 문 (continue 语句)

continue 문은 반복문을 빠져나가지 않으면서 즉시 다음 반복으로 넘어가고자할 때 사용된다. (contine语句用于在不离开迭代语句的情况下立即移动到下一个迭代。)

break 문 (break 语句)

break 문은 하나의 반복문을 즉시 벗어날 때 사용한다. (break语句用于立即退出单个循环语句。)

배열 (数组)

배열은 인덱스와 인덱스에 대응하는 데이터들로 이루어진 연속적인 자료 구조로서, 같은 종류의 데이터들이 순차적으로 저장된다. (数组是由索引和对应于该索引的数据组成的连续数据结构，其中相同种类的数据被顺序存储。)

<pre><code>
배열 선언 
int intArray [];   
int : 배열 타입
intArray : 배열에 대한 레퍼런스 변수
[] : 배열 선언

배열 생성
intArray = new int [5];
intArray : 배열에 대한 레퍼런스 변수
new : 배열 생성
int : 배열 타입
[5] : 원소 

배열 초기화
int intArray[] = {4, 3, 2, 1, 0};
double doubleArray[] = {0.01, 0.02, 0.03, 0.04};

배열 인덱스와 배열 원소 접근
int intArray[] = new int[5]; // 원소가 5개인 배열 생성. 인덱스는 0 ~ 4까지 가능
int intArray[0] = 5;  // 원소 0에 5저장
int intArray[3] = 6;  // 원소 3에 6저장
int n = intArray[3];  // 원소 3의 값을 읽어 n에 저장. n은 6이된다.

레퍼런스 치환과 배열 공유
int intArray[] = new int[5];
int myArray[] = intArray // 레퍼런스 치환. myArray는 intArray와 동일한 배열 참조

배열의 크기, length 필드
intArray[];
intArray = new int[5];
int size = intArray.length; // size는 5

for - each 문

for(변수 : 배열레퍼런스) {
        반복 작업문;
}

배열 
ex)

int []n = {1,2,3,4,5};
int  sum = 0;
for(int k : n) { // n.length번 반복. k는 n[0], ... , n[4]로 번갈아 반복
           sum += k;
}
System.out.println("합은 " + sum);

 문자열 배열 
 ex)
 
 String names[] = {"사과","배","바나나","체리","딸기","포도"};
 for(String s : names) { // 반복할 때마다 s는 name[0], ... , name[5]로 설정
           System.out.print(s + " ");
 }
 
 문자열 나열 
 ex)
 
 enum week {월, 화, 수, 목, 금, 토, 일}
 for(week day : week.values()) { // 반복될 때마다 day는 월, 화, 수, 목, 금, 토, 일로 설정
           System.out.println(day + "요일");
 }
</pre></code>

2차원 배열 (二维数组)

2차원 배열의 선언과 생성 (二维数组声明和创建。)

1차원 배열과 마찬가지로 2차원 배열에서도 레퍼런스 변수 선언 후 배열을 생성한다. (像一维数组一样，二维数组在引用变量声明之后生成数组。) 

<pre><code>
2차원 배열의 레퍼런스 변수 선언방법
int intArray [][];
char charArray [][];
double doubleArray [][];

int [][] intArray;
char [][] charArray;
double [][] doubleArray;

intArray = new int [2][5]; // 2행 5열의 2차원 배열 생성
charArray = new char [5][5]; // 5행 5열의 2차원 배열 생성
doubleArray = new double [5][2]; // 5행 2열의 2차원 배열 생성 

2차원 배열도 레퍼런스 변수 선언과 배열 생성을 동시에 할 수 있다.
int intArray [][] = new int [2][5];
char charArray [][] = new char [5][5];
double doubleArray [][] = new double [5][2];

2차원 배열의 초기화
int intArray [][] = {{0,1,2},{3,4,5},{6,7,8}};
char charArray [][] = {{'a','b','c'},{'d','e','f'}};
double doubleArray = {{0.01,0.02},{0.03,.0.04}};

비정방형 배열
int i [][]; // 2차원 배열의 레퍼런스 변수 i 선언
i = new int [4][]; // 각 행을 가리키는 레퍼런스 배열 생성
i[0] = new int [1]; // 첫째 행에 1개 크기의 배열 생성
i[1] = new int [2]; // 둘째 행에 2개 크기의 배열 생성
i[2] = new int [3]; // 셋째 행에 3개 크기의 배열 생성
i[3] = new int [4]; // 넷째 행에 4개 크기의 배열 생성
</pre></code>

메소드에서 배열 리턴

메소드에서 어떤 배열이든지 리턴하면, 배열 공간 전체가 아니라 배열에 대한 레퍼런스만 리턴된다.
<pre><code>
int[] makeArray() {
      int temp[] = new int[4];
      return temp;
}

int : 리턴 타입
makeArray : 메소드 이름
temp : 배열 리턴

int [] intArray; // makeArray()의 리턴 타입과 동일한 타입 선언
intArray = makeArray(); // makeArray() 메소드가 리턴하는 배열 받음
</pre></code>

예외처리 (异常)
자바에서 오동작이나 결과에 악영향을 미칠 수 있는 실행 중 발생한 오류를 예외라고한다. (异常是在执行过程中发生的错误，可能会对Java中的故障或结果产生不利影响。)

<pre><code>
실행 중에 예외가 발생하는 경우
정수를 0으로 나누는 경우
배열의 크기보다 큰 인덱스로 배열의 원소를 접근하는 경우
존재하지 않는 파일을 읽으려고 하는 경우
정수 입력을 기다리는 코드가 실행되고 있을 때, 사용자가 문자를 입력한 경우
</pre></code>

try - catch - finally 문 (try - catch - finally 语句)

<pre><code>
try - catch - finally 문 문법
try {
     예외가 발생할 가능성이 있는 실행문(try 블록)
} catch(처리할 예외 타입 선언) {
      예외 처리문(catch 블록)
} finally {
      예외 발생 여부와 상관없이 무조건 실행되는 문장(finally 블록)
}

자바의 예외 클래스
예외 타입(예외 클래스)               예외 발생 경우                                   패키지
ArithmeticException                 정수를 0으로 나눌때 발생                        java.lang
NullPointerException                null 레퍼런스를 참조할 때 발생                  java.lang
ClassCastException                  변환할 수 없는 타입으로 객체를 변환할 때 발생    java.lang
OutOfMemoryError                    메모리가 부족한 경우 발생                       java.lang
ArrayIndexOutOfBoundsException      배열의 범위를 벗어난 접근 시 발생               java.lang
IllegalArgumentException            잘못된 인자 전달 시 발생                        java.lang
IOException                         입출력 동작 실패 또는 인터럽트 시 발생          java.io
NumberFormatException               문자열이 나타태는 숫자와 일치하지 않는 
                                    타입의 숫자로 변환시 발생                       java.util
InputMismatchException              Scanner 클래스의 nextInt()를 호출하여 정수로
                                    입력받고자 하였지만, 사용자가 'a'등과 같이
                                    문자를 입력한 경우

int intArray [] = new int[5]; // 인덱스는 0 ~ 4 까지 가능
try {
     intArray[3] = 2;  // 예외 발생하지 않음
     intArray[6] = 5;  // 예외 발생
} catch(ArratIndexOutOfBoundsException e) { // 객체 e에 예외 정보가 넘어옴
      System.out.println("배열의 범위를 초과하여 원소를 접근하였습니다.");
}
</pre></code>

- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
