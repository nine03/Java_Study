TCP/IP 프로토콜

TCP 프로토콜 Transmission Control Protocol의 약자로 다른 두 시스템 간에 신뢰성 있는 데이터의 전송을 관장하는 통신 프로토콜로서 IP(Internet Protocol) 프로토콜 위에서 동작한다.

![image](https://user-images.githubusercontent.com/60682087/149972607-66460ddf-1ade-460b-88b2-faa86eaafe70.png)

IP 주소 

IP 주소는 네트워크상에서 유일하게 식별될 수 있는 네트워크 장치의 주소로서 예를 들면 192.156.11.15와 같이 4개의 숫자가 "."으로 연결된다. 하나의 숫자 범위는 0 ~ 255 로서 한 바이트로 표현이 가능하다. 

내 컴퓨터의 IP주소 확인하기 

원도우 PC에서 명령창을 열어 ipconfig 명령을 수행하면 컴퓨터의 IP 주소를 확일할 수 있다.

IP 주소만 가지고는 통신하고자 하는 응용프로그램을 식별할 수 없다. 이를 위해 한 컴퓨터 내의 각 응용프로그램은 통신을 위해 가상의 연결단인 포트(port)를 생성하고 이 포트 번호로 상대방이 자신을 식별하게 한다.

![캡처](https://user-images.githubusercontent.com/60682087/149973452-b472201f-6a03-44ab-a704-46b101f9e054.JPG)

소켓(socket)

소켓통신은 개발자가 TCP/IP 네트워크를 이용하여 쉽게 통신 프로그램을 작성하도록 지원하는 기반 기술이다. 여기서 소켓은 통신하는 두 응용프로그램 간의 통신 링크의 각 끝단(endpoint)으로서, TCP/IP의 네트워크 기능을 활용하여 다른 컴퓨터의 소켓과 데이터를 주고받는다.

![캡처2](https://user-images.githubusercontent.com/60682087/149973873-761523bb-1cb5-4206-8026-c2936c888cd2.JPG)

소켓과 서버 클라이언트 통신

소켓을 이용하는 통신에서는 반드시 서버 응용프로그램과 클라이언트 응용프로그램으로 구분된다. 정보를 제공하는 쪽을 서버(server)라고 부르며, 정보를 이용하는 쪽을 클라이언트(client)라고 부른다. 통신은 서버가 먼저 클라이언트의 접속을 기다리고, 클라이언트에서 서버에 접속하면, 그 때부터 서버나 클라이언트가 데이터를 서로 주고받을 수 있다. 서버나 클라이언트가 보내는 순서를 정하거나 순서에 상관없이 데이터를 전송하는 것은 개발자가 프로그램을 작성하기에 달려있다.

서버 소켓과 클라이언트 소켓

소켓에는 서버 소켓과 클라이언트 소켓의 2가지 종류가 있다.

서버 소켓은 서버 응용프로그램이 사용자의 접속을 기다리는(listen) 목적으로만 사용된다. <br>
클라이언트 응요프로그램에서는 클라이언트 소켓을 이용하여 서버에 접속한다. <br>
서버 소켓은 클라이언트가 접속해오면, 클라이언트 소켓을 추가로 만들어 상대 클라이언트와 통신하게 한다. <br>

서버에서 클라이언트 소켓들의 포트 공유 

소켓을 이용한 서버 클라이언트 통신 프로그램 구성 

1. 서버 응용프로램은 SeverSocket 클래스를 이용하여 서버 소켓 객체를 생성하고 클라이언트의 접속을 받기 위해 기다린다. 서버 소켓을 생성할 때 포트 번호를 주어 해당 포트로 접속해 오는 클라이언트 가다리게 한다. <br>
2. 클라이언트 응용프로그램은 Socket 클래스를 이용하여 클라이언트 소켓 객체를 생성하고 서버에 접속을 시도한다. 소켓 객체를 생성할때, 접속할 서버 소켓의 IP 주소와 포트 번호를 지정한다. <br>
3. 서버는 클라이언트로부터 접속 요청을 받으면, accept() 메소드에서 접속된 클라이언트와 통신하도록 전용 클라이언트 소켓을 따로 생성한다. <br>
4. 서버와 클라이언트 모두 소켓으로부터 입출력 스트림을 얻어내고 데이터를 주고 받을 준비를 한다. <br>
5. 서버에 생성된 클라이언트 전용 소켓과 클라이언트의 소켓이 상호 연결된 채 스트림을 이용하여 양방향으로 데이터를 주고받는다. <br>
6. 서버는 클라이언트가 접속해 올 때마다 accept() 메소드에서 따로 전용 클라이언트 소켓을 생성하여 클라이언트와 통신하도록 한다. 통신이 끝나면 소켓을 닫는다. <br>

![image](https://user-images.githubusercontent.com/60682087/149975926-9e2dbbce-4c7b-4d56-911e-2d384d273c70.png)
 
Socket 클래스, 클라이언트 소켓 

Socket은 java.net 패키지에 포함되어 있는 클래스로서 클라이언트 소켓을 구현한다.

클라이언트 소켓 생성 및 서버 접속

```
Socket clientSocket = new Socket("128.12.1.1",5550); // 128.12.1.1 서버에 접속
```

```
Socket clientSocket = new Socket(); // 연결되지 않는 소켓생성 
clientSocket.bind(new InetSocketAddress("192.168.1.21",1234)); // 소켓에 자신의 IP 주소(192.168.1.21)와 로컬 포트(1234)룰 결합한다.\
clientSocket.connect(new InetSocketAddress("128.12.1.1",5550)); // IP 주소가 128.12.1.1이고 포토가 5550인 서버 응용프로그램에 접속
```

네트워크 입출력 스트림 생성

소켓이 만들어지고 서버와 연결이 된 후에는 Socket 클래스의 getInputStream()과 getOutputStream() 메소드를 이용하여 서버와 데이터를 주고받을 주고받을 소켓 스트림을 얻어내고 이를 버퍼스트림에 연결한다.

```
BufferedReader in = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()));
BufferedReader out = new BufferedWriter(new OutputStreamWriter(clientSocket.getOutputStream()));
```

지금부터 in,out 스트림 객체를 이용하여 네트워크 데이터를 보내고 받으면 된다. 이코드에서 만들어진 in, out은 문자만 보내고 받을 수 있는 문자 입출력 스트림이다.

서버로 데이터 전송

```
out.write("hello" + "\n");
out.flush();
```

스트림 out은 버퍼 입출력 스트림이므로 버퍼가 차기 전까지 데이터를 보내지 않기 떄문에 강제로 out.flush()를 호출하여 스트림 속의 데이터를 모두 즉각 전송한다.

서버로부터 데이터 수신 

```
int x = in.read(); // 클라이언트로부터 한 개의 문자 수신
```

한 행의 문자열을 입력 받는 코드는 다음과 같다.

```
String line = in.readLine(); // 클라이언트로부터 한 행의 문자열 수신
```

in.readLine() 메소드는 '\n' 문자가 올 때까지 계속 일고 '\n'이 도착하면 그때까지 읽은 문자열을 리턴한다. 이 문자열 속에는 '\n'이 삽입되지 않는다.

데이터 송수신 종료 

```
socket.close();
```

Socket 클래스 생성자

![image](https://user-images.githubusercontent.com/60682087/149978502-fc3aa408-d08b-43de-901a-35423b37140d.png) 

Socket 클래스 주요 메소드

![image](https://user-images.githubusercontent.com/60682087/149978527-fa8edb40-bc05-4309-ab8b-1cab66ee05ab.png) 

ServerSocket 클래스, 서버 소켓

ServerSocket 클래스는 서버 소켓을 구현한다. ServerSocket 클래스는 java.net 패키지에 포함되어 있으며 ServerSocket 클래스의 생성자와 메소드는 같다. ServerSocket은 클라이언트로부터 연결 요청을 기다리는 목적으로 만 사용되며, 서버가 클라이언트의 연결 요청을 수락하면 Socket 객체를 별도로 생성하고, 이 Socket 객체가 클라이언트와 데이터를 주고 받는다. ServerSocket은 데이터의 송수신에 사용되지 않는다.

서버 소켓 생성

```
ServerSocket listener = new ServerSocket(9999);
```

클라이언트로부터 접속 대기

SeverSocket 클래스의 accept() 메소드를 이용하여 클라이언트로부터의 연결 요청을 기다린다. accept() 메소드가 연결을 수락하면 다음과 같이 Socket 객체를 하나 별도로 생성하여 리턴한다.

```
Socket socket = listener.accept();
```

네트워크 입출력 스트림 

클라이언트로 데이터를 주고 받기 위한 스트림 객체는, ServerSocket의 accept() 메소드로부터 얻은 socket 객체의 getInputStream()과 getOutputStream() 메소드를 이용하여 얻어낸다.

```
BufferedReader in = new BufferedReader(new InputStreamReader(Socket.getInputStream()));
BufferedReader out = new BufferedWriter(new OutputStreamWriter(Socket.getOutputStream()));
```

버퍼 입출력 스트림 in, out을 이용하여 클라이언트와 데이터를 주고받으면 된다. in, out은 모두 문자만 입출력하는 스트림이다.

클라이언트로부터 데이터 수신 

앞서 만들어진 버퍼 스트림 in을 이용하여 클라이언트로부터 문자 데이터를 수신할 수 있다.

```
int x = in.read(); // 클라이언트로부터 한 개의 문자 수신
```

한 행의 문자열을 입력받는 코드는 다음과 같다.

```
String line = in.readLine(); // 클라이언트로부터 한 행의 문자열 수신
```

in.readLine() 메소드는 '\n' 문자가 올 때까지 계속 일고 '\n'이 도착하면 그때까지 읽은 문자열은 리턴한다. 이문자열 속에는 '\n'이 삽입되지 않는다. 현재 서버에서 라인 단위로 읽이 때문에 클라이언트에서는 송신하는 데이터의 끝에 '\n' 을 덧붙여 보내야 한다.

클라이언트로 데이터 전송 

```
out.write("Hi, elient" + "\n");
out.flush();
```

"\n"을 덧붙여 보내는 이유는 클라이언트 쪽에서 라인 단위('\n' 문자가 올 때까지 한 번에 읽는)로 수신한다고 가정하였기 때문이다. out.flush()를 호출하면 버퍼 스트림 속의 데이터를 모두 즉각 클라이언트로 전송한다.

데이터 송수신 종료

```
soket.close();
```

서버 응용프로그램 종료 

더 이상 클라이언트의 접속을 받지 않고 서버 응용프로그램을 종료하고자 하는 경우 다음과 같이 ServerSocket을 종료시킨다.

```
serverSocket.close();
```

serverSocket 클래스의 주요 생성자

![image](https://user-images.githubusercontent.com/60682087/149981499-a43542b6-aaf1-4470-b90e-93af7f923519.png)

serverSocket 클래스의 주요 메소드 

![image](https://user-images.githubusercontent.com/60682087/149981555-1c1a3d17-d336-48e6-85a8-b036497e9538.png)

![캡처3](https://user-images.githubusercontent.com/60682087/149981761-a9915a88-16e3-4c41-abc7-f0c16baf1ac6.JPG)

![캡처4](https://user-images.githubusercontent.com/60682087/149981933-8c91e904-dcb0-49d8-8499-25d4f765d8c2.JPG)

- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）
