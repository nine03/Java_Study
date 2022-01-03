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
- JLabel에 출력된 이미지나 텍스트를 스크롤 가능하게 만드는 

- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
