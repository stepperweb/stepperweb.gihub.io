---
layout: single
title: "JS에서 Object(객체)를 생성하는 여러가지 방법들"
author: "김재우"
---

## 1. Functional instantiation 

#### 함수를 이용하여 인스턴트 객체를 생성하기

```
var Car = function() {
    var someInstance = {};
    someInstance.position = 0;
    someInstance.move = function() {
        this.position += 1;
    }
    return someInstance;
};

var car1 = Car();
var car2 = Car();
car1.move();
```

 

단점 : 함수 안에 메서드가 정의되어 있기 때문에 인스턴스(객체)를 생성할 때마다, 인스턴스에게 메서드를 할당하므로 인스턴스 메서드의 개수만큼 컴퓨터 메모리를 차지한다. 그래서 메모리 낭비가 심하다.

 

\1. 함수 생성 : 함수 이름은 대문자로 시작(일반 함수와 구분하기 위함)

\2. 빈 객체 생성 : 함수를 이용해 만든 객체(인스턴스)

\3. 빈 객체에 프로퍼티 및 메서드 추가

\4. 빈 객체 반환 : 인스턴스 반환

 

## 2. Functional Shared instantiation 

**Functional 방법의 단점을 보완할 수 있다. 바로 인스턴스의 메서드를 함수 밖에 서 정의 및 할당한다.**

**그리고 인스턴스의 메서드를 공유하기 위해서 따로 외부 함수 extend를 만든다.** **그러면 메서드의 메모리 주소만을**

**참조해서 메모리 효율에 좋다.**

```
var extend = function(to, from) {
    for(var key in from) {
        to[key] = from[key];
    }
}

var someMethods = {};
someMethods.move = function() {
    this.position += 1;
}

var Car = function(position) {
    var someInstance = {
        position: position,
    };
    extend(someInstance, someMethods);
    return someInstance;
};

var car1 = Car(5);
var car2 = Car(10);
```

 

1 . 함수 생성 : 함수 이름은 대문자로 시작(일반 함수와 구분하기 위함)

\2. 함수 안에 빈 객체 생성 : 인스턴스

\3. 빈 객체에 프로퍼티만 추가 : 빈 객체 안에서 프로퍼티 추가도 가능(결국 같음)

\4. 함수 밖에 메서드 추가 : 인스턴스의 메서드 

\5. 함수 안의 인스턴스(프로퍼티만 있는)와 함수 밖의 메서드 연결하기 : 외부 함수 extend 만들기

5 - 1. 외부 함수 extend의 첫 번째 인자는 인스턴스 객체, 두 번째 인자는 메서드 객체

5 - 2 . for... in 이용하여 메서드 객체 있는 key와 value를 인스턴스 객체에 추가.

\6. 빈 객체 반환 : 인스턴스 객체

 

장점 : 메서드 객체의 주소 값이 인스턴스 객체와 연결되어 있다. 메모리 효율에 좋다.

단점 : 메서드 객체 수정하고 인스턴스 객체를 생성하면 기존의 인스턴스의 메서드 객체의 주소와 수정한 인스턴스의 메서드 객체의 주소는 다르다. 

 

 

## 3. Prototypal instantiation

**프로토타입 체인을 이용하여 인스턴스 객체 생성하기**

**Object.create() 메서드를 이용해서 인스턴스 객체의 부모 객체에 메서드 정의 및 할당한다**

```
var someMethods = {};
someMethods.move = function() {
    this.position += 1;
}

var Car = function(position) {
    var someInstance = Object.create(someMethods);
    someInstance.position = position;
    return someInstance;
};

var car1 = Car(5);
var car2 = Car(10);
```

 

\1. 함수 생성 : 함수 이름은 대문자로 시작(일반 함수와 구분하기 위함)

\2. 인스턴스 객체 정의 하기 : Object.create() 메서드를 이용해서 메서드 객체를 할당하는 객체 생성.

\3. Functional Shared Instantiation처럼 인스턴스의 메서드는 함수 밖에서 정의 및 할당/ 프로퍼티는 함수 안에서 추가

\4. 인스턴스 객체 반환

 

## 4. Pseudoclassical instantiation

**인스턴스 객체 생성 시, new 키워드 사용하며, this를 사용한다.**

**함수는 그냥 인스턴스 객체를 만들기 위한 틀이라고 생각하자! 함수 생성 시, 프로토타입 객체도 동시에 생성된다.**

```
var Car = function(position) {
    this.position = position;
};

Car.prototype.move = function() {
    this.position += 1;
};

var car1 = new Car(5);
var car2 = new Car(10);
```

 

\1. 함수 생성 : 함수 이름은 대문자로 시작(일반 함수와 구분하기 위함)

\2. 빈 객체 생성 X : this를 이용해서 함수 안에서 프로퍼티 추가

\3. 메서드 추가 : 부모 객체에 바로 메서드를 추가

\4. 인스턴스 객체 반환 X

 

장점 : 인스턴스 객체를 생성하는데 최적화되어 있다. 함수에서 인스턴스 객체 반환할 필요가 없다.