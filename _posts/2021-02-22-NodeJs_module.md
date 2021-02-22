---
layout: single
title: "Node JS 모듈 / 동기와 비동기 방식"
author: "김재우"
---

#### **동기(synchronous - 동시에 일어난다)**

 \- 동기 자체는 동시에 일어난다는 뜻으로 해석한다.

요청된것과 그 결과를 동시에 수행한다는 약속이다. 요청을 했을 때에 시간이 어느정도 주어지든 요청된 자리에서 그 결과가 주어져야 한다.

 



![img](https://blog.kakaocdn.net/dn/diCjMJ/btqQLlntiDv/7zUQyIY9qDdyX9NMUxXBY1/img.png)



 

 

#### **비동기(Asynchronous : 동시에 일어나지 않는다)**

 \- 비동기는 동시에 일어나지 않는다. 요청과 결과가 동시에 일어나지 않을거라는 약속을 하기 때문이다. 



![img](https://blog.kakaocdn.net/dn/dfaXb6/btqQ1M4mzGy/vDKgNd6uzY782EnOw9qG9k/img.png)



 

 

[사진출처]

[codeameba.netlify.app/blog/why-using-async](https://codeameba.netlify.app/blog/why-using-async)

 

 자바스크립트에서는 **싱글쓰레드 방식으로 동작하기 때문에 한 번에 한 가지 일만 수행할 수 있다.**

이러한 자바스크립트의 본성 탓에 비동기적인 프로그래밍이 필요하다고 할 수 있다. 

 

 

**비동기식과 동기식의 대해 공부하며 참조한 곳**

[webclub.tistory.com/605](https://webclub.tistory.com/605)

[blog.bitsrc.io/understanding-asynchronous-javascript-the-event-loop-74cd408419ff](https://blog.bitsrc.io/understanding-asynchronous-javascript-the-event-loop-74cd408419ff)[codeameba.netlify.app/blog/why-using-async](https://codeameba.netlify.app/blog/why-using-async)

 

------

## **Node JS module**

**Module은 Node JS로 개발한 \**Application을 이루는 기본 조각\**이라고 할 수 있다.**

우리가 흔히 물건을 만들 때에 그것을 구성하는 부품과도 같다. 마치 조립식처럼 부품의 파트 하나하나가 모여서 만들어 지는거와 같다. 미리 코드에서도 이와같이 미리 만들어진 코드들을 하나하나 붙여서 완성하듯, 관련된 코드들을 모아서 캡슐화해놓은 것을 모듈이라고 한다. 그리고 여러 가지 모듈을 이용하면서 프로젝트를 훨씬 더 수월하게 진행할 수 있게 된다.

 

 

아래에 링크를 통하여서 Node JS 공식문서에 안내되어 있는대로 작성하면 된다.

[nodejs.org/en/docs/](https://nodejs.org/en/docs/)