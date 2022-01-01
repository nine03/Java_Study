스트림 (Stream)

스트림은 연속적인 데이터의 흠름 혹은 데이터를 전송하는 소프트웨어 모듈을 일컫는다. 컴퓨터에서 스트림은 도착한 순서대로 데이터를 흘러 보낸다.
자바에서 입출력 스트림은 같이 응용프로그램과 입출력 장치를 연결하는 소프트웨어 모듈이다. 응용프로그램은 입력을 받아 응용프로그램에게 전달한다. 또한 응용프로그램은 출력 스트림에 연결하고 출력 스트림에 출력하면, 출력 스트림은 다른 끝단에 연결된 출력 장치를 제어하여 출력을 완성한다. 스트림 입출력 방식에서, 자바 응용프로그램은 입출력 장치를 직접 제어하는 대신, 입출력 스트림 객체와 연결하여 쉽게 데이터 입출력을 실행한다. 

스트림을 사용하지 않고 자바 응용프로그램이 입출력 장치를 직접 제어하는 코드를 작성하여 입출력을 실행하려 한다면, 응용프로그램 작성이 매우 어렵고, 하드웨어 구조나 제어가 다양한 입출력 장치를 모두 수용할 수 없게 될 것이다. 

입출력 스트림의 특징 

- 스트림의 양끝에는 입출력 장치와 자바 응용프로그램이 연결된다.
자바 응용프로그램은 입력 스트림과 출력 스트림과만 연결하고, 입출력 스트림이 입출력 장치를 제어하고 실질적인 입출력을 담당한다.

- 스트림은 단방향이다.
입력 스트림은 입력 장치에서 응용프로그램으로 데이터를 전송하며, 출력 스트림은 응용프로그램으로부터 받은 데이터를 출력 장치로 전송한다. =

- 스트림을 통해 흘러가는 기본 단위는 바이트나 문자이다.
자바의 스트림 객체는 바이트를 단위로 입출력하는 바이트 스트림과 문자 단위로 입출력하는 문자 스트림으로 나뉜다.

- 스트림은 선입선출, 즉 FIFO구조이다.
입력 스트림에 먼저 들어온 데이터가 응용프로그램에 먼저 전달되고, 출력 스트림은 응용프로그램이 출력한 순서대로 출력 장치에 보낸다.

문자 스트림 (Character stream)과 바이트 스트림 (Byte stream)

문자 스트림은 문자만 다루기 때문에, 문자가 아닌 데이터가 출력되면 보이지 않거나 엉뚱한 기호가 출력되며, 문자가 아닌 정보가 입력되면 응용프로그램에게 엉뚱한 문자가 전달되는 오류가 발생한다. 
문자 스트림을 다루는 클래스는 Reader/Writer를 붙여 구분한다.

바이트 스트림은 바이트를 단위로 다루는 스트림으로, 스트림에 들어오고 나가는 정보를 단순 바이너리(비트들)로 다루기 때문에, 문자이든 이미지 바이트든 상관없이 흘려보낸다. 
바이트 스트림을 다루는 클래스는 공통적으로 이름 뒤에 Stream을 붙인다.

메모장으로 쓰는 경우, 문자 스트림 클래스(FileReader FileWriter)나 바이트 스트림 클래스(FileInputStream FileOutputStream) 모두 사용 가능하지만, 이미지나 오디오/비디오 파일의 데이터는 문자가 아닌 바이너리 정보들이므로 이들을 읽거나 쓰는 경우 반드시 바이트 스트림 클래스(FileInputStream FileOutputStream)를 사용해야한다.

스트림 연결 

키보드로부터 문자를 입력받기 위해 표준 입력 스트임인 System.in과 InputStreamReader 스트림 객체를 연결한다.

<pre><code>
InputStreamReader rd = new InputStreamReader(System.in);
</pre></code>

<pre><code>
int c = rd.read(); // 입력 스트림으로부터 키입력. c는 입력된 키의 문자 값 
</pre></code>

문자 스트림 클래스

문자 스트림은 2바이트의 유니코드 문자를 단위로 입출력하는 스트림이다. 문자화되지 않는 바이너리 바이트 값들은 문자 스트림 클래스에서 처리할 수 없다. 따라서 이미지와 같은 바이너리 바이트 값들은 문자 스트림 클래스에서 처리할 수 없다. 문자 입력 스트림은 바이트들을 전달받고, 이 바이트들을 로컬 문자 집합에 있는 문자인지 비교하여 문자로 변환한다. 

FileReader를 이용한 텍스트 파일 읽기 

파일 입력 스트림 생성 

파일 입력 스트림을 생성하고 스트림을 파일과 연결한다. 다음은 FileReader로 파일 입력 스트림을 생성한다.

<pre><code>
FileReader fin = new FileReader("c:\\test.txt");
</pre></code>

FileReader의 생성자는 c:\\test.txt 파일을 찾아 열고, 파일과 스트림을 연결한다. c:\\test.txt 파일은 문자들로만 구성된 텍스트 파일이다.

파일 읽기

파일 입력 스트림(fin)을 이용하여 파일을 읽을 수 있다. fin.read()는 연결된 파일로부터 문자 하나를 읽어 리턴하며, 파일의 끝(EOF)을 만나면 -1을 리턴한다. fid.read()를 이용하여 파일 전체를 읽어 화면에 출력해준다.

<pre><code>
int c;
while((c = fin.read()) != -1) { // 문자 하나를 c에 읽어 들인다. 파일 끝까지 반복한다.
  System.out.print((char)c); // 문자 c를 화면에 출력한다.
}
</pre></code>

파일이 큰 경우 한 번에 한 문자씩 읽으면 읽는 속도가 너무 느리기 때문에  한 번에 한 블록만큼 읽는 read()를 이용하면 된다.

<pre><code>
char [] buf = new char[1024]; // 1024는 1KB이다. 
int n = fin.read(buf); // 한번에 1024개 문자를 읽어 buf[]에 저장하고 실제 읽은 문자수 리턴 
</pre></code>

스트림 닫기 

파일 읽기가 더 이상 필요 없으면 close() 메소드를 호출하여 파일 입력 스트림을 닫는다. 닫힌 스트림으로부터는 더 이상 읽을 수 없다.

<pre><code>
fin.close();
</pre></code>

FileReader의 생성자 

<pre><code>
FileReader(File file) : file로부터 읽는 FileReader 생성
FileReader(String name) : name 이름의 파일로부터 읽는 FileReader 생성
</pre></code>

FileReader, Reader, InputStreamReader의 공통주요 메소드 

<pre><code>
int read() : 한 개의 문자를 읽어 정수형으로 리턴
int read(char[] cbuf) : 문자들을 읽어 cbuf 배열에 저장하고 읽은 개수 리턴 
int read(char[] cbuf, int off, int len) : 최대 len 개수의 문자들을 읽어 cbuf 배열의 off 위치부터 저장                                           하고 실제 읽은 개수 리턴
String getEncoding() : 스트림이 사용하는 문자 집합의 이름 리턴 
void close() : 입력 스트림을 닫고 관련된 시스템 자원 해제 
</pre></code>

파일 입출력과 예외 처리 

파일의 결로명이 틀린 경우, FileReader 생성자는 FileNoFoundException 예외를 발생시킨다.

<pre><code>
FileReader fin = new FileReader("c:\\test.txt"); // FileNotFoundException 발생 가능 ]
</pre></code>

파일 읽기, 쓰기, 닫기를 하는 동안 입출력 오류가 발생하면, read(), write(), close() 메소드는 IOException 예외를 발생시킨다.

<pre><code>
int c = fid.read(); // IOException 발생 가능
</pre></code>

try - catch 

<pre><code>
try {
  FileReader fin = new FileReader("c:\\test.txt");
  ...
  int c = fin.read();
  ...
  fin.close();
} catch(FileNotFoundException e) {
  System.out.println("파일을 열 수 없음");
} catch(IOException e) {
  System.out.println("입출력 오류");
}
</pre></code>

문자 집합과 InputStreamReader를 이용한 텍스트 파일 읽기

InputStreamReader는 스트림에 입력되는 바이트 데이터를 문자 집합을 통해 문자로 변환한다. 이를 위해 InputStreamReader의 생성자에 문자 집합을 지정해야 한다.

InputStreamReader 생성자

<pre><code>
InputStreamReader(InputStream in) : in으로 부터 읽는 기본 문자 집합의 InputStreamReader 생성 
InputStreamReader(InputStream in, Charset cs) : in으로부터 읽는 cs 문자 집합의 InputStreamReader 생성
InputStreamReader(InputStream in, String charsetName) : in으로부터 읽는 charsetName 문자 집합의 InputStreamReader생성
</pre></code>
- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
