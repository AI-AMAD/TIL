---
title: "TCP vs UDP"
date: 2022-05-11
categories: [네트워크]
---
## TCP란?

TCP(Transmission Control Protocol)는 연결형, 신뢰성 전송 프로토콜이다. 연결지향적 서비스를 제공하기 위해 데이터를 전송하기 전에 3way handsaking을 하여 두 호스트의 전송 계층 사이에 논리적 연결을 설립한다. 신뢰성 있는 서비스를 제공하기 위해 오류제어, 흐름제어, 혼잡제어 등을 실행한다. 신뢰성을 보장하기 위해서 header가 더 크고 속도가 비교적 느리다는 단점이 있다.

-   **흐름제어**  
    데이터를 보내는 속도와 데이터를 받는 속도의 균형을 맞추는 것을 뜻한다.
    
-   **오류제어**  
    훼손된 segment의 감지 및 재전송, 손실된 segment의 재전송, 순서가 맞지 않게 도착한 segment를 정렬하고 중복 segment를 감지 및 폐기한다.
    

## UDP란?

UDP(User Datagram Protocol)는 비연결형 프로토콜로 3way handshake등의 세션 수립 과정이 없다.  
또한 비신뢰성 프로토콜로 흐름제어, 오류제어, 혼잡제어를 제공하지 않는다. 이러한 단순성 덕분에 적은 양의 오버헤드를 갖고 수신여부를 확인하지 않아서 속도가 빠르다는 장점이 있다.

**TCP는 신뢰성이 중요한 통신(HTTP, File전송 등)에 쓰이고, UDP는 실시간성이 중요한 통신(동영상 스트리밍등)에 주로 사용된다.**

> **3-way handshake란??**

3-way handshake는 TCP/IP 프로토콜로 통신하기 전 정확한 정보 전송을 위해 상대방 컴퓨터와 세션을 수립하는(연결) 과정을 말한다. (TCP연결 초기화)

클라이언트가 서버에게 접속을 요청하는 SYN패킷을 보내면, 서버는 요청을 수락하는 ACK를 포함하여 SYN+ACK 패킷을 클라이언트에게 발송한다. 클라이언트가 이것을 수신한 후, 다시 ACK를 서버에게 발송하면 연결이 이루어지고(여기까지의 과정이 3-way handshake이다), 이로써 데이터를 주고받을 수 있게된다.  
![](https://velog.velcdn.com/images/lkdfj6/post/074d9f80-91cd-4b3a-8fc0-eb8741fa26cb/image.png)

-   **SYN 이란?**  
    TCP에서 세션을 성립할 때 가장 먼저 보내는 패킷  
    시퀀스 번호를 임의적으로 설정하여 세션을 연결하는 데 사용되며 초기에 시퀀스 번호를 보내게 된다.

-   **ACK 란??**  
    상대방으로부터 패킷을 받았다는 걸 알려주는 패킷  
    받는 사람이 보낸 사람 시퀀스 번호에 TCP계층에서 길이 또는 데이터 양을 더한 것과 같은 ACK를 보낸다.

> **4-way handshake란?**

3-way handshake를 통해 연결을 했다면 tcp 연결을 종료하는 connection termination 과정은 4-way handshaking을 통해 이루어 진다.  
![](https://velog.velcdn.com/images/lkdfj6/post/c4e41542-2949-46da-9529-5659d8725e40/image.png)