---
layout: single
title: "TIL - Basic Web Architecture"
---

## **클라이언트, 서버 그리고 API**

### **클라이언트**

\- 클라이언트는 서비스를 사용하는 사용자, 혹은 사용자의 단말기로 해석할 수 있다. 웹브라우저에서는 웹서버로 접속하기 위한 터미널역할을 한다. 서버입장에서 보면 우리 유저 한명한명이 다 클라이언트로 불린다. 

 

------

### **서버**

\- 클라이언트는 요청을 한다면, 서버는 그 요청에 응답하는 관계다. 오늘날 인터넷과 연결된 거의 모든 소프트웨어들이 클라이언트 - 서버 관계를 가지고 있다. 서버는 클라이언트에게 네트워크를 통해 정보나 서비스를 제공하는 컴퓨터 시스템으로 컴퓨터 프로그램또는 장치를 의미한다.

-서버는 역할에 따라 다양하게 구분이 된다. 

- 웹서버 : 웹사이트를 관리하는 서버
- DNS 서버 : 도메인 관리 및 제공하는 서버
- 이메일 서버 : 이메일을 관리하는 서버
- 파일 서버 : 파일을 제공하고 관리하는 서버
- 프린터 서버 : 프린터를 제어하는 서버

\- 서버는 하나의 컴퓨터에서 웹서버 혹은 DNS 서버등 설치하고 클라이언트에게 제공하면서 상황에 따라 웹서버혹은 DNS서버가 된다.

 

[자료참조] 

[m.blog.naver.com/PostView.nhn?blogId=pst8627&logNo=221662613847&proxyReferer=https:%2F%2Fwww.google.com%2F](https://m.blog.naver.com/PostView.nhn?blogId=pst8627&logNo=221662613847&proxyReferer=https:%2F%2Fwww.google.com%2F)



------

### **API - Application Programming Interface(응용 프로그램 프로그래밍 인터페이스)**

\- API를 표현하자면 스타벅스에 들어가서 커피를 주문하려고 할때 우리가 보는 **메뉴판**이라고 볼수도 있다. 우리(클라이언트)는 그 메뉴판(API)을 통하여 커피를 주문하고 직원(서버)은 주문한 커피를 제대로 접수해서 우리에게 제공한다. 혹은 프로그램과 또 다른 프로그램을 연결해주는 **일종의 다리역할**도 한다**.** 

만약에 아래에 세가지등의 상황이 주어진다면?

- 자신의 웹서비스에서 사용자들로 하여금 결제가 가능하도록 만들 수 있을까?
- 지도를 이용한 웹서비스 길찾기 혹은 맛집 검색을 제작하고 싶다면 어떻게 할까?
- 일기예보 정보를 자신이 만든 웹페이지에 띄우려면 어떻게 해야할까?

\- 이같은 서비스를 만들기 위한 데이터도 관련프로그램도 없이 시작할때, 인터넷 상에서 제공하는 API를 통하여서 제작이 가능하다.자기가 만든 프로그램등이 개인 개발자, 기업, 기관이 제공하는 기능, 프로그램 등을 활용할 수 있게끔 도와주는 중간 매개체에 역할을 하는게 API다.

 



![img](https://blog.kakaocdn.net/dn/VRZBm/btqRv9SeUFw/iZsi6WEckMXh7KF2eWRUz0/img.png)



[사진제공] [www.8bitmen.com/](https://www.8bitmen.com/)

[ 8bitmen.com - Distributed Systems & ScalabilityDistributed Systems & Scalabilitywww.8bitmen.com](https://www.8bitmen.com/)

------

### **Browser, HTTP**

-**웹 브라우저** 또는 **브라우저**([영어](https://ko.wikipedia.org/wiki/영어): web browser 또는 browser, [문화어](https://ko.wikipedia.org/wiki/문화어): 열람기)는 [웹 서버](https://ko.wikipedia.org/wiki/웹_서버)에서 이동하며(navigate) 쌍방향으로 통신하고 [HTML](https://ko.wikipedia.org/wiki/HTML) 문서나 파일을 출력하는 [그래픽 사용자 인터페이스](https://ko.wikipedia.org/wiki/그래픽_사용자_인터페이스) 기반의 [응용 소프트웨어](https://ko.wikipedia.org/wiki/응용_소프트웨어)이다.

\- 우리가 아는 웹브라우저는 주로 [모질라 파이어폭스](https://ko.wikipedia.org/wiki/모질라_파이어폭스), [구글 크롬](https://ko.wikipedia.org/wiki/구글_크롬), [인터넷 익스플로러](https://ko.wikipedia.org/wiki/인터넷_익스플로러)/[마이크로소프트 엣지](https://ko.wikipedia.org/wiki/마이크로소프트_엣지), [오페라](https://ko.wikipedia.org/wiki/오페라_(웹_브라우저)), [사파리](https://ko.wikipedia.org/wiki/사파리_(웹_브라우저))가 있다.

\- 웹 브라우저는 [웹 페이지](https://ko.wikipedia.org/wiki/웹_페이지)를 가져오기 위해(웹 문서를 열기 위해) 대부분의 [웹 서버](https://ko.wikipedia.org/wiki/웹_서버)가 사용하는 [HTTP](https://ko.wikipedia.org/wiki/HTTP)(hyper-text transfer protocol)로 통신한다. HTTP를 이용해 웹 페이지를 가져올 뿐 아니라 웹 서버에 정보를 송신하기도 한다. 페이지들은 주소처럼 이용되는 [URL](https://ko.wikipedia.org/wiki/URL)(uniform resource locator)을 통해 장소가 정해지고, HTTP 접근을 위해 "http:"로 시작된다.

\- HTTP는 서버와 클라이언트가 주로 HTML등의 문서를 주고받는데 사용되는 프로토콜이다. 

\- HTTP는 한번 요청응답이 일어나면 끝이다. 연결상태가 유지 되지 않는다. 이전 요청이나 다음 요청을 기억하지 않는다

 

[자료참조] [ko.wikipedia.org/wiki/%EC%9B%B9_%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80](https://ko.wikipedia.org/wiki/웹_브라우저)





![img](https://blog.kakaocdn.net/dn/druK2p/btqRptLhe4X/LVHSQDLokOMwfllpPnHsOk/img.png)



------

### **AJAX**

Ajax는 JavaScript의 라이브러리중 하나이며 Asynchronous Javascript And Xml(비동기식 자바스크립트와 xml)의 약자이다. 브라우저가 가지고있는 XMLHttpRequest 객체를 이용해서 전체 페이지를 새로 고치지 않고도 페이지의 일부만을 위한 데이터를 로드하는 기법 이며 Ajax를 한마디로 정의하자면 JavaScript를 사용한 비동기 통신, 클라이언트와 서버간에 XML 데이터를 주고받는 기술이라고 할 수 있겠다.

 

[자료참조] [coding-factory.tistory.com/143](https://coding-factory.tistory.com/143)