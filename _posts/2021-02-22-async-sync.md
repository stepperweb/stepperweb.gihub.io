---
layout: single
title: "JS에서 Object(객체)를 생성하는 여러가지 방법들"
author: "김재우"
---

## 비동기**(Asynchronous)**와 동기***\*(Synchronous)\****

JavaScript는 엔진은 **Single Thread**이다. 그래서 동시에 두 가지 작업을 할 수 없다.

그렇다면 여러 작업이 동시에 요청이 될 때 이 전 작업이 마무리 될 때까지 기다려야 하는가? 그렇다.

 

그래서 **JavaScript 엔진은 비동기 처리**가 가능하도록 설계되어있다.

 

**동기적\**(Synchronous)\** 처리**는 작업을 요청함과 동시에 작업의 결과를 그 자리에서 받을 수 있는 데이터 처리 방식이다.

그 반대로 **비동기적\**(Asynchronous)\** 처리**는 작업을 요청하지만 결과는 그 자리에서 꼭 받지 않아도 되는 데이터 처리 방식이다.

 



![img](https://blog.kakaocdn.net/dn/d6nJoD/btqRqbYNvDo/3RBpI0OSir1QbmxtcvMbB1/img.png)



[사진출처] [www.haninsociety.com/index.php?mid=blogO&page=612&document_srl=322098](http://www.haninsociety.com/index.php?mid=blogO&page=612&document_srl=322098)

[자료참조][developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/async_function](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/async_function)

 

### **비동기 처리 후엔 ?**

비동기적 실행이라고 하지만 요청을 할 때 이야기이고, 요청이 실행되거나 요청에 대한 응답이 돌아왔을 때는 또 다시 순차적으로 명령이 수행되어야 한다.

 

예를 들어 유튜브에서 '먹방'이라고 검색하여 검색 결과를 받아오는 것은 비동기적으로 실행되어야 하지만 검색어 '먹방'으로 인해 도착한 검색 결과들을 다시 사용자에게 원하는 대로 가공해서 보여주기 위해서는 비동기 실행이 끝난 "후"에 그 결과를 가지고(여기가 매우 중요) 코드를 작성해 원하는 결과를 시각화 할 수 있다.


이치적으로는 그러하나 일단 비동기로 발현한 것을 잡아와 다시 동기적 순서에 맞춰 가공하는 것이 쉽지는 않았을 것이다. 이를 보완하고자 아래와 같은 방법(callback → Promise객체 → Async/Await)들이 발전해 왔다.

 

 

## JS에서 비동기 실행을 구현할 수 있는 3가지 방법

- callback 이용
  1. 본디 callback 함수란 다른 함수에게 인자로 전달되어 어느 시점에 실행될 수 있도록 던져주는 함수이다. 따라서 callback을 통해 함수의 순서를 구현할 수 있다.
  2. call back 함수를 이용해 비동기적으로 1,2,3,4,5 로그 찍기
  3. 아래 코드에서 볼 수 있듯이 비동기 처리 구현은 가능하나 "콜백 지옥"이라는 것이 형성되었고, 가독성 또한 떨어지는 구조이다.

```
function delay(callback) {
  setTimeout(callback, 1000);
}

let arr = [];

delay(() => {
  console.log(1)
  arr.push(1);
  delay(() => {
    console.log(2)
    arr.push(2);
    delay(() => {
      console.log(3)
      arr.push(3);
      delay(() => {
        console.log(4)
        arr.push(4);
        delay(() => {
          console.log(5)
          arr.push(5);
          delay(() => {
            console.log(arr);
          })
        })
      })
    })
  })
})
// 1
// 1초 뒤 2
// 1초 뒤 3
// 1초 뒤 4
// 1초 뒤 5
// 1초 뒤 마지막으로 [1,2,3,4,5] 로그가 찍힘
```

 

------

Promise 객체

1. Promise는 어떤 값이 생성 되었을 때 그 값을 대신하는 대리자이다. 비동기 연산이 종료된 이후에 그 결과 값이나 에러를 처리할 수 있도록 처리기를 연결하는 역할을 하는 객체이다. 결과 값이나 에러 처리는 바로 알 수 없고, 프로미스라는 객체에 남겨 두었다가 그 다음 어떤 시점에서 결과를 사용할 수 있도록 한다. 
2. callback 함수와 달리 Promise 객체는 비동기적으로 처리할 수 있지만 코드를 볼 때는 상 → 하의 흐름으로 읽을 수 있어 가독성이 더 좋다. 또 비동기에 대한 에러 처리 또한 할 수 있다.
3. Promise를 이용해 비동기적으로 1,2,3,4,5 로그 찍기
4. Promise instance에 어떠한 값(성공했을 때는 성공 값-resolve, 그렇지 않았을 때는 에러 값-reject)을 담아 두었다가 .then이라는 method를 사용해서 비동기 처리 후 진행되어야 하는 순서를 구분해준다 프로미스 인스턴스에 담겨 있던 어떠한 값은 then 뒷 부분의 전달 인자로 주어진다.

```
        function deplayP(n) {
          return new Promise((resolve, reject) => {
            setTimeout(() => {
              resolve(n);
            }, 1000);
          });
        }
        
        delayP(1).then(result => {
          console.log(result);
          return delayP(2);
        }).then(result => {
          console.log(result);
          return delayP(3);
        }).then(result => {
          console.log(result);
          return delayP(4);
        }).then(result => {
          console.log(result)
          return delayP(5);
        }).then(result => {
          console.log(result)
        })
        //1부터 1초씩 지나면서 1, 2, 3, 4, 5가 로그에 찍힌다.
```

 

------

Async - Await

1. Async - Await은 비동기 코드를 동기식으로 표현하는 더 나은 방법으로 ES2017에 등장하였다. 그 사이에도 Promise의 장황한 구조를 대체하기 위해 ES2016 generator 등의 노력이 있었다고 한다. 그 결과 더 명료한 함수 표현이 가능해졌다.
2. Async는 await과 항상 함께 한다. Await 모드는 Promise 객체를 받아 처리하고, 만약 비동기 함수가 아닌 동기적 함수라면 리턴 값을 그대로 받는다.
3. Async 함수는 Promise가 없으면 의미가 없다. Promise 객체를 통해 비동기적으로 처리된 내용을 동기적인 코드 진행 순서로 보여주는 역할을 하기 때문이다.
4. Async 함수를 이용해 비동기적으로 1,2,3,4,5 로그 찍기
5. 이번에는 for loop로 돌려봤다. 별 다른 차이는 없고 for loop 안에 await 부분이 중요하다. 프로미스 객체를 리턴하는 delayP 함수의 값을 await 모드로 받은 것이 result 이다. result에 값이 담기기 전에는 그 다음 console.log 부분은 진행되지 않는다.(비동기 제어)

```
       function delayP(n) {
          return new Promise((resolve, reject) => {
            setTimeout(() => {
              resolve(n);
            }, 1000);
          });
        }
        async function myAsync() {
          for(let n = 1; n < 6; n++) {
            let result = await delayP(n);
            console.log(result);
          }
        };
        myAsync();
        //1부터 1초씩 지나면서 1, 2, 3, 4, 5가 로그에 찍힌다.
```