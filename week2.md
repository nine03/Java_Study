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


- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
