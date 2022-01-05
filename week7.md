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

InputStreamReader로 문자 입력 스트림 생성

InputStreamReader는 바이트 스트림을 전달받아 문자 정보로 변환하는 스트림 객체이다. 

<pre><code>
FileInputStream fin = new FileInputStream("c:\\Temp\\hangul.txt");
</pre></code>

c:\Temp\hangul.txt는 메모장으로 작성한 한글 텍스트 파일이다. 그러고 나서 다음과 같이 InputStreamReader 객체를 생성한다.

<pre><code>
InputStreamReader in = new InputStreamReader(fin,"MS949");
</pre></code>

생성자 InputStreamReader()의 두 번째 매개변수에는 fin으로부터 읽어 들인 바이트들을 문자로 인코딩하기 위한 문자 집합을 지정한다.
원도우에서 디폴트로 사용하는 문자 집합은 MS949 이다. 그러므로 앞의 코드에서 InputStreamReader 생성자에 MS949 문자 집합을 지정하였다.

파일 읽기

in.read()는 문자 집합의 인코딩 규칙에 따라, fin에게 파일로부터 필요한 바이트들을 읽도록 지시하고, 읽어 들인 바이트들을 MS949 문자 집합에 정의된 문자인지 찾아 한글 문자를 리턴한다. 만일 문자 집합에 없는 바이트들인 경우 정상적이지 않은 값을 리턴한다.

FileWriter를 이용한 텍스트 파일 쓰기 

파일 출력 스트림 생성 

<pre><code>
FileWriter fout = new FileWriter("c:\\Temp\\test.txt");
</pre></code>

FileWriter의 생성자는 c:\Temp\test.txt 파일을 열어 스트림과 연결한다. 파일이 없는 경우 빈 파일을 생성하며, 이미 파일이 있는 경우 파일이 있는 경우 파일 내용을 지우고 파일의 처음부터 쓸 준비를 한다.

파일 쓰기 

fout 스트림의 write() 메소드를 이용하면 문자 단위로 파일에 저장할 수 있다. 

<pre><code>
fout.write('A'); // 문자 'A'를 파일에 저장 
</pre></code>

write()를 이용하면 한 번에 한 블록씩 쓸 수 있다.

<pre><code>
char[] buf = new char[1024];
fout.write(buf,0,buf.length); // buf[] 배열의 처음부터 배열 크기(1024개 문자)만큼 쓰기
</pre></code>

스트림 닫기 

텍스트를 모두 파일에 저장하였으면 close()를 호출하여 스트림을 닫는다. 스트림을 닫으면 연결된 파일도 닫힌다.

<pre><code>
fout.close(); // 스트림을 닫는다. 더 이상 스트림에 기록할 수 없다.
</pre></code>

FileWriter와 OutputStreamWriter의 생성자

<pre><code>
OutputStreamWriter(OutputStream out) : out에 출력하는 기본 문자 집합의 OutputStreamWriter 생성
OutputStreamWriter(OutputStream out, Charset cs) : out에 출력하는 cs문자 집합의 OutputStreamWriter 생성
OutputStreamWriter(OutputStream out, String charsetName) : charsetName 문자 집합의 OutputStreamWriter 생성
FileWriter(File file) : file에 데이터를 저장할 FileWriter 생성
FileWriter(String name) : name 파일에 데이터를 저장할 FileWriter 생성
FileWriter (File file, boolean append) : FileWriter를 생성하며 append가 true이면 파일의 마지막부터 데이터를 저장
FileWriter(String name, boolean append) : FileWriter를 생성하며 append가 true이면 파일의 마지막부터 데이터를 저장 
</pre></code>

FileWriter와 OutputStreamWriter의 주요메소드

<pre><code>
void write(int c) : c를 char로 변환하여 한 개의 문자 출력
void write(String str) : 문자열 str 출력
void write(String str, int off, int len) : 인덱스 off부터 len개의 문자를 str 문자열에서 출력 
void write(char[] cbuf, int off, int len) : 인덱스 off부터 len개의 문자를 배열 cbuf에서 출력
void flush() : 스트림에 남아있는 데이터 모두 출력
String getEncoding() : 스트림이 사용하는 문자 집합의 이름 리턴 
void close() : 출력 스트림을 닫고 관련된 시스템 자원 해제 
</pre></code>

바이트 스트림 클래스 

바이트 스트림은 바이트 단위로 바이너리 데이터가 흐르는 스트림이다. 바이트 스트림은 바이너리 데이터를 있는 그대로 입출력하기 때문에 이미지나 동영상 파일 입출력에 필수적이고, 문자들로 구성된 텍스트 파일로 입출력할 수 있다.

InputStream/OutputStream

추상 클래스이며, 바이트 입출력 처리를 위한 공통 기능을 가진 슈퍼 클래스이다.

FileInputStream/FileOutputStream

파일 입출력을 위한 클래스로서, 파일로부터 바이너리 데이터를 읽거나 파일에 바이너리 데이터를 저장할 수 있다.

DataInputStream/DataOutputStream

이 스트림을 이용하면 boolean, char, byte, short, int, long, float, double 타입의 값을 바이너리 형태로 입출력한다. 문자열도 바이너리 형태로 입출력한다.

FileOutputStream을 이용한 바이너리 파일 쓰기 

프로그램 내의 변수나 배열에 들어 있는 바이너리 값을 그대로 저장해야 하는 경우가 있다. 메모리에 있는 이미지 비트들을 그대로 이미지 파일로 저장하는 경우이다. 바이너리 파일은 사람이 읽고 해석하는 것이 거의 불가능하다.

FileOutputStream 클래스의 생성자 

<pre><code>
FileOutputStream(Filefile) : file이 지정하는 파일에 출력하는 FileOutputStream생성 
FileOutputStream(String name) : name이 지정하는 파일에 출력하는 FileOutputStream생성
FileOutputstream(File file, boolean append) : FileOutputStream을 생성하며 append가 true이면 file이 지정하는 파일의 마지막부터 데이터 저장
FileOutputStream(String name, boolean append) : FileOutputStream을 생성하며 append가 true이면 name이름의 파일의 마지막부터 데이터 저장 
</pre></code>

OutputStream과 FileOutputStream의 공통 주요 메소드 

<pre><code>
void write(int b) : int형으로 넘겨진 한 바이트를 출력 스트림으로 출력
void write(byte[] b) : 배열 b의 바이트를 모두 출력 스트림으로 출력
void write(byte[] b, int off, int len) : len 크기만큼 off부터 배열 b를 출력 스트림으로 출력
void flush() : 출력 스트림에서 남아 있는 바이너리 데이터 모두 출력 
void close() : 출력 스트림을 닫고 관련된 시스템 자원 해제 
</pre></code>

파일 출력 스트림 생성

c:\Temp\test.out 파일에 바이너리 데이터를 저장하는 출력 스트림은 다음과 같이 생성한다.

<pre><code>
FileOutputStream fout = new FileOutStream("c:\\Temp\\test.out");
</pre></code>

FileOutputStream 생성자는 c:\\Temp\test.out 파일을 생성하여 연결한다. 파일이 이미 있으면 그 내용을 지우고 스트림에 연결한다. 쓰기가 이루어지면 c:\Temp\test.out 파일은 바이너리 파일이 된다.

파일 쓰기 

배열을 파일에 저장한다. write()메소드를 이용하여 다음과 같이 한 바이트씩 배열 데이터를 기록한다.

<pre><code>
byte b[] = { 7,51,3,4,-1,24};
for(int i = 0;i < b.length; i++) {
  fout.write(b[i]); // 배열 b[]의 바이트를 바이너리 그대로 파일에 저장 
}
</pre></code>

for 문 없이 한번에 배열 b[]를 저장할 수 있다.
<pre><code>
fout.write(b); // 배열 b[]의 바이트 모두 파일 저장
</pre></code>

FileInputStream을 이용한 바이너리 파일 읽기

바이트 스트림으로 파일을 읽는 스트림 클래스는 FileInputStream이다.

FileInputStram클래스의 생성자

<pre><code>
FileInputStream(File file) : file이 지정하는 파일로부터 읽는 FileInputStream 생성
FileInputStream(String name) : name이 지정하는 파일로부터 읽는 FileInputStream 생성
</pre></code>

InputStream과 FileInputStream의 공통 주요 메소드 

<pre><code>
int read() : 입력 스트림에서 한 바이트를 읽어 int형으로 리턴
int read(byte[] b) : 최대 배열 b의 크기만큼 바이트를 읽음. 읽는 도중 EOF를 만나면 실제 읽은 바이트 수 리턴
int read(byte[] b, int off, int len) : 최대 leng개의 바이트를 읽어 b배열의 off위치부터 저장, 읽는 도중 EOF를 만나면 실제 읽은 바이트 수 리턴
int available() : 입력 스트림에서 현재 읽을 수 있는 바이트 수 리턴
void close() : 입력 스트림을 닫고 관련된 시스템 자원 해제 
</pre></code>

파일 입력 스트림 생성 

FileInputStream 클래스는 파일과 연결한 바이트 스트림을 생성한다.

<pre><code>
FileInputStream fin = new FileInputStream("c:\\Temp\\test.out");
</pre></code>

파일 읽기
fin.read() 메소드를 호출하면 파일 스트림으로 부터 한 바이트를 읽어 리턴한다. read() 메소드를 이용하여 파일에 저장된 바이트들을 읽어 배열 byte b[]에 다시 채운다.

<pre><code>
byte b[] = new byte[6]; // 비어있는 배열 
int n = 0, c;
while((c = fin.read()) != -1) { // 파일 끝(EOF)까지 한 바이트씩 읽기
  b[n] = (byte)c; // 읽은 바이트를 배열에 저장 
  n++;
}
</pre></code>

<pre><code>
fin.read(b); // 파일에서 배열 b[]의 크기만큼 바이트 읽기
</pre></code>

스트림 닫기 

<pre><code>
fin.close(); // 스트림을 닫는다. 더이상 스트림으로부터 읽을 수 없다.
</pre></code>

버퍼(Buffer)

버퍼란 데이터를 일시적으로 저장하기 위한 메모리이다. 파일 출력 스트림이 파일에 쓸 데이터를 버퍼에 모아 두었다가, 한 번에 운영체제 API를 호출하여 파일에 쓰게 하면, 운영체제의 부담을 줄이고 장치를 구동하는 일이 줄어들게 되어 시스템의 속도나 효율이 올라가게 된다.

버퍼를 가지는 스트림을 버퍼 스트림(Buffered Stream)이라고 부른다.

버퍼 스트림 생성 및 활용

바이트 버퍼 스트림 클래스의 생성자

<pre><code>
BufferedInputStream(InputStream in) : in을 연결하는 디폴트 크기의 입력 버퍼 스트림 객체 생성
BufferedInputStream(InputStream in, int size) : in을 연결하는 size 크기의 입력 버퍼 스트림 객체 생성
BufferedOutputStream(OutputStream out) : out을 연결하는 디폴트 크기의 출력 버퍼 스트림 생성
BufferedOutputStream(OutputStream out, int size) : out을 연결하는 size 크기의 출력 버퍼 스트림 생성
</pre></code>

문자 버퍼 스트림 클래스의 생성자

<pre><code>
BufferedReader(Reader in) : in을 연결하는 디폴트 크기의 문자 입력 버퍼 스트림 생성
BufferedReader(Reader in, int sz) : in을 연결하는 sz 크기의 문자 입력 버퍼 스트림 생성
BufferedWriter(Writer out) : out을 연결하는 디폴트 크기의 문자 출력 버퍼 스트림 생성
BufferedWriter(Writer out, int sz) : out을 연결하는 sz 크기의 문자 출력 버퍼 스트림 생성 
</pre></code>

버퍼 출력 스트림 생성 

<pre><code>
BufferedOutputStream bout = new BufferedOutputStream(System.out, 20); // 20바이트 버퍼 
</pre></code>

스트림 출력 

<pre><code>
FileReader fin = new FileReader("c:\\windows\\system.ini");
int c;
while((c = fin.read()) != -1) { // 파일 끝을 만날 때까지 문자들을 하나씩 읽는다.
  bout.write((char)c); // 읽은 문자를 버퍼 출력 스트림에 쓴다. 출력 스트림과 연결된 화면에 출력된다.
}
</pre></code>

버퍼에 남아 있는 데이터 출력 

<pre><code>
bout.flush(); // bout 스트림의 버퍼에 있는 데이터를 모두 장치에 출력 
</pre></code>

스트림 닫기 

<pre><code>
bout.close(); // 버퍼 스트림 닫기
fin.close(); // 파일 입력 스트림 닫기
</pre></code>

File 클래스

File 클래스는 파일이나 디렉터리에 대해, 경로명, 크기, 타입, 수정 날짜 등의 속성 정보를 제공하고, 파일 삭제, 디렉터리 생성, 파일 이름 변경, 디렉터리 내의 파일 리스트 제공 등 다양한 파일 관리 작업을 지원한다.

File 객체 생성 

<pre><code>
File f = new File("c:\\temp\\test.txt");
File f = new File("c:\\temp","test.txt"); // 디렌터리와 파일명을 나누어 전달 
</pre></code>

File 클래스의 생성자 

<pre><code>
File(File parent, String child) : parent 디렉터리에 child 이름의 서브 디렉터리나 파일을 나타내는 File 객체 생성 
File(String pathname) : pathname의 완전 경로명이 나타내는 File 객체 생성 
File(String parent, String child) : parent 디렉터리에 child 이름의 서브 디렉터리나 파일을 나타내는 File객체 생성
File(URI uri) : file:URI를 추상 경로명으로 변환하여 File 객체 생성 
</pre></code>

File 클래스의 주요 메소드 

<pre><code>
boolean mkdir() : 새로운 디렉터리 생성
String[] list() : 디텍터리 내의 파일과 서브 디렉터리 리스트를 문자열 배열로 리턴
File[] listFiles() : 디렉터리 내의 파일과 서브 디렉터리 리스트를 File[] 배열로 리턴 
boolean renameTo(File dest) : dest가 지정하는 경로명으로 파일 이름 변경 
boolean delete() : 파일 또는 디렉터리 삭제
long length() : 파일의 크기 리턴
String getPath() : 경로명 전체를 문자열로 변환하여 리턴 
String getParent() : 파일이나 디렉터리의 부모 디렉터리 이름 리턴 
String getName() : 파일 또는 디렉터리 이름을 문자열로 리턴 
boolean isFile() : 일반 파일이면 true 리턴
boolean isDirectory() : 디렉터리이면 true 리턴
long lastModified() : 파일이 마지막으로 변경된 시간 리턴 
boolean exists() : 파일 또는 디렉터리가 존재하면 true 리턴 
</pre></code>

파일 크기, length()

length()는 파일이나 디렉터리의 크기를 리턴한다.

<pre><code>
File f = new File("c:\\windows\\system.ini"); // 파일 크기는 219바이트
long size = f.length(); // size = 219
</pre></code>

파일의 경로명, getName(), getPath(), getParent()

getName()은 파일명만, getPath()는 완전경로명을, getParent()는 부모 디렉터리를 문자열로 리턴한다.

<pre><code>
String filename = f.getName(); // "system.ini"
String path = f.getPath(); // "c:\\windows\\system.ini"
String parent = f.getParent(); // "c:\\windows"
</pre></code>

파일 타입 판별, isFile()과 isDirectory()

isFile()과 isDirectory()는 경로명이 파일인지 디렉터리인지에 따라 true/false를 리턴한다.

<pre><code>
if(f.isFile()) // 파일인 경우
  System.out.println(f.getPath() + "는 파일입니다.");
else if(f.isDirectory()) // 디렉터리인 경우
  System.out.println(f.getPath() + "는 디렉터리입니다.");
</pre></code>

디렉터리에 있는 파일 리스트 얻기, listFiles()

File 객체가 디렉터리의 경로명을 가진 경우, 디렉터리의 모든 파일과 서브디렉터리의 리스트를 얻을 수 있다. list()는 파일과 서브디렉터리 경로명을 문자열 배열(String[])로 리턴하는 반면, listFiles()는 파일과 서브디렉터리 경로명을 File[]배열로 리턴한다.

<pre><code>
File f = new File("c:\\Temp");
File[] subfiles = f.listFiles(); // c:\Temp 디렉터리의 파일 및 서브디렉터리 리스트 얻기
for(int i = 0; i < filenames.length; i++) {
    System.out.print(subfiles[i].getName()); // 파일명 출력
    System.out.println("\t파일 크기:" + subfiles[i].length()); // 파일 크기 출력 
}
</pre></code>

텍스트 파일 복사 

문자 스트림을 이용하여 텍스트 파일을 복사할 수 있다. FileReader를 이용하여 텍스트 파일을 읽고 FileWriter로 텍스트를 복사한다. 

바이너리 파일 복사 

바이트 스트림을 이용하여 바이너리 파일을 복사할 수 있다. 파일을 바이트 단위로 복사하므로 이미지, 동영상 실행파일(exe)과 같은 바이너리 파일뿐 아니라 텍스트 파일도 복사할 수 있다.

- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
