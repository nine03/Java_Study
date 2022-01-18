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








- 这个项目是我为了重新学习Java而做的项目（이 프로젝트는 내가 Java를 다시 공부하기위해서 만든 프로젝트입니다.）