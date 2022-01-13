스윙 컴포넌트 

컴포넌트 기반 GUI 프로그램이다. 스윙 패키지에 주어진 GUI 컴포넌트를 이용하여 쉽게 GUI 프로그램을 작성 할 수 있는 장점이 있지만, 자바 패키지에서 제공하는 GUI 컴포넌트의 한계를 벗어날 수 없다. 그래픽 기반 GUI 프로그래밍이다. 선, 원 등의 도형과 이미지를 이용하여 그래픽으로 직접화면에 그린다.

스윙 컴포넌트와 상속 구조

기본적인 스윙 컴포넌트들과 그들 사이의 상속 관계를 보여준다. 스윙 컴포넌트는 JComponent를 상속받으며, 이름이 모두 J로 시작된다. 그러므로 JComponent에는 스윙 컴포넌트들이 상속받는 많은 공통 메소드와 상수들이 작성되어 있다. 왼쪽 아래에는 버튼으로 작동하는 여러 스윙 컴포넌트들이 있고, 오른쪽에는 텍스트 입력 창의 기능을 하는 컴포넌트들이 있고, 메뉴와 관련된 컴포넌트들을 알아두어야 한다.

![0316f7648c35ff0fe5658e5b7c70ef7](https://user-images.githubusercontent.com/60682087/149241703-8f661ea5-af1b-41b9-b861-32c2cc926c26.png)

배경색, 전경색, 폰트

<pre><code>
c.setBackground(Color.YELLOW); // 컴포넌트의 배경색을 노란색으로 설정
c.setForeground(Color.MAGENTA); // 컴포넌트 c의 글자색을 마젠타로 설정
c.setFont("Arial", Font.ITALIC,20); // 20픽셀 이탤릭 Arial 체로 설정
</pre></code>

위치와 크기

<pre><code>
c.setLocation(100,200); // 컴포넌트 c를 (100,200) 위치로 이동
c.setSize(100,100); // 컴포넌트 c의 크기를 100x100 크기로 설정

int x = c.getX(); int y = c.getY();
int w = c.getWidth(); int h = c.getHeight();
</pre></code>

활성화/비활성화, 보이기/숨기기

setEnabled()로 활성화/비활성화, setVisible()로 보이기/숨기기를 할 수 있다.

<pre><code>
c.setEnabled(false); // 컴포넌트 c가 작동하지 않게 함. 버튼의 경우 클릭해도 무반응
c.setVisible(false); // 컴포넌트 c가 화면에 보이지 않게 함 
</pre></code>

부모 컨테이너 찾기

getParent()를 이용하면 컴포넌트 c가 담긴 부모 컨테이너를, getTopLevelAncestor()를 호출하면 최상위 컨테이너를 알아낼 수 있다.

<pre><code>
Container c = c.getParent(); // 컴포넌트 c의 부모 컨테이너 알아내기
MyFrame frame = (Myframe)c.getTopLevelAncestor(); // c의 최상위 스윙 프레임 알아내기 

c.remove(child); // 컨테이너 c에서 자식 컴포넌트 child를 삭제한다.

child가 제거된다고 바로 화면에서 사라지지 않는다.
c.revalidate(); // 컨테이너 c의 재배치
c.repaint(); // 컴포넌트 c의 다시 그리기 
</pre></code>

JLabel

JLabel은 문자열이나 이미지를 스크린에 출력하는 레이블 컴포넌트를 만드는 클래스이다.

레이블 컴포넌트 생성

레이블 컴포넌트는 레이블이라고도 부르며, 다음 생성자를 이용하여 생성한다.

![6c55ccbae881708aba9b5de0918dc52](https://user-images.githubusercontent.com/60682087/149243641-890c3596-604e-4a26-b48d-e21c23d28d86.png)

문자열 레이블 생성 

<pre><code>
JLabel textLabel = new JLabel("사랑합니다")
</pre></code>

이미지 레이블 생성

이미지를 가진 레이블을 생성하기 위해서는, ImageIcon 클래스를 이용하여 이미지 파일로부터 이미지 객체를 생성하고, JLabel로 이미지 레이블 생성한다.

<pre><code>
ImageIcon image = new ImageIcon("images/sunset.jpg");
JLabel imageLabel = new JLabel(image);
</pre></code>

sunset.jpg 파일의 경로명은 "images/sunset.jpg" 이므로 이클립스의 경우 sunset.jpg는 프로젝트의 images 폴더에 있어야 한다.

문자열, 이미지, 수평 정렬 값을 가진 레이블 생성

문자열과 이미지를 함께 가진 레이블을 생성하고, 문자열과 이미지를 레이블 컴포넌트 영역 내에 중앙 정렬한다.

<pre><code>
ImageIcon image = new ImageIcon("images/sunset.jpg");
JLabel imageLabel = new JLabel("사랑합니다",image,SwingConstants.CENTER);
</pre></code>

JButton

JButton은 버튼 컴포넌트를 만드는데 이용된다. 레이블 컴포넌트가 문자열이나 이미지를 화면에 출력하는 용도로 사용되는 것이라면, 버튼은 사용자로부터 명령을 받기 위해 사용된다. 버튼을 마우스로 클릭하거나 키로 선택하면 Action 이벤트가 발생한다.

버틑은 다음 생성자를 이용하여 생성한다.

![3c99c1e5ac701ec4ad76eb2795c438d](https://user-images.githubusercontent.com/60682087/149251108-0644bdba-c5bc-4952-8506-b04ee3ebabac.png)

<pre><code>
JButton btn = new JButton("hello");
</pre></code>

이미지 버튼 만들기 

JButton은 사용자의 버튼 조작에 대한 시각적 효과를 극대화하기 위해, 마우스 접근에 따라 모양이 다른 3개의 버튼 이미지를 출력할 수 있다.

normalIcon

버튼이 보통 상태에 있을 때 출력되는 디폴트 이미지로, 생성자나 JButton의 setIcon(Icon image)을 통해 설정한다.

rolloverIcon

버튼 위에 마우스가 올라갈 때 출력되는 이미지로, JButton의 setRolloverIcon(Icon image)을 호출하여 설정한다.

pressedIcon

버튼이 눌러져 있는 동안 출력되는 이미지로, JButtond의 setPressedIcon(Icon image)을 호출하여 설정한다.

<pre><code>
    ImageIcon normalIcon = new ImageIcon("images/normalIcon.gif");
		ImageIcon rolloverIcon = new ImageIcon("images/rolloverIcon.gif");
		ImageIcon pressedIcon = new ImageIcon("images/pressedIcon.gif");

		JButton button = new JButton("테스트버튼", normalIcon); // normalIconㄷ 달기
		button.setRolloverIcon(rolloverIcon); // rolloverIcon 달기
    button.setPressedIcon(pressedIcon); // pressedIcon 달기
		
실제로는 normalIcon 이미지 하나만 가진 디폴트 버튼을 많이 사용하는데, 실행 중에 디폴트 이미지를 변경하려면 다음과 같이 setIcon() 메소드를 호출하면 된다 

button.setIcon(new ImageIcon("images/newIcon.gif")); // 디폴트 이미지변경
</pre></code>

버튼과 레이블의 정렬(Alignment)

버튼 컴포넌트와 레이블 컴포넌트는 정렬 기능을 이용하면, 컴포넌트 내에 문자열과 이미지의 위치를 조정할 수 있다. 정렬은 수평 정렬과 수직 정렬로 구분된다.

수평 정렬은 왼쪽, 중앙, 오른쪽 정렬의 3가지로, JButton이나 JLabel에 다음 메소드를 이용하면 된다.

![cd044db34e35176c90018ec127d9357](https://user-images.githubusercontent.com/60682087/149253358-d49091b6-76f2-46c8-85c5-72d4693572bf.png)

<pre><code>
contentPane.setLayout(new BorderLayout()); // 버튼으로 꽉 채우기 위해
ImageIcon normalIcon = new ImageIcon("images/normalIcon.gif");
JButton btn = new JButton("call~~",normalIcon);
btn.setHorizontalAlignment(SwingConstants.LEFT); // 버튼 안에서 이미지와 문자열의 왼쪽 정렬
contentPane.add(btn);
</pre></code>

SwingConstants.LEFT 대신 SwingConstants.CENTER나 SwingConstants. RIGHT를 사용하면 중앙정렬, 오른쪽 정렬을 할 수 있다.

수직 정렬 

수직 정렬은 위쪽, 중앙, 아래쪽 정렬의 3가지로서, JButton이나 JLabel의 다음 메소드를 이용하면 된다.

![98f3de816bf7f73259edf4ba8ee83cf](https://user-images.githubusercontent.com/60682087/149254597-cc8ca1b9-8866-40fe-be77-70b0d6a3de04.png)

<pre><code>
contentPane.setLayout(new BorderLayout()); // 버튼으로 꽉 채우기 위해
ImageIcon normalIcon = new ImageIcon("images/normalIcon.gif");
JButton btn = new JButton("call~~",normalIcon);
btn.setHorizontalAlignment(SwingConstants.TOP); // 버튼 안에서 이미지와 문자열의 위쪽 정렬
contentPane.add(btn);
</pre></code>

JCheckBox

JCheckBox를 이용하면 선택(selected)과 해제(deselected)의 두 상태만 가지는 체크박스 컴포넌트를 만들 수 있다. 체크박스는 체크박스 문자열과 체크박스 이미지로 구성되어있다.

체크박스 컴포넌트 생성 

체크박스는 다음 생성자를 이용하여 생성하며, 디폴트가 해제 상태이다.

![755732dd753c6361437bc1c32bb140f](https://user-images.githubusercontent.com/60682087/149312580-63d33b9a-11e7-477b-a6a4-983dc852ff5f.png)

문자열 체크박스 

"사과" 문자열을 가진 체크박스를 만드는 코드는 다음과 같고, 해제 상태로 생성된다.

<pre><code>
JCheckBox apple = new JCheckBox("사과");
</pre></code>

"배" 문자열을 가지고 처음부터 선택 상태인 체크박스는 다음 코드로 생성한다.

<pre><code>
JCheckBox pear = new JCheckBox("배",true); 
</pre></code>

이미지 체크박스 

이미지 체크박스는 체크박스 모양대신, 선택 상태 때 출력할 별도의 이미지를 필요로한다. 선택 상태 이미지는 JCheckBox의 setSelectedIcon(ImageIcon) 메소드를 이용하여 등록한다.

<pre><code>
ImageIcon cherryIcon = new ImageIcon("images/cherry.jpg"); // 해제 상태 이미지 
ImageIcon selectedCherryIcon = new ImageIcon("images/selectedCherry.jpg"); // 선택 상태 이미지
JCheckBox cherry = new JCheckBox("체리", cherryIcon); // 해제 상태 이미지만 가진 체크박스 생성
cherry.setSelectedIcon(selectedCherryIcon); // 선택 상태의 이미지 등록
</pre></code>

이미지 체크박스의 경우 다음과 같이 체크박스의 외곽선이 보이도록 하여 체크박스 영역을 분명히 할 수 있다.

<pre><code>
cherry.setBorderPainted(true);
</pre></code>

JCheckBox에서 Item 이벤트 처리 

Item 이벤트는 체크박스나 라디오버튼의 선택 상태가 바뀔 때 발생하는 이벤트이다. 이미 선택 상태인 라디오버튼을 누르는 경우 선택 상태에 대한 변화가 없기 때문에 Item 이벤트는 발생하지 않는다. 선택/해제 행위는 대부분 마우스 클릭으로 이루어지지만, 다음과 같이 자바 코드로 실행할 수도 있다.

<pre><code>
JCheckBox c = new JCheckBox("사과");
c.setSelected(true); // 선택 상태로 설정, false이면 해제 상태로 설정 
</pre></code>

마우스로 선택하든 프로그램 코드로 실행하든 선택 상태가 변할 때 Item 이벤트가 발생한다.

ItemListener 인터페이스 

![8744f7006c2e3b4a8a2958282728c01](https://user-images.githubusercontent.com/60682087/149317755-c71c6dd3-716c-4ddf-8578-514e435ff765.png)

Item 이벤트 리스너는 ItemListener 인터페이스를 상속받아 만들며, 다음 하나의 메소드로 구성된다. 이 메소드는 체크박스의 선택 상태에 변화가 일어나면 호출된다.

ItemEvent 객체 

Item 이벤트가 발생하면 ItemEvent 객체가 생성되어 itemStateChanged()의 인자로 전달된다. 개발자는 ItemEvent 객체의 다음 메소드를 호출하여 체크 상태의 변화와 이벤트 소스 컴포넌트를 알아낼 수 있다.

![bcddbcba13a71d03980cbf0fd916546](https://user-images.githubusercontent.com/60682087/149318674-e0c77dbe-0347-408d-9438-d1ae2b3c91ba.png)

체크박스 컴포넌트에 ItemListener 리스너 달기

JCheckBox의 addItemListener()메소드를 이용하여 다음과 같이 등록한다.

<pre><code>
checkbox.addItemListener(new MyItemListener);
</pre></code>

JRadioButton

JRadioButton을 이용하면 라디오버튼을 만들 수 있다. 라디오버튼은 생성, 메소드, 이벤트 처리에 있어 체크박스와 동일하지만, 한 가지 면에서 다르다. 체크박스는 독립적으로 선택/해제되지만, 라디오버튼은 여러 개가 하나의 버튼 그룹을 형성하고, 그룹 내에서 하나만 선택 가능하다.

JRadioButton 컴포넌트의 생성

라디오버튼은 다음 생성자를 이용하여 생성하며, 디폴트가 해제 상태이다.

![e9687491d55d56bbc685115c4e86c11](https://user-images.githubusercontent.com/60682087/149319994-3a840b16-e60e-46e4-ae90-7ac25e8debe6.png)

이미지 라디오버튼을 만들려면 디폴트 이미지와 선택 상태를 나타내는 2개의 이미지가 필요하다. 

버튼 그룹과 라디오버튼의 생성 과정 

라디오버튼의 생성은 JRadioButton의 생성자를 호출하는 것으로 끝나지 않는다. 우선 ButtonGroup 클래스를 이용하여 라디오버튼들을 묶을 버튼 그룹 객체를 생성한다. 그러나 나서 JRadioButton 생성자로 라디오 버튼을 생성하고 버튼 그룹에 추가한다.그리고 라디오 버튼을 화면에 출력하기 위해 컨테이너에 삽입한다.

![65c1c1cedd44626b236e9a28aaa6660](https://user-images.githubusercontent.com/60682087/149321015-d2351e20-d19f-47a5-b615-3ccdd51ea3a9.png)

JRadioButton과 Item 이벤트 처리 

라디오버튼에 선택 상태가 변경되면 Item 이벤트가 발생한다. 마우스와 키보드를  이용하거나 프로그램에서 JRadioButton의 setSelected()를 호출하여 선택 상태를 변경 할 수 있다. 이 경우 모두 Item 이벤트가 발생한다. Item 이벤트는 ItemListener 인터페이스의 다음 메소드에 의해 처리한다.

<pre><code>
void itemStateChanged(ItemEvent e) // 라디오버튼의 선택 상태가 변경되었을 때 호출된다.
</pre></code>

JTextField

JTextField를 이용하면 한 줄의 문자열을 입력받는 창을 만들 수 있다. 입력 가능한 문자 개수와 창의 크기는 응용프로그램에서 변경할 수 있다. 텍스트필드에 문자열 입력 도중<Enter> 키가 입력되면 Action 이벤트가 발생한다.

JTextField 컴포넌트의 생성

텍스트필드 컴포넌트의 생성자는 다음과 같다
  
![877b78e7707632ee9052c241e3bbc16](https://user-images.githubusercontent.com/60682087/149322673-ee521e9d-46bb-402e-846f-6bc11eaa2192.png)

<pre><code>
JTextField tf1 = new JTextField(10);
</pre></code>
  
JTextField의 주요 메소드 활용

문자열의 편집 불가능하게 하기

다음 코드는 사용자가 텍스트필드 창에 문자열을 입력하거나 수정할 수 없도록 한다.

<pre><code>
JTextField tf = new JTextField();
tf.setEditable(false); // 텍스트필드 창에 입력하거나 수정 불가
</pre></code>

  
입력 창에 문자열 출력   

다음 코드는 텍스트필드 입력 창에 있는 문자열을 "hello"로 수정하여 출력한다.

<pre><code>
tf.setText("hello"); // "hello"를 텍스트필드 창에 출력 
</pre></code>
  
문자열의 폰트 지정 
  
다음 코드는 텍스트필드 입력 창의 문자열을 고딕체에 이탤릭 20픽셀 크기로 출력되게한다.
  
<pre><code>
tf.setFont(new Font("고딕체",Font.ITALIC,20));
</pre></code>
  
JTextArea

JTextArea를 이용하면 여러 줄의 문자열을 입력받을 수 있는 창을 만들 수 있다. 창의 크기보다 많은 줄과 문자를 입력할 수 있지만 스크롤바를 지원하지 않는다. JTextArea 컴포넌트를 JScrollPane에 삽입하여야 스크롤바 지원을 받을 수 있다.
  
JTextArea 컴포넌트의 생성 

텍스트영역 컴포넌트의 생성자는 다음과 같다.

![3236d10da316b3786c111f9765b142a](https://user-images.githubusercontent.com/60682087/149325222-180f6590-e85c-4459-bc99-f6518b99182d.png)
  
<pre><code>
container.add(new JCrollPane(new JTextArea("hello",7,20)));
</pre></code>
- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
