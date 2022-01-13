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
![6d0b50e8cdd06fc3fab36daea536538](https://user-images.githubusercontent.com/60682087/149250819-ff39ed4d-a0a7-41a3-a488-04309bc4d378.png)

- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
