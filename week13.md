메뉴

메뉴 구성

JMenuBar

메뉴바의 기능을 구현한 클래스이다. 이곳에 JMenu로 만든 메뉴를 여러 개 단다.

JMenu

하나의 메뉴를 구현한 클래스이다. 이곳에 JMenuItem으로 만든 메뉴아이템을 여러 개 단다.

JMenuItem

하나의 메뉴아이템을 구현한 클래스이다.

분리선

메뉴아이템 사이의 분리선으로서 separator라고 부르며, JMenu의 addSeparator() 메소드를 호출하면 메뉴에 분리선이 삽입된다. 

메뉴 만들기 

1. 메뉴바 만들기

```
JMenuBar mb = new JMenuBar();
```

2. 메뉴를 만들고 메뉴바에 붙이기 

메뉴 이름은 문자열로 JMenu의 생성자에 전달한다. 메뉴바에 메뉴를 붙일 때 JMenuBar의 add() 메소드를 이용한다. "Screen" 메뉴를 만들어 메뉴바에 붙이는 코드는 다음과 같다.

```
JMnu screenMenu = new JMenu("Screen"); // Screen 메뉴 생성 
mb.add(screenMenu); // 메뉴바에 Screen 메뉴 붙이기 
```

3. 메뉴 아이템을 생성하여 메뉴에 붙이기 

메뉴아이템의 이름은 문자열로서 JMenuItem의 생성자에 전달한다. 메뉴아이템을 메뉴에 붙일 때는 JMenu의 add() 메소드를 이용한다. screenMenu에 메뉴아이템과 분리선을 붙이는 코드는 다음과 같다.

```
screenMenu.add(new JMenuItem("Load"));
screenMenu.add(new JMenuItem("Hide"));
screenMenu.add(new JMenuItem("ReShow"));
screenMenu.addSeparator(); // ReShow 메뉴아이템 다음에 분리선 삽입
screenMenu.add(new JMenuItem("Exit"));
```

4. 메뉴바를 프레임에 붙이기

JFrame의 setJMenuBar() 메소드를 이용하여 메뉴바를 붙이는 예는 다음과 같다.

```
frame.setJMenuBar(mb);
```

메뉴아이템에 Action 이벤트 달기 

많은 경우 메뉴아이템은 사용자로부터 작업 명령을 받는 데 사용된다. 사용자가 메뉴 아이템을 선택하면 Action 이벤트가 발생한다. 다음은 메뉴아이템에 Action 이벤트를 처리하기 위해 Action 리스너를 등록하는 코드 예이다.

```
JMenuItem item = new JMenuItem("Load");
item.addACtionListener(new MenuActionListener()); // 메뉴아이템에 Action 리스너 등록 
screenMenu.add(item);
...
class MenuActionListener implements ActionListener {
    public void actionPerformed(ActionEvent e) {
      // 사용자가 Load 메뉴아이템을 선택하는 경우 처리할 직업 구현 
    }
}
```

툴바

JToolBar 

JToolBar는 툴바를 구현한 컴포넌트이다. 툴바는 모양의 컨테이너로, 다양한 스윙 컴포넌트를 담아 아이콘 형태의 메뉴를 제공하기 위해 사용된다. 툴바틑 BorderLayout 배치관리자를 가진 컨테이너에만 부착되며, 동(EAST), 서(WEST), 남(SOUTH), 북(NORTH)의 아무 곳이나 부착 가능하다. 

툴바 만들기 

1.JToolBar 객체 생성

JToolBar의 생성자에 툴바 이름을 전달하여 툴바를 만든다. 아래는 툴바 이름이 "Kitae Menu"인 툴바를 생성하는 코드이다. 

```
JToolBar toolBar = new JToolBar("Kitae Menu");
```

2. 메뉴로 사용할 컴포넌트를 툴바에 삽입

모든 스윙 컴포넌트가 JToolBar에 삽입 가능하며, 컴포넌트 사이에 분리 공간(separator)을 삽입할 수 있다.

```
toolBar.add(new JButton("New")); // 버튼 삽입
toolBar.addSeparator(); // 분리 공간 삽입
toolBar.add(new JTextField("text field")); // 텍스트필드 삽입
```

3. 툴바를 컨테이너에 삽입

툴바는 BorderLayout 배치관리자가 설정된 컨테이너에만 부착된다. 다음은 컨테이너 container의 NORTH 영역에 툴바를 부착하는 사례이다.

```
container.add(toolBar, BorderLayout.NORTH); // 컨테이너의 NORTH에 툴바 부착
```

툴바 이동 제어 

툴바는 기본적으로 사용자가 핸들을 드래깅하여 다른 영역으로 이동할 수 있지만, 다음과 같이 JToolBar.setFloatable(false)를 호출 하면 툴바의 핸들이 보이지 않게 되며 사용자는 툴바를 다른 곳으로 이동할 수 없다.

```
toolBar.setFloatable(false); // 툴바 이동 불가능. true이면 이동 가능 
```

툴팁 생성 및 달기

스윙 컴포넌트에 마우스를 올리면 잠깐 나타났다가 사라지는 문자열을 툴팁(tooltip)이라고 부른다. 

모든 스윙 컴포넌트들이 툴팁을 가질 수 있으며 생성 방법 또한 단순하다. 간단히 JComponent의 setToolTipText(String msg) 메소드를 호출하면, 문자열(msg)을 컴포넌트의 툴팁으로 등록한다.

```
JButton b = new JButton("New");
b.setToolTipText("파일을 생성합니다."); // 버튼에 툴팁등록 
```

ToolTipManager와 툴팁 시간 제어 

툴팁은 마우스를 올리면 나타났다가 일정 시간 후에 사라진다. ToolTipManager 클래스를 이용하여 툴팁과 관련된 시간을 제어할 수 있다. 툴팁에 관한 시간 제어는 모든 툴팁에 일괄적으로 적용되며 각 툴팁마다 관련 시간을 따로 지정할 수 없다.

ToolTipManager 객체 얻기

툴팁 시간을 지정하려면, 우선 다음과 같이 ToolTipManager 객체를 얻어야 한다.
ToolTipManager m = ToolTipManager.sharedInstance(); // toolTipManager 객체 리턴 

툴팁 활성화

ToolTipManager의 setEnabled(boolean b) 메소드를 이용하면, 툴팁이 나타나도록 할지 나타나지 않도록 할지 제어할 수 있다. 이러한 툴팁의 활설화/ 비활성화는 응용프로그램에 속한 모든 툴팁에 일괄적으로 적용되며 컴포넌트별 별로 제어할 수 없다. 

```
m.setEnabled(false); // 툴팁이 나타나지 않도록 설정
```

위의 문장에서 인자를 true를 주면 모든 툴팁이 활성화된다. 

초기 툴팁 출력 시간 제어 

ToolTipManager의 setInitialDelay(int millis) 메소드를 호출하면, 마우스가 컴포넌트 위에 올라간 후, 툴팁이 출력되는 데까지 걸리는 시간을 정할 수 있다. 인자는 밀리초 단위의 시간이다. 이 시간 역시 모든 컴포넌트에 일괄적으로 적용된다.

```
m.setInitialDelay(1000); // 마우스가 올라온 지 1000ms 후 툴팁이 출력되도록 설정 
```

툴팁 지속 시간 제어 

ToolTipManager의 setDismissDelay(int millis) 메소드를 호출하면, 출력된 툴팁이 지속되는 시간을 정할 수 있다. 인자는 밀리초 단위의 시간이다.

```
m.setDismissDelay(1000); // 툴팁이 출력되어 있는 지속시간을 1000ms로 설정 
```

JDialog

다이얼로그란 보여주고자 하는 내용을 스크린에 출력하고, 사용자로부터 입력을 받는 대화 상자이다. 개발자는 JDialog를 상속 받아 자신만의 다이얼로그를 만들 수 있다. JDialog는 JFame처럼 다른 컨테이너에 속할 필요 없이 화면에 출력 가능한 최상위 컨테이너(Top Level Container)이다.

```
JDialog dialog = new JDialog(); // 다이얼로그 생성
dialog.setTitle("나의 다이얼로그"); // 타이틀 달기
dialog.add(new JButton("click!")); // 다이얼로그에 버튼 삽입
dialog.setSize(300,300); // 다이얼로그 크기 설정
dialog.setVisible(true); // 다이얼로그 화면에 출력
```

JDialog

```
JDialog()                                          다이얼로그를 생성하는 생성자이다. owner는 다이얼로그의 주인,
JDialog(Frame owner)                               title은 타이틀, model은 다이얼로그의 종류를 뜻한다. modal 값이
JDialog(Frame owner, String title)                 true이면 모달 다이얼로그를, false이면 모달리스 다이얼 로그를 
JDialog(Frame owner, String title, boolean model)  생성한다. 디폴트는 모달리스 타입이다. 

void setVisivle(boolean b)   b가 true이면 다이얼로그를 화면에 출력하고 false이면 숨긴다.
void setTitle(String title)  title 문자열을 다이얼로그 타이틀로 설정한다.
```

다이얼로그 만들기 

JDialog를 상속받는 다이얼로그 클래스 작성 

```
class MyDialog extends JDialog {
}
```

다이얼로그 생성자 작성

JDialog 클래스의 생성자는 여러가지가 있으며, 다음과 같이 MyDialog의 생성자를 작성한다.

```
class MyDialog extends JDialog {
  public MyDialog(JFrame frame, String title) {
    super(frame, title); // frame은 다이얼로그의 주인이며 title은 다이얼로그의 타이틀이다.
  }
}
```

모달 다이어로그와 모달리스 다이얼로그 

다이얼로그의 타입은 모달(modal)과 모달리스(modeless)의 두 가지가 있다. 모달 타입은 다이얼로그가 일단 출력되면 당이얼로그를 닫기전에는 다른 작업을 전혀 할 수 없도록 사용자 입력을 독점하는 타입이며, 모달리스 타입은 다른 창과 모달리스 다이얼로그가 각자 독립적으로 작동하는 타입이다. 그러므로 모달리스 다이얼로그를 열어 놓은 채 다른 찾에서 입력 작업이 가능하다.

```
JDialog(Frame owner, String title, boolean modal)
```

```
super(frame, title, true); // true는 다이얼로그를 모달 타입으로 지정 
```

다이얼로그로부터 사용자 입력 값 전달받기

사용자가 입력한 내용을 다이얼로그로부터 읽어 오기 위해 다음 코드를 이용하였다.

```
String text = dialog.getInput();
```

text의 값이 null이면 사용자가 아무 값도 입력하지 않는 것이므로 단순히 리턴하도록 다음 코드를 사입하였다.

```
if(text == null) return;
```

다음 코드는 text값으로 JButton 컴포넌트의 문자열을 변경한다.

```
btn.setText(text);
```

팝업 다이얼로그와 JOptionPane

지금까지 JDialog를 상속받아 다이얼로그를 만드는 방법을 알아봤다. 파업 다이얼로그는 스윙 패키지에 구현된 간단한 팝업 창으로 사용자에게 메시지를 전달하거나 간단한 문자열을 입력받는 유요한 다이얼로그이다. JOptionPane 클래스는 여러 종류의 팝업 다이얼로그를 출력하는 static 메소드를 지원한다.

입력 다이얼로그, JOptionPane.showInputDialog() 

JOptionPane의 showInputDialog() 메소드를 호출하면 한 줄의 문자열을 입력받는 입력 다이얼로그를 출력할 수 있다.

```
static String JOptionPane.showInputDialog(String msg)
msg : 다이얼로그 메시지
리턴값 : 사용자가 입력한 문자열. 취소 버튼이 선택되거나 창이 닫히면 null 리턴 
```

확인 다이얼로그 JOptionPane.showConfirmDialog()

사용자로 부터 확인/취소를 입력받기 위한 팝업 다이얼로그를 출력하는 showConfirmDialog() 메소드는 다음과 같다.

```
static int JOptionPane.showConfirmDialog(Component parentComponent, Object msg, String title, int optionType)
parentComponent : 다이얼로그의 부모 컴포넌트로서 다이얼로그가 출력되는 영역의 범위 지정을 위해 사용(예 : 프레임). 
                  null이면 전체 화면 중앙에 출력
msg: 다이얼로그 메시지
title : 다이얼로그 타이틀
optionType : 다이얼로그 옵션 종류 지정
YES_NO_OPTION,YES_NO_CANCEL_OPTION,OK_CANCEL_OPTION
리턴 값 : 사용자가 선택한 옵션 종류 
YES_OPTION, NO_OPTION, CANCEL_OPTION, OK_OPTION, CLOSED_OPTION                  
```

메시지 다이얼로그 JOptionPane.showMessageDialog() 

showMessageDialog() 메소드를 이용하면, 사용자에게 문자열 메시지를 출력하기 위한 메시지 다이얼로그 출력한다. 이 메소드는 다음과 같다.

```
static void JOptionPane.showMessageDialog(Component parentComponent, Object msg, String title, int message Type)
parentComponent : 다이얼로그의 부모 컴포넌트로서 다이얼로그가 출력되는 영역의 범위 지정을 위해 사용(예 : 프레임). null이면 전체 화면 중앙에 출력
msg : 다이얼로그 메시지
title : 다이얼로그 타이틀
messageType : 다이얼로그의 종류로서 다음 중 하나 
ERROR_MESSAGE, INFORMATION_MESSAGE, WARNING_MESSAGE, QUESTIION_MESSAGE, PLAIN_MESSAGE
```

파일 다이얼로그 

JFileChooser는 파일 탐색기(File Browser)와 같은 기능을 하는 파일 다이얼로그를 구현한 스윙 컴포넌트이다. JFileChooser는 같은 모양의 다이얼로그를 출력하여 사용자가 파일이나 디렉터리를 선택하게 한다. JFileChooser를 이용하면 파일 열기 다이얼로그(File Open Dialog)와 파일 저장 다이얼로그(File Save Dialog)를 모두 출력할 수 있다.

파일 열기 다이얼로그 생성

1. JFileChooser 객체 생성 

```
JFileChooser chooser = new JFileChooser();
```

2. 파일 필터 생성

파일 필터(file filter)란 파일 다이얼로그가 특정 확장자를 가진 파일만 보여주기위해 사용되는 필터 정보로, FileNameExtensionFilter 클래스를 이용하여 다음과 같이 생성한다. 

```

FileNameExtensionFilter filter = new FileNameExtendsionFilter ("JPG & GIF Images", "jpg", "gif");
```

파일 필터를 사용한 한 예이다. FileNameExtensionFilter 클래스를 사용하기 위해서 다음 import가 필요하다.

```
import javax.swing.filechooser.*;
```

3. JFileChooser에 파일 필터 설정 

파일 필터를 다이얼로그에 설정할 차례이다. 다음과 같이 setFileFilter() 메소드를 이용하여 파일 다이얼로그에 파일 필터를 설정한다.

```
chooser.setFileFilter(filter);
```

JFileChooser는 여러 개의 파일 필터를 가질 수 있다. JFileChooser에 새로운 파일 필터를 추가하려면 다음과 같이 addChoosableFileFilter() 메소드를 이용하면 된다.

```
chooser.addChoosableFilter(filter);
```

4. 파일 대신 디렉터리를 선택하고자 할 때

setFileSelectionMode() 메소드를 이용하면 파일 다이얼로그에서 파일이나, 디렉터리, 혹은 둘 다 선택 가능하도록 설정할 수 있다. 다음 코드는 파일이나 디렉터리 모두 선택 가능하게 한다.

```
chooser.setFileSelectionMode(JFileChooser.FILES_AND_DIRECTORIES);
``` 

이 코드가 없으면 파일만 선택 가능하다.

5. 파일 열기 다이얼로그 출력 

이제, 파일 다이얼로그를 출력하고 가동해보자. 다음 코드와 같이 showOpenDialog()를 이용하여 파일 다이얼로그를 화면에 출력한다.

```
int ret = chooser.showOpenDialog(null);
```

showOpenDialog(Component parent) 메소드의 인자인 parent는 다이얼로그의 부모 컴포넌트를 지정하는 것으로, 다이얼로그를 출력할 위치를 정할 때, 기준이 되는 부모 컴포넌트이며, null을 주면 전체 화면을 기준으로 위치를 잡게 된다.

6. 사용자가 선택한 파일 이름 알아내기

사용자는 보통 파일을 선택하고 열기 버튼을 누른다. 이때 파일 다이얼로그는 보이지 않게 될 뿐이지 JFileChooser 객체가 사라진 것은 아니다. JFileChooser 객체 내부에는 사용자가 선택한 파일 이름, 파일 경로명, 디렉터리명 등 다양한 정보가 남아 있다. 사용자가 선택한 파일 이름은 다음과 같이 JFileChooser의 getSelectedFile() 메소드를 이용하여 알아낸다.

```
String pathName = chooser.getSelectedFile().getPath(); // 완전경로명
```

7. showOpenDialog()의 리턴 값 처리 

마지막으로 사용자가 취소 버튼을 선택하거나 강제로 다이얼로그를 닫는 경우에 대한 대책이 필요하다. showOpenDialog()는 사용자의 행위에 따라 3가지의 값 중 하나를 리턴한다.

JFileChooser.APPROVE_OPTION : "열기" 버튼을 누른경우
JFileChooser.CANCEL_OPTION : "취소" 버튼을 누른경우
JFileChooser.ERROR_OPTION : 오류가 발생하거나 사용자가 다이얼로그를 닫은경우 

```
int ret = chooser.showOpenDialog(null);
if(ret == JFileChooser.APPROVE_OPTION) {
  String pathName = chooser.getSelectedFile().getPath(); // 선택한 파일의 완전 경로명
  String fileName = chooser.getSelectedFile().getName(); // 파일의 이름 
}
```

파일 저장 다이얼로그 생성

파일 저장 다이얼로그를 출력하기 위해서는 showOpenDialog() 대신 다음과 같이 showSaveDialog()를 호출하면된다.

```
int ret = chooser.showSaveDialog(null);
```

JColorChooser

JColorChooser를 이용하면 사용자가 색을 선택할 수 있는 컬러 다이얼로그를 출력할 수 있다.

컬러 다이얼로그 생성 및 출력

1. 컬러 다이얼로그 출력 

JColorChooser 객체를 생성하여 컨텐트팬이나 패널에 컴포넌트로 삽입하여 사용할 수 있지만, 다음과 같이 JColorChooser의 static 메소드인 showDialog()를 호출하면 독립적으로 출력하여 동작하는 컬러 다이얼로그 출력할 수 있다.

```
Color selectedColor = JColorChooser.showDialog(null,"Color", Color.YELLOW);
```

showDialog() 메소드는 사용자가 선택한 색을 리턴한다.

2. 사용자가 선택한 색 얻기

showDialog()는 확인 버튼을 누르면 선택한 색을 리턴하며, 취소 버튼이나 다이얼로그를 강제로 닫는 경우 null을 리턴한다.

```
if(selectedColor != null) { // 사용자가 색을 선택하고 확인 버튼을 누른 경우 
  // 사용자가 선택한 색 selectedColor 사용 
}
```

탭팬 

JTabbedPane

JTabbedPane은 같이 여러 개의 패널을 겹치게 하여 출력 공간을 공유하는 탭팬을 구현한다. 탭팬에 부착된 각 패널을 탭(tab)이라고 부른다.

탭팬 만들기

1. JTabbedPane 객체 생성

```
JTabbedPane pane = new JTabbedPane(); // 탭 위치는 디폴트로 JTabbedPane. TOP
```

탭은 디폴트로 탭팬의 위쪽에 위치한다. 탭 위치를 왼쪽에 부착하려면 다음과 같이한다.

```
JTabbedPane pane = new JTabbedPane(JTabbedOane.LEFT); // 탭 위치를 왼쪽으로 
```

2. 탭 만들어 붙이기 

탭팬에 탭을 붙이는 작업은 JTabbbedPane의 addTab() 메소드를 이용한다.

```
// img1.jpg 이미지 레이블을 가진 tab1
pane.addTab("tab1", new JLabel(new ImageIcon("images/img1.jpg")));
```

```
class MyPanel extends JPanel {
  ............................
  // 여러 컴포넌트를 붙인다.
  ............................
}
..............................
pane.addTab("tab3", new MyPanel()); // MyPanel 객체를 컴포넌트로 가진 tab3
```

자바 오디오 다루기 

자바의 오디오 API

자바는 응용프로그램에서 오디오를 재생하고 제어할 수 있는 오디오 API를 제공하며 다음 2가지 종류의 오디오 데이터를 다룰 수 있다.

디지털 오디오(Digital Audio) <br>
미디(MIDI : Music Instrument Digital Interface) 데이터 <br>

디지털 오디오란 연주되고 있는 음악이나 사람의 목소리 등 아날로그 소리를 샘플링하여 디지털 데이터로 만든 오디오 데이터로, 음악 CD나 전화 목소리를 녹음한 WAVE 파일 등이 이에 해당한다. javax.sound.sampled 패키지에 제공된다. 미디 데이터란 피아노, 바이올린, 드럼 등 악기의 소리를 낼 수 있는 특별한 장치(MIDI Device)에게, 어떤 악기를, 어느 높이로, 얼마의 시간동안 연주할지를 지시하는 데이터이다. 미디 제어를 위한 클래스의 인터페이스는 javax.sound.midi 패키지에서 제공된다.

디지털 오디오 포맷

```
WAV, AU, AIFF,AIFC
```

오디오 클립과 오디오 재생

1. 오디오 클립 만들기

오디오를 재생하기 위해서는 먼저 오디오 클립(audio clip)을 만들어야 한다. 오디오 클립의 기능은 자바의 Clip 인터페이스 객체를 통해 구현된다. 먼저 비어 있는 오디오 클립은 다음과 같이 생성한다.

```
Clip clip = AudioSystem.getClip(); // AudioSystem 클래스의 static 메소드 getClip()
```

2. 오디오 클립에 오디오 스트림 연결 

```
File audioFile = new File("애국가.wav");
AudioInputStream audioStream = AudioSystem.getAudioInputStream(audioFile);
```

오디오 클립과 오디오 스트림을 연결한다.

```
clip.open(audioStream); // 오디오 클립과 오디오 스트림 연결 
```

3. 오디오 재생

Clip 클래스의 start() 메소드를 호출하면 오디오 재생을 시작한다.

```
clip.start(); // 오디오 재생 시작
```

```
void open(AudioInputStream stream)
오디오 클립은 stream에 존재하는 오디오 형식과 데이터를 인식하고, 재생할 수 있는 준비를 갖춘다.
void start()
현재 프레임 위치에서 오디오 클립을 재생한다. 처음 실행될 때 프레임 위치는 0
void stop()
재생중인 오디오 클립의 재생을 중단한다.
void setFramePosition(int frames)
오디오 샘플 내에 재생할 프레임의 위치를 지정한다. 프레임의 시작번호는 0이다.
void loop(int count)
현재 프레임의 위치에서 시작하여 count만큼 반복 재생한다. count 값이 LOOP_CONTINUOUSLY이면 무한 반복한다.
void close()
오디오 클립의 모든 자원을 반환한다.
```

오디오 클립에 Line 이벤트 처리 

오디오 클립(Clip 객체)은 오디오가 재생되는 도중 여러 상황에서 Line 이벤트가 발생한다. 이것은 Clip 클래스가 Line 클래스를 상속받았기 때문이다.

Line 이베트와 LineListener 인터페이스 

오디오가 재생을 시작할 때, 재생이 중단되었을 때, 오디오 클립이 닫혔을 때, 오디오 클립 객체에 Line 이벤트가 발생한다. Line 이벤트를 처리하는 리스너는 Linelistener 인터페이스이며, Line 이벤트가 발생하면 다음 메소드가 호출된다.

```
public void update(LineEvent e)
오디오가 재생을 시작할 때, 재생이 중단되었을 때, 오디오 클립이 닫혔을 때 호출된다.
```

LineEvent 객체 

LineEvent 객체는 다음 메소드를 통해 이벤트에 대한 여러 정보를 제공한다.

```
Line getLine()
이벤트가 발생하는 오디오 클립 객체(Clip은 Line 인터페이스 상속 받음)
Long getFramePosition()
오디오 내에 이벤트가 발생한 프레임 위치(0부터 시작)
LineEvernt.Type getType()
이벤트 종류로 다음 4가지 값 중 하나 리턴
LineEvent.Type.OPEN : 오디오 클립이 열릴 때(Clip의 open() 호출시)
LineEvent.Type.START : 재생이 시작될 때(Clip의 start() 호출시)
LineEvent.Type.STOP : 재생이 중단될때(Clip의 stop()이나 끝까지 재생되었을 때)
LineEvent.Type.CLOSE : 오디오 클립이 닫히고 모든 자원이 반환되었을 때(Clip의 close() 호출시)
```

오디오 클립 객체에 Line 이벤트 리스너 달기

```
clip.addLineListener(new MyLineListener());
```

- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
