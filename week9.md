이벤트 기반 프로그래밍

이벤트 기반 프로그래밍은 이벤트의 발생에 의해 프로그램 실행 흐름이 결정되는 방식의 프로그래밍 패러다임이다. 이벤트는 키 입력, 마우스 클릭, 마우스 드래그 등 사용자의 액션이나, 센서 등외부 장치로부터의 입력, 네트워크를 통한 데이터 수신, 다른 스레드나 프로그램으로부터의 메시지 수신등에 의해 발생한다. 이벤트 기반 응용프로그램은 각 이벤트를 처리하는 이벤트 리스너(event listener)들을 보유하며, 이벤트가 발생할 때마다 리스너가 실행된다.

이벤트 리스너(event listener)

이벤트 리스너는 이벤트를 처리하는 프로그램 코드로서 컴포넌트에 연결되어 있어야 작동된다.

<pre><code>
1. 사용자가 마우스로 화면의 New 버튼을 클릭한다.
2. 버튼 클릭은 운영체제의 마우스 드라이버를 거쳐 자바 가상 기계에 전달된다.
3. 자바 가상 기계는 이벤트 분배 스레드(Event Dispatch Thread)에게 마우스 클릭에 관한 정보를 보낸다.
4. 이벤트 분배 스레드는 이벤트(ActionEvent) 객체를 생성한다. 이벤트 객체는 이벤트에 관한 여러 정보를 담은 객체이다. 이벤트 객체 내에 저장되는 정보 중, 특별히 이벤트를 발생시킨 컴포넌트를 이벤트 소스(Event Source)라고 부른다. 여기서 이벤트 소스는 'NEW'글자가 새겨진 JButton 컴포넌트이다.
5. 이벤트 분배 스레드는 JButton에 연결된 '이벤트 리스너4'를 찾아 호출한다.
6. 이벤트 분배 스레드는 '이벤트 리스너4'로 부터 리턴한 후 다음 이벤트를 기다린다.
</pre></code>

이벤트 소스 

이벤트를 발생시킨 GUI 컴포넌트이다.

이벤트 객체 

발생한 이벤트에 대한 정보(이벤트 종류, 이벤트 소스, 화면 좌표, 마우스 버튼 종류, 눌러진 키)를 담는 객체로서, 이벤트에 따라 서로 다른 정보가 저장된다.

이벤트 리스너(Event Listener)

이벤트를 처리하는 코드로서 컴포넌트에 등록되어야 작동 가능하다.

이벤트 분배 스레드(Event Dispatch thread)

이벤트 기반 프로그래밍의 핵심 요소로서 무한 루프를 실행하는 스레드이다. 자바 가상 기계로부터 이벤트의 발생을 통지받아, 이벤트 소스와 이벤트 종류를 결정하고 이에 따라 적절한 이벤트 객체를 생성하고 이벤트 리스너를 찾아 호출한다.

이벤트 객체

이벤트 객체는 현재 발생한 이벤트에 관한 정보를 가진 객체이며, 이벤트 리스너에게 전달된다. 모든 이벤트 객체들은 java.util.EventObject 클래스를 상속받으며, java.awt.event와 javax.swing.event 패키지에 구현되어 있다. 

<pre><code>
import java.awt.event.*;
import javax.swing.event.*;
</pre></code>

이벤트 객체 정보

- 이벤트 종류
- 이벤트 소스
- 화면 내 이벤트 발생한 마우스 좌표
- 컴포넌트 내 이벤트가 발생한 마우스 좌표
- 버튼이나 메뉴 아이템에 이벤트가 발생한 경우 버튼이나 메뉴 아이템의 문자열 
- 클릭된 마우스 버튼 번호
- 마우스의 클릭 횟수
- 키가 눌러졌다면 키의 코드 값과 문자 값
- 체크박스, 라디오버튼에 이벤트가 발생하였다면 체크 상태

이벤트 객체는 메소드를 통해 이벤트 정보를 제공한다. MouseEvent 객체는 눌러진 마우스 버튼 번호(getButton()), 마우스 포인터 좌표(getPoint(), getX(), getY()) 등을 알려주는 메소드가 있다. 이 중 모든 이벤트가 객체에 있고, 이벤트 리스너에서 가장 많이 사용되는 getSource()메소드이다.


Object getSource()

getSource()는 현재 발생한 이벤트의 소스 컴포넌트의 레퍼런스를 리턴한다.

Object이므로 캐스팅해서 사용하는데, 예를들어 버튼이 눌러진 경우라면 다음과 같이 캐스팅하면된다.

<pre><code>
// event는 이벤트 객체
JButton b = (JButton)event.getSource(); // b는 이벤트가 발생한 버튼의 레퍼런스
</pre></code>

이벤트 객체와 이벤트 소스

이벤트 객체 : MouseEvent

이벤트 소스 : Component
Component를 상속받은 모든 스윙 컴포넌트에 대해 마우스 이벤트 발생 가능

이벤트가 발생하는 경우 : 총 7가지 
마우스버튼이 눌러지는 순간, 눌러진 마우스 버튼이 떼어질때, 마우스 버튼이 클릭될 때, 컴포넌트 위에 마우스가 올라갈 때, 마우스가 컴포넌트 위에서 드래그될 때, 마우스가 컴포넌트 위에서 움직일 때

![ed155473c6b8f61e24a404d7e713829](https://user-images.githubusercontent.com/60682087/149149508-e7734cc5-ee58-433b-9017-56a3ad085735.png)

리스너 인터페이스

이벤트 리스너는 이벤트를 처리하는 자바 프로그램 코드로서 클래스로 만든다. JDK와 같이 이벤트 리스너 인터페이스(interface)를 제공하며, 개발자는 이 인터페이스를 상속받고 추상 메소드를 모두 구현하여 이벤트 리스너를 작성한다.

<pre><code>
interface ActionListener {
  public void actionPerformed(ActionEvent e); // Action 이벤트 발생 처리 
}
</pre></code>

버튼을 누르는 Action 이벤트가 발생하면 actionPerformed(ActionEvent e) 메소드가 호출되고, 이때 ActionEvent 객체가 인자로 전달된다.

MouseListener 인터페이스는 다음과 같이 5개의 메소드를 가지고 있으며, 각 메소드는 마우스의 조작에 따라 발생하는 이벤트를 처리한다.

<pre><code>
interface MouseListener {
  public void mousePressed(MouseEvent e); // 마우스 버튼이 눌러지는 순간 
  public void mouseReleased(MouseEvent e); // 눌러진 마우스 버튼이 떼어지는 순간
  public void mouseClicked(MouseEvent e); // 마우스가 클릭되는 순간
  public void mouseEntered(MouseEvent e); // 마우스가 컴포넌트 위에 올라가는 순간
  public void mouseExited(MouseEvent e); // 마우스가 컴포넌트 위에서 내려오는 순간 
}
</pre></code>

리스너 인터페이스들은 java.awt.event 패키지에 구현되어 있으므로 이벤트 리스너 작성하기 위해서는 import java.awt.event.*; 문이 필요하다.


![29662232354e43f10cf26be9b647b81](https://user-images.githubusercontent.com/60682087/149154427-e3d53413-107a-4f48-84e9-6a3fc96fdcf1.png)

이벤 리스너 작성 과정

1. 이벤트와 이벤트 리스너 선택 - 목적에 적합한 이벤트와 리스너 인터페이스 선택
2. 이벤트 리스너 클래스 작성 - 리스너 인터페이스를 상속받는 클래스를 작성하고 추상 메소드 모두 구현 
3. 이벤트 리스너 등록 - 이벤트를 받을 스윙 컴포넌트에 이벤트 리스너 등록

이벤트와 이벤트 리스너 선택 

이벤트 : Action 이벤트
이벤트 리스너 : ActionListener
이벤트 객체 : ActionEvent

이벤트 리스너 클래스 작성 

ActionListener 인터페이스를 상속받은 MyActionListener 클래스를 선언하고, 한 개뿐인 추상 메소드 actionPerformed(ActionEvent e)를 다음과 같이 작성한다.

<pre><code>
class MyActionListener implements ActionListener {
  public void actionPerformed(ActionEvent e) { // 버튼 클릭 시 호출되는 메소드
    JButton b = (JButton)e.getSource(); // 클릭된 버튼 알아내기
      if(b.getText().equals("Action")) // 버튼의 문자열이 "Action"인지 비교
          b.setText("액션");
       else
          b.setText("Action");
  }
}
</pre></code>

이벤트 리스너 등록 

이벤트 리스너가 작동하기 위해서는 MyActionListener의 객체를 생성하여 이벤트를 처리할 버튼 컴포넌트에 등록해야 한다.

<pre><code>
MyActionListener listener = new MyActionListener(); // 리스너 객체 생성
btn.addActionListener(listener); // 리스너 등록

일반적으로 컴포넌트 component에 이벤트 리스너를 등록하기 위해서는 다음 메소드를 사용한다.
component.addXXXListener(listener);
</pre></code>

오류 
<pre><code>
JButton b = new JButton("test");
b.addItemListener(listener); // 오류. JButton 클래스에 addItemListener() 없음

JScrollBar s = new JScrollBar();
s.addActionListener(listener); // 오류. JScrollBar 클래스에 addActionListener() 없음 
</pre></code>

JList Mouse

<pre><code>
JList list = new JList();
list.addMouseListener(listener);
</pre></code>

이벤트 리스너 작성 방법

독립 클래스로 이벤트 리스너 작성 
이벤트 리스너 클래스를 독립적으로 작성하는 방법으로서, 가장 전형적인 방법이다.

내부 클래스(inner class)로 이벤트 리스너 작성
이벤트 리스너를 내부 클래스(inner class)로 작성하는 방법이다.

익명 클래스(anonymous class)로 이벤트 리스너 작성
익명 클래스는 이름 없이 만들어진 클래스이다. 익명 클래스는 다음과 같이 new와 함께 사용되어 바로 객체를 생성하는데 사용된다.

<pre><code>
new 익명클래스의슈퍼클래스(생성자인자들) {
  // 멤버 구현 
}
</pre></code>

어댑터(Adapter)클래스

리스너 인터페이스를 상속받아 이벤트 리스너를 구현할 때 리스너 인터페이스의 메소드를 모두 구현하여야 하는 부담이 있다. 자바의 JDK에는 이런 부담을 줄여주기 위해 리스너 인터페이스를 미리 구현해 놓은 클래스를 제공하는데 이것이 바로 어댑터 클래스(Adapter)이다.

<pre><code>
  class MouseAdapter implements MouseListener, MouseMotionListener, MouseWheelListener {
	public void mousePressed(MouseEvent e) { }
	public void mouseReleased(MouseEvent e) { }
	public void mouseClicked(MouseEvent e) { }
	public void mouseEntered(MouseEvent e) { }
	public void mouseExited(MouseEvent e) { }
	public void mouseDragged(MouseEvent e) { }
	public void mouseMoved(MouseEvent e) { }
	public void mouseWheelMoved(MouseWheelEvent e) { }
} 
</pre></code>

![905c29db7057e0299f7f85383bbea96](https://user-images.githubusercontent.com/60682087/149161692-95530825-88d5-43b7-8ec6-82c88b611391.png)

KeyEvent와 KeyListener

Key 이벤트와 포커스

Key 이벤트는 사용자가 키를 입력할 때 발생하는 이벤트이며, 모든 컴포넌트가 Key 이벤트를 받을 수 있다. 그러나 응용프로그램 내에 포커스(focus)를 가진 컴포넌트가 키 입력을 독점하기 떄문에, 현재 포커스를 가진 컴포넌트에만 Key 이벤트가 전달된다. 

포커스

포커스는 키 입력의 독점권을 뜻한다. 버튼을 누르기 위해 <Enter> 키를 입력하더라도 버튼이 포커스를 가지고 있지 않다면 Key 이벤트를 받을 수 없다. 어떤 컴포넌트에게 키를 입력하고자 하면 <Tab> 키나 마우스 클릭으로 포커스를 그 컴포넌트에게 이동시켜야 한다. 스윙 응용프로그램에서는 강제로 임의의 컴포넌트에 포커스를 주기 위해 다음 두 코드가 모두 필요하다.

<pre><code>
component.setFocusable(true); // component가 포커스를 받을 수 있도록 설정한다.
component.requestFocus(); // component에게 포커스를 주어 키 입력을 받을 수 있게 함
</pre></code>
	
컴포넌트에 포커스 주기 

<pre><code>
setVisible(true); // 스윙 프레임 출력
component.setFocusable(true);
component.requestFocus(); 
</pre></code>
	
<pre><code>
component.addMouseListener(new MouseAdapter() {
	public void mouseClicked(MouseEvent e) {
		Component c = (Component)e.getSource(); // 클릭된 컴포넌트
		c.setFocusable(true);
		c.requestFocus(); 
	}
}); // 예제 10-8에서 활용하였음
</pre></code>

Key 이벤트와 KeyListener

KeyListener 인터페이스는 3개의 추상 메소드로 구성된다. keyPressed()는 키를 누르는 순간에, keyReleased()는 누른 키를 떼는 순간에 호출되며, 문자 키(유니코드)인 경우에는 누른 키가 떼어지는 순간 keyTyped()가 추가적으로 호출된다.

유니코드(Unicode)는 전 세계의 모든 문자를 컴퓨터에서 일관되게 표현하고 다루고자 설계된 국제 산업 표준이다.

	
키 이벤트 리스너 달기 
컴포넌트에 키 이벤트 리스너를 등록하기 위해서는 다음과 같이 addKeyListener() 메소드를 이용한다.
	
<pre><code>
component.addKeyListener(myKeyListener);
</pre></code>
	
<pre><code>
Key 이벤트가 발생하는 경우    KeyListener의 메소드           리스너
키를 누르는 순간              void keyPressed(KeyEvent e)   KeyListener
누른 키를 떼는 순간           void keyReleased(KeyEvent e)  KeyListener
누른 키를 떼는 순간           void keyTyped(KeyEvent e)     KeyListener
(유니코드 키 경우에만 적용)
</pre></code>
	
입력된 키 판별

키 이벤트가 발생하면 입력된 키 정보가 KeyEvent 객체에 담겨져 리스너에게 전달된다. KeyEvent 객체의 다음 2개의 메소드를 통해 입력된 키를 판별할 수 있다.
		
char KeyEvent.getKeyChar()

입력된 키의 문자코드를 리턴하며, 유니코드 키가 아닌 경우 KeyEvent.CHAR_UNDEFINED를 리턴한다. 다음은 q키가 눌러지는 순간 프로그램을 종료하는 코드이다. getKeyChar()의 리턴 값과 문자'q'를 서로 비교하면 된다.

<pre><code>
public void keyPressed(KeyEvent e) {
	if(e.getKeyChar() == 'q')
		System.exit(0); // 키 q가 눌러지면 프로그램을 종료한다.
}
</pre></code>

int KeyEvent.getKeyCode()

이 메소드는 유니코드 키를 포함한 모든 키에 대해 정수형의 키 코드(key code) 값을 리턴한다. 키 코드는 운영체제나 하드웨어에 따라 서로 다를 수 있기 때문에, 입력된 키를 판별하기 위해서는 반드시 getKeyCode()가 리턴한 키 코드와 가상 키(Virtual Key) 값을 비교해야 한다. 가상 키는 KeyEvent 클래스에 VK_로 시작하는 static 상수로 선언되어 있다.


<pre><code>
public void keyPressed(KeyEvent e) {
	if(e.getKeyCode() == KeyEvent.VK_F5)
	System.exit(0);
}
</pre></code>

![f5d18edf2ec48144cfe6c93559428c6](https://user-images.githubusercontent.com/60682087/149168417-18aa2c3b-d149-424d-b26b-7ed356f80788.png)

KeyEvent와 KeyListener의 활용

이 절에서는 KeyListener, KeyEvent 객체, getKeyChar(), getKeyCode() 등을 활용할 수 있다.

<pre><code>
static String KeyEvernt.getKeyText(int KeyCode);
</pre></code>

Mouse 이벤트 

Mouse 이벤트는 사용자의 마우스 조작에 따라 총 8가지 경우에 발생한다. 이중에서 5가지 경우는 MouseListener의 메소드가 호출되고, 2가지 경우는 MouseMotionListener의 메소드가, 나머지 1가지는 MouseWheelListener의 메소드가 호출된다. 모든 스윙 컴포넌트가 Mouse 이벤트를 받을 수 있으며, Mouse 이벤트가 발생하면 MouseEvent 객체나 MouseWheelEvent객체가 리스너의 메소드에 전달된다.

![f64d1d89bac1f4a609d3866f039866f](https://user-images.githubusercontent.com/60682087/149171216-b7fd640f-f5ff-4f13-973e-29a635f5dd55.png)

마우스 리스너 달기 

<pre><code>
component.addMouseListener(myMouseListener);
</pre></code>

동일한 컴포넌트가 마우스 드래깅(mouseDragged())과 마우스 무브(mouseMoved()) 이벤트도 함께 처리하고자 하면, 다음과 같이 MouseMotion 리스너를 따로 등록해야 한다.

<pre><code>
component.addMouseMotionListener(myMouseMotionListener);
</pre></code>

MouseEvent 객체 

MouseEvent 객체는 Mouse 이벤트나 MouseMotion 이벤트 정보를 제공하는 객체이다. MouseEvent 객체의 메소드를 이용하여 이벤트 정보를 얻을수 있다.

마우스 포인터의 위치

<pre><code>
int getX() // 마우스 포인터의 x 위치 리턴
int getY() // 마우스 포인터의 y 위치 리턴
Point getPoint() // 마우스 포인터의 위치를 Point 객체로 리턴. point 객체에 x,y 정보 있음 

public void mousePressed(MouseEvent e) {
	int x = e.getX();
	int y = e.getY();
}
</pre></code>

마우스 클릿 횟수

더블클릭을 인식할 때 이용되는 것으로 클릭 횟수를 리턴하는 메소드는 다음과 같다.

int getClickCount() // 마우스의 클릭 횟수 리턴

<pre><code>
public void mouseClicked(MouseEvent e) {
	if(e.getClickCount() == 2) {
		// 더블클릭을 처리하는 코드
	}
}
</pre></code>

마우스 버튼 

눌러진 마우스 버튼을 리턴하는 메소드는 다음과 같다.

int getButton() // 눌러진 마우스 버튼의 번호를 리턴한다.
리턴값은 NOBUTTON,BUTTON1,BUTTON2,BUTTON3 중의 하나이며 마우스 왼쪽 버튼은 BUTTON1이고 오른쪽 버튼은 BUTTON3이다.

<pre><code>
public void mousePressed(MouseEvent e) {
	if(e.getButton() == MouseEvent.BUTTON1)
		System.out.println("Left Button Pressed");
}
</pre></code>

MouseWheelEvent와 MouseWheelListener

마우스 휠을 굴리면 MouseWheelEvent가 발생하며, MouseWheelListener 인터페이스가 가진 유일한 다음 메소드가 호출된다.

public void mouserWheelMoved(MouseWheelEvent e)

<pre><code>
component.addMouseWheelListener(new MouseWheelListener() {
	public void mouseWheelMoved(MouseWheelEvent e) {
		// 마우스 휠의 구르는 방향에 따라 이벤트를 처리한다.
	}
});
</pre></code>


- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
