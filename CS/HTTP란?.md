---
title: "HTTP란??"
date: 2022-05-11
categories: [CS]
---
## HTTP란??

HTTP는 HyperText Transfer Protocol의 약자로 서버-클라이언트 모델을 따르면서 request, response구조로 웹 상에서 정보를 주고받을 수 있는 프로토콜을 말한다. TCP/IP기반으로 작동하며, HTTP의 가장 큰 특징은 connectionless와 stateless 이다.

클라이언트가 HTTP request를 서버에 보내면  
서버는 HTTP response를 클라이언트에 보내는 구조이다.

-   **request message**  
    `start line`(method, path, HTTP version), `headers`, `body`로 이루어져있다.  
    ![](https://velog.velcdn.com/images/lkdfj6/post/1972bcd3-f6e3-41d3-a2f7-cfeef21c4ead/image.png)

-   **response message**  
    `status line`(HTTP version, status code, status message), `headers`, `body`로 이루어져있다.  
    ![](https://velog.velcdn.com/images/lkdfj6/post/37f8dd74-4c29-47fc-b388-68233e1fde83/image.png)

> **connectionless란??**

클라이언트와 서버가 한번 연결을 맺은 후, 클라이언트 요청에 대해 서버가 응답을 마치면 맺었던 연결을 끊어 버리는 성질을 말한다.

-   **connectionless의 장점**  
    HTTP는 인터넷 상에서 불특정 다수의 통신 환경을 기반으로 설계되었다.  
    따라서 서버에서 다수의 클라이언트와 연결을 계속 유지해야 한다면, 이에 따른 많은 리소스가 발생하게 되므로 이 리소스 증가를 막기위해 비연결적인 특징을 갖는다.
    
-   **connectionless의 단점**  
    서버는 클라이언트를 기억하고 있지 않으므로 동일한 클라이언트의 모든 요청에 대해, 매번 새로운 연결을 시도/해체의 과정을 거쳐야 하므로 이에 대한 오버헤드가 발생한다.
    

> **stateless란??**

말그대로 상태를 보존하지 않는 것을 의미한다.  
일상생활속 대화를 예로 설명할 수 있다.

-   **stateful**

```
승객: 서울에서 전주 가는 KTX는 얼마인가요?
직원: 25,000원입니다.

승객: 2장 주세요.
직원: 50,000원입니다. 결제는 무엇으로 하시겠습니까? (KTX 노선과 주문 수량에 대한 상태를 유지)

승객: 체크카드입니다.
직원: 결제과 완료되었습니다. (KTX 노선과 주문 수량, 결제 수단에 대한 상태를 유지)
```

-   **stateless**

```
승객: 서울에서 전주 가는 KTX는 얼마인가요?
직원: 25,000원입니다.

승객: 2장 주세요.
직원: ??? 무엇을 2장 구매하시는 건가요???

승객: 아까 말했잖아요😳. 서울에서 전주 가는 KTX요!!!
직원: 몇 장인지, 결제 수단은 무엇인지 한 번에 얘기해주세요!
```

stateful은 우리의 일상 대화와 비슷하다. 대화를 주고 받을 때 마다(요청과 응답) 상대는 문맥의 상태를 유지한다. 하여 전에 했던말을 또 반복해서 하지 않아도 상대는 기억하고 대화가 가능하다.

하지만, stateless에서는 대화가 오고 갈 때 마다 상대는 그 문맥의 상태를 모른체 대화를 한다고 보면된다. 따라서 한꺼번에 모든것을 이야기 해야하야 한다.

```
승객: 서울에서 전주가는 KTX 2장 체크카드로 결제할게요!
```

-   **stateless의 장점**

stateful의 경우에는 상태를 유지해야 하므로 항상 같은 서버가 유지 되어야 한다. 하지만 stateless는 상태를 보관하지 않으므로 클라이언트의 요청에 어느 서버가 응답해도 상관이 없다. 따라서 클라이언트의 요청이 대폭 증가해도 서버를 증설해 해결할 수 있다.

-   **stateless의 단점**  
    사용자의 상태를 유지 시키지 못한다면 매번 로그인 같은 인증과정을 거쳐야 하므로 번거로워진다. 이를 해결하기 위해 쿠키, 세션등을 사용한다.

  

## GET & POST method

> **GET method**

-   정보를 조회하기 위한 메서드
-   서버에서 어떤 데이터를 가져와서 보여주기 위한 용도의 메서드
-   가져오는 것(`Select`)
-   url 끝에 '?'가 붙고, 요청정보가 (key=value)형태의 쌍을 이루어 ?뒤에 이어서 붙어 서버로 전송한다.
-   요청 정보가 여러개 일 경우 '&'로 구분한다.

**특징**

-   url에 요청 정보를 붙여서 전송한다.
-   url에 요청 정보가 이어 붙기 때문에 길이 제한이 있어서 대용량의 데이터를 전송하기 어렵다.
-   요청 정보를 사용자가 쉽게 눈으로 확인 가능하여 보안에 취약하다.
-   HTTP패킷의 body는 비어 있는 상태로 전송한다.

> **POST method**

-   서버의 값이나 상태를 바꾸기 위한 용도의 메서드
-   수행하는 것(`Insert`, `Update`, `Delete`)
-   요청 정보를 body안에 담아서 전송하기 때문에 대용량의 데이터를 전송하기에 적합하다.
-   body안에 담아서 정보를 전송하기 때문에 아무래도 GET방식 보다는 보안에 안전하다. (하지만 완벽한 보안은 아니다)

### GET, POST method의 부수적 차이점

GET방식의 요청은 브라우저에서 caching 할 수 있다. 때문에 POST방식으로 요청해야 할 것을 보내는 데이터의 크기가 작고 보안적인 문제가 없다는 이유로 GET방식으로 요청한다면 기존에 caching 되었던 데이터가 응답될 가능성이 존재한다.  
그러므로 목적에 맞는 기술을 사용해야 한다.

> **PUT & PATCH method**

-   **PUT**  
    모든 리소스를 수정, 대체한다.
    
-   **PATCH**  
    일부 리소스만 수정한다.
    

  

## HTTP status code

HTTP status code는 클라이언트가 보낸 HTTP 요청에 대한 서버의 응답 코드로, 상태 코드를 통해 요청의 성공/실패 여부를 판단할 수 있다. 100번대부터 500번대까지 총 5개의 클래스로 구분되어 HTTP 요청에 대한 상태를 알려준다.

-   `1xx(정보)`: 요청을 받았으며 작업을 계속한다.
    
-   `2xx(성공)`: 클라이언트가 요청한 동작을 성공적으로 수신하여 이해했고 성공적으로 처리하였다.
    
-   `3xx(리다이렉션)`: 요청을 완료하기 위해 추가 작업 조치가 필요하다.
    
-   `4xx(클라이언트 오류)`: 클라이언트의 요청에 문제가 있다.
    
-   `5xx(서버 오류)`: 서버가 유효한 요청의 수행을 실패했다.
    

> **자주 사용하는 status code**

![](https://velog.velcdn.com/images/lkdfj6/post/a9169aba-a669-4083-971a-f6cf4f6641d5/image.png)

> **www.google.com을 주소창에 쳤을때 일어나는 과정 (네트워크 관점)**

1.  사용자가 브라우저에 URL 입력하면 HTTP request message를 생성
    
2.  브라우저는 DNS를 통해 서버의 IP주소를 찾는다.
    
3.  반환된 IP주소(구글의 server IP)로 HTTP request message 전송 요청  
    i. 생성된 HTTP request message를 TCP/IP층에 전달  
    ii. HTTP request message에 header를 추가해서 TCP/IP패킷을 생성
    
4.  해당 패킷은 전기신호로 랜선을 통해 네트워크로 전송되고, 목적지 IP에 도달
    
5.  구글 server에 도착한 패킷은 unpacking을 통해 message를 복원하고 server의 process로 보낸다.
    
6.  server의 process는 HTTP request message에 대한 response data를 가지고 HTTP response message를 생성한다.
    
7.  HTTP response message를 전달 받은 방식 그대로 client IP로 전송
    
8.  HTTP response message에 담긴 데이터를 토대로 웹브라우저에서 HTML 렌더링을 하여 모니터에 검색창이 보여진다.