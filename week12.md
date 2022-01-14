멀티태스킹(multitasking) 

멀티태스킹이란 멀티 + 태스킹의 합성어로서 다수의 작업을 동시에 처리하는 것을 말한다. 

멀티태스킹 프로그램 

응용프로그램은 보통 하나의 작업(태스크)만 하는 경우가 대부분이지만, 큰규모의 응용프로그램은 많은 경우 여러 작업(태스크)을 동시에 실핸한다. 

스레드

스레드(Thread)는 직역하면 바느질할 때 사용하는 '실'이다. 바늘에 꿰어진 하나의 실로 하나의 바느질 작업만 할 수 있다. 한 사람이 두 개의 바느질을 동시에 하려면 실(Thread)이 따로 필요하다. 컴퓨터에서 사용하는 스레드는 Thread of control의 준말로서 프로그램 코드를 실행하는 하나의 실 혹은 제어의 개념이다.

멀티프로세싱(multi-processing) 

멀티프로세싱은 하나의 응용프로그램을 여러 개의 프로세스(process)로 구성하여 각 프로세스가 하나의 작업을 처리하도록 하는 기법이다. 각 프로세스는 고유한 메모리 영역을 보유하고 독립적으로 실행된다.

멀티스레딩(multi-threading)

멀티스레딩은 하나의 응용프로그램을 동시처리가 가능한 여러 작업으로 분할하고 작업의 개수만큼 스레드를 생성하여 각 스레드로 하여금 하나의 작업을 처리하도록 하는 기법이다.

자바 스레드 

자바 스레드는 다른 운영체제의 스레드와 크게 다르지 않다. 응용프로그램 개발자 입장에서 스레드를 만들기 위해서는 스레드로 실행될 프로그램 코드를 작성하여야 한다.

자바 스레드를 만들기 위해 개발자는 다음 두 가지 작업을 하여야 한다.

Thread 클래스 이용

Runnable 인터페이스 이용

```
Thread()                                  스레드 객체 생성
Thread(Runnable target)                   Runnable 객체인 target을 이용하여 스레드 객체 생성
Thread(String name)                       이름이 name인 스레드 객체 생성
Thread(Runnable target, String name)      Runnable 객체를 이용하며, 이름이 namedls 스레드 객체 생성

void run()                                스레드 코드로서 JVM에 의해 호출된다. 개발자는 반드시 이 메소드를 오버라이딩하여 
                                          스레드 코드를 작성하여야 한다. 이 메소드가 종료하면 스레드도 종료한다.


void start()                              JVM에게 스레드 실행을 시작하도록 요청
void interrupt()                          스레드 강제 종료
static void yield()                       다른 스레드에게 실행을 양보한다. 이때 JVM은 스레드 스케줄링을 시행하며 다른 스레드를
                                          링을 시행하며 다른 스레드를 선택하여 실행시킨다.
void join()                               스레드가 종료할 때까지 기다린다. 
long getId()                              스레드의 ID 값 리턴
String getName()                          스레드의 이름 리턴 
int getPriority()                         스레드의 우선순위 값 리턴. 1에서 10 사이 값
void setPriority(int n)                   스레드의 우선순위 값을 n으로 변경
Thread State getState()                   스레드의 상태 값 리턴
static void sleep(long mills)             스레드는 mills 시간 동안 잔다. mills의 단위는 밀리초
static Thread currentThread()             현재 실행 중인 스레드 객체의 레퍼런스 리턴
```

스레드 클래스 작성 : Thread 클래스 상속 

```
class TimerThread extends Thread { // Thread
  ...............................
}
```
스레드 코드 작성 : run() 메소드 오버라이딩

```
class TimerThread extends Thread {
@Override
public void run() {   // run() 오버라이딩
    ..................
  }
}
```

만일 run()을 오버라이딩하지 않으면 Thread 클래스에 작성된 run()이 실행되며, 이 run()은 아무도 일도 하지 않고 단순 리턴하도록 작성되어 있어 스레드가 바로 종료된다.

스레드 객체 생성 

```
TimerThread th = new TimerThread(); // 스레드 객체 생성
```

스레드 객체를 생성한 것으로 스레드가 작동하는 것은 아니다. 스레드 객체의 생성은 어디까지나 하나의 객체 생성에 불과하다. 스레드는 다른 객체와 달리 JVM에 등록되어 JVM에 의해 스케줄링되어야 비로소 작동되는 것이다.

스레드 시작 : start() 메소드 호출

```
th.start();
```

start() 메소드는 Thread 클래스에 구현된 메소드이며 개발자가 오버라이딩하면 안된다. start() 메소드는 생성된 스레드 객체를 스케줄링이 가능한 상태로 전환하도록 JVM에게 지시한다. TimerThread는 Thread를 상속받은 클래스로서 run()을 오버라이딩하여 스레드 코드를 구현한다. run() 메소드는 무한 루프를 돌면서 1초 간격으로 콘솔에 초 시간을 출력한다. <br>
sleep(1000); 코드는 TimerThread 스레드가 1000ms 동안 잠을 자는 코드이다. 한 스레드가 잠을 자면 JVM은 다른 스레드를 실행시킨다. 스레드는 잠을 자는 사이에 발생하는 InterruptedException 예외 처리할 try-catch 블록을 반드시 가지고 있어야 한다.

Runnable 인터페이스로 스레드 만들기

Runnable은 클래스가 아닌 인터페이스로서 경로명 java.lang.Runnable이며, 다음과 같이 추상 메소드 run() 하나만 가지고 있다.

```
interface Runnable {
  public void run();
}
```

스레드 클래스 선언 : Runnable 인터페이스 구현

```
class TimerRunnable implements Runnable {
  ..................................
}
```
스레드 코드 작성 : run() 메소드 오버라이딩

```
class TimerRunnable implements Runnable {
  @Override
  public void run() { // run() 메소드 오버라이딩
    ...................
  }
}
```

스레드 객체 생성 

```
Thread th = new Thread(new TimerRunnable);
```

스레드 시작 : start() 메소드 호출

```
th.start();
```

![ca5c342ba538e6a943efa34bb91fe4f](https://user-images.githubusercontent.com/60682087/149551356-8e88069d-a3bb-4d54-9236-4a1be629ece6.png)

스레드 정보

```
스레드 이름                스트링               스레드의 이름으로서 사용자가 지정
스레드 ID                  정수                스레드 고유의 식별자 번호
스레드의 PC(Program Count) 정수                현재 실행 중인 스레드 코드의 주소
스레드 상태                정수                NEW, RUNNABLE,WAITING,TIMED_ WAITING, BLICK, TERMINATED 등 6개의 상태 중 하나
스레드 우선순위            정수                스레드 스케줄링 시 사용되는 우선순위 값으로서 1 ~ 10 사이의 값이며 10이 최상위 우선순위
스레드 그룹                정수                여러 개의 자바 스레드가 하나의 그룹을 형성할 수 있으며, 이 경우 스레드가 속한 그룹
스레드 레지스터 스택        메모리 블록         스레드가 실행되는 동안 레지스터들의 값
```

데몬 스레드(daemon thread)와 사용자 스레드(user thread)

데몬 스레드인데 응용프로그램이 실행되는 동안 관리를 위해 존재하는 스레드로, 가비지 컬렉션 스레드가 대표적이다. 

사용자 스레드로서 응용프로그램이 생성한 스레드이다.

스레드 상태 

스레드는 JVM에 있어 생명체와 같다.

![dd05581ae8633c119dc79b6dfef58e4](https://user-images.githubusercontent.com/60682087/149559740-bc1333c1-0e8c-4ac3-9a3b-f5325ce0f494.png)

스레드 상태 6가지

NEW

스레드가 생성되었지만 아직 실행할 준비가 되지 않은 상태이다. start() 메소드가 호출되면 RUNNABLE 상태가 된다.

RUNNABLE

스레드가 현재 실행되고 있거나, 실행 준비되어 스케줄링을 기다리는 상태이다.

TIMED_WAITING

스레드가 sleep(long n)을 호출하여 n밀리초 동안 잠을 자는 상태이다.

BLOCk

스레드가 I/O 작업을 실행하여 I/O 작업의 완료를 기다리면서 멈춘(blocked) 상태이다. 스레드가 I/O 작업을 실행하면 JVM이 자동으로 현재 스레드를 BLOCk 상태로 만들고 다른 스레드를 스케줄링한다.

WAITING

스레드 어떤 객체 a에 대해 a.wait()을 호출하여, 다른 스레드가 a.notify(), a.notifyAll()을 불러줄 때까지 무한정 기다리는 상태이다.

TERMINATED

스레드가 종료한 상태이다. 더 이상 다른 상태로 변이할 수 없다.

스레드 우선순위와 스케줄링 

JVM은 철저히 우선순위(priority)를 기반으로 스레드를 스케줄링한다. 가장 높은 우선순위의 스레드를 먼저 실행시킨다. 동일한 우선순위인 경우에는 돌아가면서 실행시킨다. 

최대값(MAX_PRIORITY) = 10 <br>
최소값(MIN_PRIORITY) = 1 <br>
보통값(NORMAL_PRIORITY) = 5

자바 응용프로그램이 실행될 때 처음으로 생성되는 main 스레드는 보통 값(5)의 우선순위로 태어나며, 자식 스레드는 생성될 때 부모 스레드의 우선순위 값을 물려받기 때문에 main 스레드의 모든 자식 스레드는 보통값 5)의 우선순위를 가지고 탄생된다. 하지만 다음 메소드를 이용하면 우선순위를 값을 바꿀수 있다.

```
void setPriority(int newPriority) // newPriority로 스레드의 우선순위 값 변경
```

main()을 실행하는 main 스레드 

JVM은 자바 응용프로그램을 실행하기 직전, 사용자 스레드를 하나 만들고, 이 스레드로 하여금 main() 메소드를 실행하도록 한다. 메인 스레드이고 실행 시작 주소는 main() 메소드의 첫 코드가 된다. 자바 응용프로그램의 main() 메소드가 실행되는 순간 2개의 스레드가 존재하는 셈이다. 하나는 main 스레드이고 다른 하나는 JVM 내에 자동으로 생성된 가비지 컬렉션 스레드이다.

스레드 종료

스레드는 다음 예와 같이 run() 메소드가 실행 도중 리턴하거나 run()을 완전히 실행하고 리턴하면 종료된다.

```
public void run() {
  ...................
  return;  // 스레드는 스스로 종료한다.
  ...................
}
```

강제 종료 

```
B.interrupt(); // 스레드 B를 종료시킨다.
```

flag를 이용한 종료 

TimerThread 클래스에 boolean 타입의 flag 필드와 finish() 메소드를 추가한다. finish() 메소드는 다른 스레드에서 호출하도록 만든 것으로 flag 값을 true로 설정하여 스레드가 종료해야 함을 표시한다. main 스레드가 TimerThread 스레드를 종료시키고자 하는경우, TimerThread 클래스의 finish() 메소드를 호출한다. 한편 TimerThread 스레드는 주기적으로 flag의 값이 true인지 검사하여 true이면 return을 실행하여 스스로 종료한다. 

![7f90a85b7d8fb1b0af254384b1128e6](https://user-images.githubusercontent.com/60682087/149566711-e9c5aadd-c377-4223-b67d-ce9ec3b1816f.png)

스레드 동기화(Thread Synchronization)

스레드 동기화의 필요성 

멀티스레드는 다수의 작업을 동시에 실행시키는 응용프로그램 작성 기법이다. 하지만 멀티스레드를 사용할 때 주의를 기울려야한다. 다수의 스레드가 공유 자원 혹은 공유 데이터에 동시에 접근할 때 예상치 못한 결과를 낳을 수 있다. 다수의 스레드가 공유 자원에 동시에 접근하는 두사례가 있다. 

1. 공유 프린터에 동시 접근하는 경우 <br>
2. 공유 집계판에 동시 접근하는 경우 <br>




- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
