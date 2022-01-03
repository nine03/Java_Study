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

- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
