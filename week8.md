GUI

GUI란 Graphicl User Interface의 약자로서 이미지 혹은 그래픽을 이용하여 메뉴 등을 포함하는 화면을 구성하고, 키보드 외 마우스 등의 편리한 입력 도구를 이용하여 사용자가 입력하기 편하도록 만들어진 사용자 인터페이스이다.

GUI 컴포넌트 (GUI Component)

자바의 GUI 컴포넌트는 AWT 컴포넌트와 Swing 컴포넌트로 구분되며, 이들을 각각 java.awt 패키지와 javax.swing 패키지를 통해 공급된다.

AWT

AWT(Abstract Windowing Toolkit)는 자바가 처음 나왔을 때 함께 배포된 패키지로서 많은 GUI 컴포넌트를 포함한다. Frame, Window, Panel, Dialog, Button, Label, TextField, Checkbox, Choice 등 AWT의 컴포넌트들은 중량 컴포넌트(heavy weight component)로 불리는데, 이 컴포넌트들은 운영체제(native OS)의 도움을 받아 화면에 출력되기 때문에 운영체제의 자원을 많이 소모하여 운영체제에 많은 부담을 준다.

스윙(Swing) 

스윙(Swing)은 AWT와 달리 순수 자바 언어로 작성되었다. 운영체제의 도움을 받지 않기 때문에 스윙 컴포넌트들은 경량 컴포넌트(light weight component)라고 불린다. 그러므로 스윙 컴포넌트들은 운영체제와 관계없이 항상 동일하게 작동하며 동일한 모양으로 그려진다. 모든 AWT 컴포넌트들이 100% 호환되도록 스윙 컴포넌트로 다시 작성되었으며, 스윙 컴포넌트의 이름은 AWT 컴포넌트와 구분하기 위해 모두 대문자 J로 시작한다.

스윙 기반의 GUI 응용프로그램 샘플

- 응용프로그램의 전체 컴포넌트를 담는 JFrame
- 모든 메뉴를 담는 JMenuBar
- 메뉴로 작동하는 JMenu
- 툴바로 작동하는 JToolBar
- 버튼으로 작동하는 JButton. 툴바에 부착된다.
- 문자열을 출력하는 JLabel. 툴바에 부착된다.
- 이미지 버튼으로 작동하는 JButton. 툴바에 부착된다.
- 한 줄 문자열을 입력 받는 찾 JTextFiled. 툴바에 부착된다.
- 푸시다운 버튼으로 작동하는 JComboBox. 툴바에 부착된다.
- 두 개의 분리된 팬으로 작동하는 JSplitPane의 왼쪽에 부착된다.
- 리스트를 출력하는 JList, JSplitPane의 왼쪽에 부착된다.
- 이미지를 출력하는 JLabel. JSplitPane의 오른쪽에 부착된다.
- JLabel에 출력된 이미지나 텍스트를 스크롤 가능하게 만드는 JScrollPane

GUI 패키지 계층 구조 

![image](https://user-images.githubusercontent.com/60682087/147947388-1adb3327-1852-4c02-80b9-97365edb2c80.png)
그림1 AWT와 스윙 클래스의 상속 관계

GUI 응용프로그램을 사용하기 위해 필요한 주요 클래스들의 상속 관계를 그림1에 나타냈었다. 모든 GUI 컴포넌트들은 Component 클래스를 반드시 상속받으며, 스윙 컴포넌트의 클래스 명은 모두 J로 시작한다. AWT 컴포넌트는 Button, Label 등과 같이 Component를 직접 상속받는 것들과 Panel, Frame 등과 같이 Container를 상속받는 것들이 있다. 그리고 JApplet, JFrame, JDialong를 제외한 모든 스윙 컴포넌트들은 JComponent를 상속받는다. Font, Dimension, Color, Graphics 등은 컴포넌트가 아니지만, 문자의 폰트 설정, 색, 도형 그리기 등 그래픽 작업시 반드시 필요하다.

컨테이너와 컴포넌트

자바의 GUI 응용프로그램은 GUI 컴포넌트들로 구성되며, GUI 컴포넌트들은 다른 컴포넌트를 포함할 수 있는지 여부에 따라 순수 컴포넌트와 컨데이너로 분류된다. 빈 판위에 레고 블록을 쌓아 가듯이, GUI 컴포넌트들을 쌓아 GUI 응용프로그램을 구성한다.

컨테이너

컨테이너란 다른 GUI 컴포넌트를 포함할 수 있는 컴포넌트이다. 그러므로 컨테이너는 컴포넌트이면서 동시에 컨테이너이다. 컨테이너가 되기 위해서는 java.awt.Container 클래스를 상속받아야만 한다. Container 클래스는 java.awt.Component를 상속받기 때문에 컨테이너가 컴포넌트이기도 한 것이다. 컨테이너는 다른 컨테이너에 컴포넌트로 포함될 수도 있다.

<pre><code>
Frame, Panel, Applet, Dialog, Window // AWT 컨테이너
JFrame, JPanel, JApplet, JDialog, Jwindow // 스윙 컨테이너
</pre></code>

컴포넌트

컴포넌트란 컨테이너와 달리 다른 컴포넌트를 포함할 수 없으며, 컨테이너에 포함되어야 비로소 화면에 출력될 수 있는 GUI 객체이다. AWT나 스윙의 모든 컴포넌트들은 java.awt.Component를 상속받기 때문에, Component 클래스에는 모든 컴포넌트들의 공동적인 속성과 기능이 작성되어 있다. 컴포넌트의 크기, 모양, 위치, 색, 폰트 등에 관한 정보를 관리하는 멤버 변수와 메소드, 컴포넌트 그리기, 이동, 삭제, 이벤트 처리에 관한 메소드 등 다양한 기능을 제공한다. 또한 순수 스윙 컴포넌트들은 모두 javax.swing.Jcomponent를 상속받으며, JComponent에는 스윙 컴포넌트들의 공통적인 기능이 작성되어 있다.

최상위 컨테이너

컨테이너 중에서 다른 컨테이너에 속하지 않고도 독립적으로 화면에 출력될 수 있는 컨테이너를 최상위 컨테이너(Top Level Container)라고 한다. JFrame, JDialog, JApplet의 3가지가 이에 속한다. 그러나 이들을 제외한 나머지 컨테이너나 컴포넌트들은 다른 컨테이너에 부착되어야 하고, 종국에는 최상위 컨테이너에 부착되어야만 화면에 출력된다.

컨테이너와 컴포넌트의 포함 관계

최상위 컨테이너와 컨테이너, 컴포넌트의 포함 관계를 보여준다. 그림의 오른쪽은 스윙으로 작성된 GUI 응용프로그램의 실제 모습을, 왼쪽은 응용프로그램을 구성하는 스윙 컴포넌트들의 관계를 보여준다. 맨 바깥에 최상위 컨테이너인 JFrame컨테이너가 있고, 그 안에 JPanel 컨테이너가 하나 부착되어 있다. 그리고 이 컨테이너에 다시 두 개의 JPanel 컨테이너와 1개의 버튼 컴포넌트가 부착되어 있다. 두 JPanel 컨테이너에는 다시 여러 개의 스윙 컴포넌트들이 부착되어 있다.

자바 스윙 응용프로그램은 이렇게 JFrame과 같은 최상위 컨테이너 위에 컨테이너와 컴포넌트들이 마치 레고 블록을 쌓는 것처럼 컨테이너와 컴포넌트의 계층 구조로 구성되어, 컨테이너에 부착된 컴포넌트들을 자식 컴포넌트라고 부른다.

스윙 GUI 프로그램 만들기 

- 스윙 프레임 작성
- main() 메소드 작성
- 프레임에 스윙 컴포넌트 붙이기

스윙 패키지 사용을 위한 import문

스윙 패키지를 이용하기 위해서는 스윙 컴포넌트의 클래스 파일들이 존재하는 경로명 javax.swing.* 를 import 해야한다.

<pre><code>
import javax.swing.*;
</pre></code>

대부분의 스윙 응용프로그램은 이벤트 처리, 이미지나 도형을 그리는 부분을 필수적으로 동반하므로, 다음과 같은 import문이 필요한 경우가 많다.

<pre><code>
import java.awt.*; // 폰트 등 그래픽 처리를 위한 클래스들의 경로명
import java.awt.event.*; //이벤트 처리에 필요한 기본 클래스들의 경로명
import javax.swing.*; // 스윙 컴포넌트 클래스들의 경로명
import javax.swing.event.*; // 스윙 이벤트 처리에 필요한 클래스들의 경로명
</pre></code>

스윙 프레임과 컨텐트팬

스윙 프레임은 모든 스윙 컴포넌트들을 담는 최상위 컨테이너(Top Level Container)이다. 스윙 프레임이 출력될 때, 스윙 프레임이 내에 부착된 모든 컴포넌트들이 화면에 출력된다. 컴포넌트들은 스웡 프레임 내의 모든 컴포넌트들도 프레임과 함께 화면에서 사라진다. 스윙에서 프레임의 역할을 수행하는 클래스가 JFrame 객체는 Frame(java.awt.Frame), 메뉴바(Menu Bar), 컨텐트팬(Content Pane)의 3공간으로 구성된다.Frame은 AWT패키지에 있는 클래스로서 JFrame이 같이 상속받기 때문에 당연히 그 속성들이 존재하며, 메뉴바는 메뉴들을 부착하는 공간이고, 컨텐트팬은 메뉴를 모든 GUI컴포넌트들을 부착하는 공간이다. 

프레임 만들기, JFrame 클래스 상속 

<pre><code>
public class MyFrame extends JFrame {
.................................
}
</pre></code>

스윙 프레임 생성 

<pre><code>
MyFrame frame = new MyFrame(); // 스윙 프레임 생성 
</pre></code>

<pre><code>
setTitle("300x300 스윙 프레임 만들기"); // 프레임 타이틀 설정 
setSize(300,300); // 폭 300, 높이 300 크기로 프레임 크기 설정
setVisible(true); // 프레임이 출력되도록 지시. false의 경우 프레임이 숨겨짐  
</pre></code>

스윙 응용프로그램에서 main() 메소드의 기능과 위치 

스윙 응요프로그램에서 main()의 기능은 최소화하는 것이 좋다. main()에는 스윙 응용프로그램이 실행되는 시작점으로서 프레임을 생성하는 코드 정도만 만들고, 나머지 기능은 프레임 클래스에 작성하는 것이 좋다.

프레임에 컴포넌트 붙이기

프레임은 응용프로그램을 구성하는 바탕 틀이다.

타이틀 달기

프레임에 타이틀을 달기 위해서는 다음과 같이 super()를 이용하여 JFrame의 생성자를 호출하거나, JFrame 클래스의 setTitle() 메소드를 이용 할 수 있다.

<pre><code>
public MyFrane() { // 생성자
  super("타이틀문자열"); // JFrame("타이틀문자열") 생성자를 호출하여 타이틀 달기
  setTitle("타이틀문자열"); // 메소드를 호출하여 타이틀 달기 
}
</pre></code>

메뉴 붙이기

메뉴를 작성하기 위해서는 메뉴바를 만들고, 메뉴를 붙이고, 메뉴에는 여러개의 메뉴 아이템을 붙인다. 메뉴바를 JFrame의 메뉴바 영역에 붙이면 화면에 메뉴가 출력된다.

컨텐트팬에 컴포넌트 달기 

스윙에서는 컨텐트팬(Content pane)에만 컴포넌트를 부착할 수 있다. JFrame 객체가 생길 때 컨텐트팬이 자동으로 생성한다. 그러므로 현재 프레임에 붙어 있는 컨텐트팬을 알아내기 위해서는, 다음과 같이 JFrame 클래스의 getContentPane() 메소드를 호출한다.

<pre><code>
public class MyFrame extends JFrame {
        public MyFrame() {
          ...
          Container contentPane = getContentPane(); // 프레임에 부착된 컨텐트팬을 알아낸다.
        }
        ...
}
</pre></code>

컨텐트팬에 컴포넌트를 붙이는 것은 비교적 간단하다. 컨텐트팬은 컨테이너이기때문에 다음과 같이 add() 메소드를 이용하여 간단히 컴포넌트를 부착하면 된다.

<pre><code>
JButton button = new JButton("Click"); // 버튼 컴포넌트 생성
contentPane.add(button); // 컨텐트팬에 버튼 부착
</pre></code>

컨텐트팬의 변경 

JFrame 클래스의 setContenetPane() 메소드를 이용하면 프레임에 부착된 컨텐트팬을 제거하고 새로운 컨텐트팬을 붙일 수 있다. 컨텐트팬은 Container 타입이므로 Container를 상속받은 어떤 컨테이너도 컨텐트팬이 될 수 있다.

<pre><code>
class MyPanel extends JPanel {
    // JPanel을 상속받은 패널을 작성한다.
}

frame.setContentPane(new MyPanel()); // 프레임의 컨텐트팬을 MyPanel 객체로 변경 
</pre></code>

스윙 응용프로그램의 종료 

자바에서 프로그램을 종료하려면 어떤 상황에서나 다음 코드를 사용하면 된다.

<pre><code>
System.exit(0); // 자바프로그램을 종료한다.
</pre></code>

프레임 원도우가 닫힐 때 스웡 프로그램도 함께 종료시키고자 한다면 다음 코드를 삽입하여야 한다.

<pre><code>
frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
// 프레임이 닫힐 때 프로그램도 함께 종료한다.
</pre></code>

컨테이너와 배치

컨테이너에 부착되는 컴포넌트들의 위치와 크기는 컨테이너 내부에 있는 배치관리자(Layout Manager)에 의해 결정된다. 

- 컨테이너마다 배치관리자가 하나씩 있다.
- 배치관리자는 컨테이너에 컴포넌트가 부착되는 시점에 컴포넌트의 위치와 크기를 결정한다.
- 컨테이너의 크기가 변경되면 배치관리자는 컨테이너 내부의 모든 컴포턴트들의 위치와 크기를 재조정한다. 

배치관리자의 종류

FlowLayout

컨테이너에 부착되는 순서대로 왼쪽에서 오른쪽으로 컴포넌트를 배치하며, 오른쪽에 더이상 배치할 공간이 없으면 아래로 내려와서 다시 왼쪽에서 오른쪽으로 배치한다. 컴포넌트의 크기는 화면에 출력될 수 있는 적당한 크기로 설정한다.

BorderLayout

컨테이너의 공간을 동(EAST), 서(WEST), 남(SOUTH), 북(NORTH), 중앙(CENTER)의 5개의 영역으로 나누고 응용프로그램에서 지정한 영역에 컴포넌트를 배치한다. 응용프로그램에서는 5개의 영역 중 하나를 반드시 지정하여야 한다. 영역을 지정하지 않으면 중앙에 배치된다. 컴포넌트의 크기는 영역의 크기에 맞추어 설정된다.

GridLayout

컨테이너의 공간을 응용프로그램에서 설정한 동일한 크기의 2차원 격자로 나누고, 컴포넌트가 삽입되는 순서대로 좌에서 우로, 다시 위에서 아래로 배치한다. 컴포넌트의 크기는 셀의 크기와 동일하게 설정한다.

CardLayout

컨테이너의 공간에 카드를 쌓아 놓은 듯이 컴포넌트를 포개어 배치한다. 컴포넌트의 크기는 컨테이너의 크기와 동일하게 설정한다.

컨테이너의 디폴트 배치관리자

<pre><code>
AWT와 스윙 컨테이너   디폴트 배치관리
Window, JWindow    :  BorderLayout
Frame, JFrame      :  BorderLayout
Dialog, JDialog    :  BorderLayout
Panel, JPanel      :  FlowLayout
Applet, JApplet    :  FlowLayout
</pre></code>

컨테이너에 새로운 배치관리자 설정, setLayout() 메소드

컨테이너에는 새로운 배치관리자를 마음대로 설정할 수 있다. 이를 위해 다음과 같이 Container 클래스의 setLayout() 메소드를 호출한다.

<pre><code>
Container.setLayout(LayoutManager lm); // lm을 새로운 배치관리자로 설정한다.
</pre></code>

JPanel에 BorderLayout 배치관리자를 설정하려면 다음과 같다.

<pre><code>
JPanel p = new JPanel();
p.setLayout(new BorderLayout()); // 패널에 BorderLayout 배치관리자 설정
</pre></code>

컨텐트팬의 배치관리자를 FlowLayout으로 변경하려면 다음과 같이 한다.

<pre><code>
Container contentPane = frame.getContentPane(); // 프레임의 컨텐트팬
contentpane.setLayout(new FlowLayout()); // FlowLayout 배치관리자 설정
</pre></code>

배치 관리자 객체 생성하는 new를 빠트리지 않도록한다.

<pre><code>
contentPane.setLayout(FlowLayout); // 오류 
</pre></code>

FlowLayout 배치관리자

배치방법

FlowLayout 배치관리자를 가진 컨테이너에 컴포넌트를 부착하는 방법은 다음과 같이 간단히 add() 메소드를 이용하면 된다.

<pre><code>
container.setLayout(new FlowLayout());
container.add(new JButton("add"));
container.add(new JButton("sub"));
container.add(new JButton("mul"));
container.add(new JButton("div"));
container.add(new JButton("Calculate"));
</pre></code>

FlowLayout 배치관리자는 컴포넌트를 왼쪽에서 오른쪽으로 배치하고, 더 이상 오른쪽 공간이 없으면 다시 아래로 내려와서 왼쪽에서 오른쪽으로 배치한다.

FlowLayout의 생성자와 속성 

FlowLayout 배치관리자의 생성자는 다음과 같이 여러 개 있으며, 생성자에 컴포넌트 사이의 간격과 정렬 방식을 지정할 수 있으며 FlowLayout 배치관리자의 align, hGap, vGap 가 있다.

<pre><code>
FlowLayout()
FlowLayout(int align)
FlowLayout(int align, int hGap, int vGap)
align : 컴포넌트의 정렬 방법. 왼쪽 정렬(FlowLayout.LEFT), 오른쪽 정렬(FlowLayout.RIGHT), 중앙 정렬(FlowLayout.CENTER(디폴트))
hGap : 좌우 컴포넌트 사이의 수평 간격, 픽셀 단위. 디폴트는 5
vGap : 상하 컴포넌트 사이의 수직 간격, 픽셀 단위. 디폴트는 5
</pre></code>

FlowLayout의 생성자 예제

<pre><code>
new FlowLayout(); // 중앙 정렬과 hGap = 5, vGap = 5인 배치관리자
new FlowLayout(FlowLayout.LEFT); // 왼쪽 정렬과 hGap = 5, vGap = 5인 배치관리자
new FlowLayout(FlowLayout.CENTER,10,20); // 왼쪽 정렬과 hGap = 10, vGap = 20인 배치관리자
</pre></code>

BorderLayout 배치관리자

배치방법

BorderLayout 배치관리자는 컨테이너 공간을 동(EAST), 서(WEST), 남(SOUTH), 북(NORTH), 중앙(CENTER)의 5개의 영역으로 분할하여 배치한다.

다른 배치관지라와는 달리 BorderLayout 배치관리자를 가진 컨테이너에 컴포넌트를 삽입하기 위해서는 add() 메소드에 컴포넌트의 위치를 명확히 정해주어야 한다.

<pre><code>
void add(Component comp, int index) // comp 컴포넌트를 index 위치에 삽입한다.
comp : 컨테이너에 삽입되는 컴포넌트
index : 컴포넌트의 위치 
동 : BorderLayout.EAST
서 : BorderLayout.WEST
남 : BorderLayout.SOUTH
북 : BorderLayout.NORTH
중앙 : BorderLayout.CENTER
</pre></code>

add() 메소드를 사용하는 방법

<pre><code>
container.setLayout(new BorderLayout());
container.add(new JButton("div"),BorderLayout.WEST);
container.add(new JButton("Calculate"),BorderLayout.CENTER;
</pre></code>

BorderLayout의 생성자와 속성 

BorderLayout 배치관리자의 생성자는 다음과 같으며, 생성자를 이용하면 컴포넌트 사이의 간격으로 조절할 수 있다.

<pre><code>
BorderLayout()
BorderLayout(int hGap, int vGap)
hGap : 좌우 두 컴포넌트 사이의 수평 간격, 필셀 단위. 디폴트는0
vGap : 상하 두 컴포넌트 사이의 수직 간격, 픽셀 단위. 디폴트는0
</pre></code>

BorderLayout의 생성자를 사용하는방법

<pre><code>
new BorderLayout(); // hGap = 0, vGap = 0인 BorderLayout 배치관리자 생성
new BorderLayout(30,20); // hGap = 30, vGap = 20인 BorderLayout 배치관리자 생성
</pre></code>

GridLayout 배치관리자

GridLayout은 컨테이너 공간을 그리드(격자) 모양으로 분할하여 각 셀에 하나씩 컴포넌트를 배치하는 방법이다. GridLayout은 부착되는 순서대로 컴포넌트를 셀에 배치한다. 

컴포넌트를 삽입하는 방법

<pre><code>
container.setLayout(new FridLayout(4,3)); // 4 x 3 분할로 컴포넌트 배치
container.add(new JButton("1")); // 상당 왼쪽 첫 번째 셀에 버튼 배치
container.add(new JButton("2")); // 그 옆 셀에 버튼 배치
</pre></code>

GridLayout의 생성자와 속성

<pre><code>
GridLayout()
GridLayout(int rows, int cols)
GridLayout(int rows, int cols, int hGap, int vGap)
rows : 그리드의 행 수, 디폴트는 1
cols : 그리드의 열 수, 디폴트는 1
hGap : 좌우 컴포넌트 사이의 수평 간격, 픽셀 단위. 디폴트는 0
vGap : 상하 컴포넌트 사이의 수직 간격, 픽셀 단위. 디폴트는 0
</pre></code>

GridLayout의 생성자를 사용한 예제

<pre><code>
new GridLayout(); // 그리드에 배치하는 GridLayout 배치관리자 생성
new GridLayout(4,3,5,5); // 4 x 3 그리드에 hGap = 5, vGap = 5의 간격으로 컴포넌트를 배치하는 GridLayout 배치관리자 생성
</pre></code>

배치관리자없는 컨테이너가 필요한 경우
- 컴포넌트의 크기나 위치를 개발자가 결정하고자 하는 경우
- 게임 프로그램과 같이 시간이나 마우스/키보드의 입력에 따라 컴포넌트들의 위치와 크기가 수시로 변하는 경우
- 여러 컴포넌트들이 겹치는 효과를 연출하고자 하는 경우

이런경우, 컴테이너의 배치관리자를 없애고 응용프로그램에서 직접 컴포넌트의 위치와 크기를 마음대로 설정할 수 있어야 한다.

컨테이너의 배치관리자 제거

Container의 setLayout() 메소드를 이용하여 컨테이너의 배치관리자를 제거할 수 있다.

<pre><code>
container.setLayout(null); // container의 배치관리자 제거
</pre></code>

JPanel에 현재 부착된 배치관리자를 삭제한다.

<pre><code>
JPanel p = new JPanel();
p.setLayout(null);
</pre></code>

예제

<pre><code>
JPanel p = new JPanel();
p.setLayout(null);

// 배치관리자가 없으므로 아래 2개의 버튼은 배치되지 않는다.
p.add(new JButton("click")); // 폭과 높이가 0인 상태로 화면에 보이지 않는다.
p.add(new JButton("me!")); // 폭과 높이가 0인 상태로 화면에 보이지 않는다.
</pre></code>

컴포넌트의 절대 위치와 절대 크기 설정 

배치관리자가 없는 컨테이너에 컴포넌트를 삽입할 때는 응용프로그램에서 컴포넌트의 크기와 위치를 직접 설정하여야 한다. 컴포넌트의 절대 위치와 크기를 설정하기 위해서는 java.awt.Component 클래스의 다음 메소드를 이용한다.

<pre><code>
void setSize(int width, int height) 컴포넌트를 width x height 크기로 설정 
void setLocation(int x, int y) 컴포넌트를 왼쪽 상단 모서리 좌표를 (x,y)로 설정
void setBounds(int x,int y,int width, int height) 크기와 위치 동시 설정
</pre></code>

예제

<pre><code>
Panel p = new JPanel();
p.setLayout(null); // 패널 p의 배치관리자 제거
JButton clickButton = new JButton("Click");
clickButton.setSzie(100,40); // 버튼의 크기를 100 x 40으로 지정
clickButton.setLocation(50,50); // 버튼의 위치를 (50,50)으로 지정
p.add(clickButton); // 패널에 버튼 부착. 패널 내 (50,50) 위치에 100 x 40 크기의 버튼 출력
</pre></code>

CardLayout을 제외한 나머지 배치관리자는 컴포넌트들이 서로 겹치지 않도록 배치한다. 그러나 배치관리자가 없는 컨테이너를 만드면 컴포넌트를 절대 위치에 절대 크기로 배치할 수 있기 때문에 컴포넌트들이 서로 켭치도록 배치할 수 있다.


- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
