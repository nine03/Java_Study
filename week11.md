GUI 컴포넌트

모든 GUI 플랫폼에서 그리고(painting)의 기본은 GUI 컴포넌트가 자신의 모양을 스스로 그린다는 점이다.

paintComponent()

모든 스윙 컴포넌트가 가지고 있는 메소드로서, 스윙 컴포넌트가 자신의 내부를 그리는 paintComponent() 메소드의 원형은 다음과 같다.


```
void paintComponent(Graphics g) // 컴포넌트의 내부 모양을 그린다. 
Graphics 객체 g를 그래픽 컨텍스트(graphics context)라고 부르며 자바 플랫폼에 의해 생성되어 공급된다.
```

컴포넌트가 처음으로 그려질 때 <br>
컴포넌트의 크기나 위치 변경 등 컴포넌트에 변화가 생길때 <br>
다른 원도우에 의해 가려졌다가 드러날때 <br>
아이콘화되었다가 본래 크기로 복구할 때 <br>
응용프로그램이 컴포넌트의 repaint() 메소드를 호출하여 강제로 다시 그릴 때 <br>

paintComponent()의 오버라이딩 

개발자가 JComponent를 상속받아 새로운 컴포넌트를 설계하든지 아니면 기존의 스웡컴포넌트의 모양을 다르게 그리고자 할 때, 다음과 같이 paintComponent()를 오버라이딩하여 자신만의 컴포넌트 모양을 그릴수 있다.

```
class MyComponenet extends JXXX {  // JXXX는 기존의 스윙 컴포넌트
          ...
public void paintComponent(Graphics g) { // 오버라이딩 
        ... 필요한 코드 작성 ...
  }
}
```

JPanel에 그리기 

JPanel은 빈 캔버스와 같이 아무 모양도 없는 빈 컨테이너로서, 다양한 GUI를 창출할 수 있는 캔버스로 적합하기 때문에 그래픽을 위해 많이 사용된다.

```
class MyPanel extends JPanel {
  public void paintComponent(g); { // JPanel에 구현된 paintComponent() 호출
  super.paintComponent(g); // JPanel에 구현된 paintComponent() 호출
    g.setColor(Color.BLUE); // 파란색 선택. 이후 그리기는 파란색으로 진행 
    g.draw(10,10,50,50); // (10,10) 위치에 50x50 크기의 사각형 그리기
    g.draw(50,50,50,50); // (50,50) 위치에 50x50 크기의 사각형 그리기
    g.draw(90,90,50,50); // (90,90) 위치에 50x50 크기의 사각형 그리기
  }
}
```

Graphics

Graphics 클래스의 경로명은 java.awt.Graphics이며, 그리기, 칠하기, 이미지 출력, 클리핑 등 GUI 프로그래밍에 있어 필요한 필드와 메소드를 제공한다.

Graphics의 좌표 체계

![f06a6148037586999178a40b292ad5c](https://user-images.githubusercontent.com/60682087/149489741-e5616ba1-b6ba-4333-a90d-d4dad37af042.png)
그림1

자바 그래픽의 좌표값은 그림1과 같이 그래픽 대상 컴포넌트의 왼쪽 상단 모서리가(0,0)이고, 오른쪽으로 X축의 값이 증가하며, 아래쪽으로 Y축의 값이 증가한다.

Graphics기능

색상 선택하기 <br>
문자열 그리기 <br>
도형 그리기 <br>
도형 칠하기 <br>
이미지 그리기 <br>
클리핑 <br>

문자열 그리기 

```
void drawString(String str, int x,int y)
str 문자열을 (x,y) 영역에 그린다. 현재 Graphics에 설정된 색과 폰트로 문자열을 출력한다.
```

drawString()을 사용하여 (30,30) 위치에서 "자바는 재밌다. ~~ "를 출력하는 예를들면 다음과 같다.

```
Graphices g;
g.drawString("자바는 재밌다. ~~",30,30);
```

Color 클래스

Color는 색을 표현하는 클래스이다. 자바에서 색은 r(Red),g(Green),b(Blue) 성분으로 구서오디며, 각 성분은 0 ~ 225(8비트) 범위의 정수이다. 

```
Color(int r, int g, int b) r,g,b 값으로 sRGB 색 생성int
Color(int rgb) rgb는 32비트의 정수이지만 하위 24비트만 유효. 즉 0x00rrggbb로 표현. 각 바이트가 r,g,b의 색 성분 
```

```
Graphics g;
g.setColor(new Color(255,0,0)); // 빨간색을 생성하여 그래픽 색으로 지정한다.
g.setColor(new Color(0x0000ff00)); // 초록색을 생성하여 그래픽 색으로 지정한다.
g.setColor(Color.YELLOW); // 노란색을 그래픽 색으로 지정한다.
```

Font 클래스 

```
Font(String fontFace, int style, int size)
fontFace : "고딕체", "Ariel" 등과 같은 폰트 이름
style : 문자의 스타일로 Font.BOLD, Font.ITALIC, Font.PLAIN 중 택일
size : 픽셀 단위의 문자 크기 
```

```
Font f = new Font("Times New Roman",Font.ITALIC,30);
```

Graphics에서 색상과 폰트 활용 

```
void setColor(Color color) // 그래픽 색을 color로 설정. 그리기 시에 색으로 이용
void setFont(Font font) // 그래픽 폰트를 font로 설정. 문자열 출력시 폰트로 이용
```

도형 그리기 

![7e105835f35d8da27fea590fe724684](https://user-images.githubusercontent.com/60682087/149494843-a7b6dc14-efdb-4596-b676-b954fa1e220f.png)

원호와 폐다각형 그리기 

![e71567c088baa526c96ceed357dd166](https://user-images.githubusercontent.com/60682087/149495169-a0c7430a-bbf7-4c79-9a6a-98b4466a5e8a.png)

도형 칠하기

도형 칠하기란 도형의 외곽선과 내부를 동일한 색으로 칠하는 기능이다. 도형의 외곽선과 내부를 분리하여 칠하는 기능은 없다. 내부 색과 외곽선 색을 달리하고자 하면, 도형 내부를 칠한 후, 다른 색으로 외곽선을 그려야 한다. 도형 칠하기를 위한 메소드는 다음과 같이 그리기 메소드 명에서 draw를 fill로 바꾸면 된다.

```
drawRect() -> fillRect()
drawArc() -> fillArc()
```

이미지 그리기 

이미지 그리는 2가지 방법

JLabel 컴포넌트를 이용하여 이미지 그리기 <br>
Graphics의 메소드 <br>

첫번째 방법은 JLabel을 이용하여 이미지를 출력한다. 

두 번째 방법은 Graphics의 drawImage() 메소드를 호출하여 원하는 위치에, 원하는 크기로, 원하는 비율로 이미지를 출력하는 방법이다. 이 방법은 이미지의 원본 크기와 다르게 그릴 수 있는 장점이 있으나, 이미지를 그리는 코드를 직접 작성해야 하는 부담이 있다. 

Graphics로 이미지 그리기 


```
boolean drawImage(Image img, int x, int y, Color bgColor, ImageObserver observer)
boolean drawImage(Image img, int x, int y, ImageObserver observer)
img : 이미지 객체
x,y : 이미지가 그려질 좌표 
bgColor :  이미지가 투명한 부분을 가지고 있을 때 투명한 부분에 칠해지는 색상
observer : 이미지 그리기의 완료를 통보받는 객체
img를 그래픽 영역의(x,y) 위치에 img의 원본 크기로 그린다.
```

크기 조절하여 그리기 

```
boolean drawImage(image img, int x, int y, int width, int height, Color bgColor, ImageObserver observer)
boolean drawImage(Image img, int x, int y, int width, int height, ImageObserver observer)
width : 그려지는 폭으로서 픽셀 단위
height : 그려지는 높으로서 픽셀 단위
img를 그래픽 영역의 (x,y) 위치에 width x height 크기로 조절하여 그린다.
```

원본의 일부분을 크기 조절하여 그리기 

```
boolean drawImage(Image img, int dx1, int dy1, int dx2, int dy2, int sx1, int sy1, int sx2, int sy2, Color bgColor, Image Observer observer)
boolean drawImage(Image img, int dx1, int dy1, int dx2, int dy2, int sx1, int sy1, int sx2, int sy2, ImageObserver observer)

dx1, dy1 : 그래픽 영역상의 왼쪽 상단 모서리 좌표
dx2, dy2 : 그래픽 영역상의 오른쪽 하단 모서리 좌표 
sx1, sy2 : 소스 이미지(img) 내의 왼쪽 상당 모서리 좌표
sx2, sy2 : 소스 이미지(img) 내의 오른쪽 하단 모서리 좌표 
img의 (sx1,sy1)에서 (sx2, sy2)로 구성된 사각형 부분을 그래픽 영역 내의 (dx1, dy1)에서 (dx2,dy2)의 사각형 크기로 변형하여 그린다.
```

이미지 로딩 : Image 객체 생성

이미지를 그리기 전에 이미지를 로딩하여 Image 객체를 만들어야 한다.

```
ImageIcon icon = new ImageIcon("images/image0.jpg"); // 파일로부터 이미지 로딩
Image img = icon.getImage();
```

img는 이미지의 픽셀 값과 이미지 크기 등의 정보를 가지고 있으므로, 다음 코드로 이미지의 폭과 높이를 알아낼 수 있다.

```
int width = img.getWidth(this); // 이미지의 폭. this는 ImageObserver로서, null도 기능
int height = img.getHeight(this); // 이미지의 높이 
```

(20,20) 위치에 이미지 원본 크기로 그리기 

```
class MyPanel extends JPanel {
   public void paintComponent(Graphics g) {
   super.paintComponent(g);
   g.drawImage(img,20,20,this);
   }
}
```

drawImage()의 마지막 인자에는 그리기 완료를 통보받는 객체를 지정하는데, 이 코드에서 this를 주어 MyPanel이 통보를 처리하도록 하였다. 통보 자체를 무시하고자 한다면 null을 주면 된다.

이미지를 (20,20) 위치에 100 x 100 크기로 그리기 

```
class MyPanel extends JPanel {
  public void paintComponent(Graphics g) {
    super.paintComponent(g);
    g.drawImage(img,20,20,100,100,this);
  }
}
```

이미지를 패널의 크기에 꽉 차도록 그리기 

```
class MyPanel extends JPanel {
  public void paintComponent(Graphics g) {
    super.paintComponent(g);
    g.drawImage(img,0,0,this.getWidth(),this.getHeight(), this);
  }
}
```

원본 이미지의 일부분을 크기 조절하여 그리기 

원본 이미지 img의 (50,0)에서 (150,150)의 사각형 부분을 MyPanel의 (20,20)에서 (250,100) 영역에 그리는 코드는 다음과 같다.

```
class MyPanel extends JPanel {
  public void paintComponent(Graphics g) {
    super.paintComponent(g);
    g.drawImage(img,20,20,250,100,50,0,150,150,this);
  }
}
```

클리핑(Clipping)

클리핑는 컴포넌트의 전체 그래픽 영역 내 특정 사각형 영역에만 그래픽이 이루어진도록 하는 기능이다. 클리핑이 이루어지는 사각형 영역을 클리핑 영역(clipping area)이라고 부르며 반드시 사각형으로 설정된다.

```
void setClip(int x, int y, int w,int h)
그래픽 대상 컴포넌트의 (x,y) 위치에서 w x h의 사각형 영역을 크리핑 영역으로 지정
void clipRect(int x, int y, int w,int h)
Graphics 객체 내에 유지되어 돈 기존 클리핑 영역과 (x,y)에서 w x h 크기로 지정된 사각형 영역의 교집합 영역을 새로운 클리핑 영역으로 설정 한다. clipRect()이 계속 호출되면 클리핑 영역은 계속 줄어들게 된다.
```

스윙의 페인팅 메커니즘

스윙 컴포넌트들이 그려지는 과정

스윙에서 페인팅의 기본 골격은 JComponent에 의해 구현되어 있다. 모든 스윙 컴포넌트들을 JComponent를 상속받음으로써 자연스럽게 스윙의 페인팅 메커니즘에 따라가도록 된다.

![1f06012879197da53b89b75b3e9bcf7](https://user-images.githubusercontent.com/60682087/149510166-ed34f070-f3f2-499e-ac57-0a5457442adf.png)

```
public void paint(Graphics g) { // g가 아래 3개의 메소드에 그대로 전달된다.
	...
	paintComponent(g); // 1. 컴포넌트 자신의 내부 모양 그리기
	paintBorder(g); // 2. 컴포넌트 자신의 외곽 그리기
	paintChildren(g); // 3. 컴포넌트의 자식들 그리기
	...
}
```

![3c56920395e05531a63a853b9345125](https://user-images.githubusercontent.com/60682087/149510717-6f3913bd-9dc1-48b5-9f9c-494fddd3a7d3.png)

repaint()

repaint()는 Component 클래스의 메소드로 자바 플랫폼에게 컴포넌트에 변화가 일어났으니 강제로 페인팅할 것을 지시하는 메소드이다.

```
component.repaint(); // 컴포넌트 다시 그리기 지시 
```

컴포넌트를 다시 그리기 위해서는 부모 컴포넌트부터 그리는 것이 좋다. 컴포넌트의 크기나 위치가 변경되었다면, 컴포넌트의 부모에게 컴포넌트의 이전 모양이나 이전 위치의 잔상을 지우도록 해야 하기 때문이다. 부모 컴포넌트에서부터 다시 그리고자 하는 경우 다음과 같이 호출한다.

```
component.getParent().repaint(); // 컴포넌트의 부모 컨테이너에게 다시 그리기 지시 
```

revalidate()

revalidate()는 컨테이너의 배치관리자에게 자식 컴포넌트의 배치를 다시 하도록 지시하는 메소드이다. 컨테이너에 컴포넌트를 새로 삽입하거나 삭제하여 컨테이너가 출력된 모양에 변화가 생겼다면 revalidate()를 호출하여 컨테이너를 다시 그리도록 해야 한다. revalidate()가 내부적으로 repaint()를 부르지만 상황에 따라 잘 처리되지 않는 경우도 있다. 그러므로 컨테이너에 컴포넌트를 새로 상입하거나 삭제하였다면, 다음 두라인 모두 호출하여 컨테이너의 화면을 갱신해야 한다.

```
container.revalidate(); // 컨테이너에 부착된 컴포넌트의 재배치 지시
container.repaint(); // 컨테이너 다시 그리기 지시 
```

- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
