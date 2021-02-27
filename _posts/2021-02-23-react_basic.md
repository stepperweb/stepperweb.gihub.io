---
layout: single
title: "TIL - 리액트 - basic"
---

## 리액트는 무엇인가?

1. React

   - React는 페이스북이 만든 자바스크립트 라이브러리로, MVC 패턴 중 view layer를 담당한다.
   - 자바스크립트를 이용한 프론트엔드 구현에는 다양한 방법이 있는데(바닐라js+css+html, Vue, Angular 등) 그 중 하나이며 개발자들에게 인기 있는 라이브러리다.

   

2. 주요 개념: Component

   - React는 Component(컴포넌트)를 중심으로 구축할 수 있는데, 여기서 컴포넌트는 마치 customized html element와 같다고 볼 수 있다.
   - **컴포넌트 정의 :** 하나의 의미를 가진 독립적인 모듈
   - 컴포넌트의 두 가지 핵심 원리: **독립적으로 기능할 것**과 **재사용 가능할 것**
   - 컴포넌트는 잘게 쪼갤 수록 좋은데 이는 **재사용성**과 **코드 관리에 용이**하기 때문이다. 하나의 컴포넌트가 하나의 기능만 하게 함으로써 에러 발생 시 해결도 용이하다.

3. 주요 개념: 가상 DOM

   - React는 가상DOM을 사용하는데, 가상의 DOM을 렌더하는 과정을 통해 기존의 html DOM 사용 시 브라우저에 가해졌던 부담을 많이 줄였다.
   - 리액트로 구현한 웹앱에서 html은 root div가 존재하고 나머지는 상→하로 흐르는 리액트 컴포넌트의 스트림 구조로 핸들링 한다.

4. 주요 개념: JSX

   - JSX는 React에서 컴포넌트를 만드는 특수한 문법이다.
   - 자바스크립트의 형태를 띄고 있으나 내부에는 html 엘리먼트를 삽입하는 듯한 모양이다.
   - JSX는 React “엘리먼트(element)” 를 생성하는 주요 역할을 맡는다.
   - JSX : 규칙
     - class가 아니라 className을 사용: class는 이미 js에서 예약어이기 때문에
     - carmelCase 사용: DOM에서 사용하듯 onclick이 아니라 onClick이라고 사용
     - 컴포넌트 생성 후 태그를 반드시 닫아야 함
     - JSX 안에서 js를 사용할 때에는 반드시 { } 안에서 사용해야 함
     - JSX로 작성된 컴포넌트는 실험적 문법을 처리해주는 Babel이 JS코드로 컴파일된다.

### Props

1. Props 정의: 상위 컴포넌트에서 하위 컴포넌트로 물려 받는 속성(데이터)
2. React의 특징 중 하나는 단방향 흐름을 가진다는 것인데, props라는 것을 통해 데이터의 흐름을 핸들한다.
   - 상위 컴포넌트에서는 데이터를 만들고, 이를 props에 담아 하위 컴포넌트에 전달한다.
   - 하위 컴포넌트는 전달 받은 this.props의 해당 데이터 변수명을 찾아서 사용한다.
3. props는 html처럼 기본이 문자열(string)이기 때문에 부모 컴포넌트에서 다른 자료형을 담아 전달하려면 { } 안에 넣어 전달해야 한다.
4. props는 상위 객체에서 지정한 후에는 하위 객체에서 변경할 수 없고 read-only만 가능하다.

### State

1. State 정의: 컴포넌트의 특정 상태, 객체 형태로 컴포넌트 내에서 보관하고 관리
2. State는 props와 유사하지만, **비공개**이며 **컴포넌트에** **의해** **완전히** **제어된다.**
3. state의 위치: 컴포넌트가 만들어질 때 가장 먼저 설정되는 것이기 때문에 constructor 안에 위치한다.
4. state는 컴포넌트가 db에 접근해 뭔가를 수정하기 전 상태에 임시로 어떤 데이터를 넣었다가 뺐다가 할 수 있는 공간과 같다. 데이터를 넣을 때에는 state라는 배열 안에 객체 형태(key는 데이터를 가리키는 변수명, value는 실제 데이터들)로 넣는다.
5. state에 있는 데이터를 변경하기 위해서는 this.setState()라는 내장 메소드를 사용해야만 변경을 인식한다. setState의 실행 후에는 항상 리액트가 변경을 감지하여 새롭게 render를 실행하는데 그냥 `this.state.property = 값`으로 처리하면 변경을 감지하지 못해 render 또한 이루어지지 않는다.
6. Props와 State 구별하기
   - 참조 링크: https://ko.reactjs.org/docs/faq-state.html#what-is-the-difference-between-state-and-props
   - 두 객체 모두 렌더링 결과물에 영향을 주는 정보를 갖고 있는데, props는 (함수 매개변수처럼) 컴포넌트에 전달되는 반면 state는 (함수 내에 선언된 변수처럼) 컴포넌트 안에서 관리된다.
   - 시간이 지나도 변하지 않는가? ( yes → props, no → state )

### Life Cycle

![스크린샷 2021-02-23 오후 11.07.32](/Users/erick1129/Desktop/스크린샷 2021-02-23 오후 11.07.32.png)

1. Life Cycle(생명 주기) 정의: 컴포넌트가 생성되고 소멸되는 모든 과정
2. Life Cycle Event: 이러한 생명주기 안에서는 특정 시점에 자동으로 호출되는 메소드들
3. 생성 시 flow
   - constructor: 컴포넌트 생성 시 1회 설정되고, state를 정할 수 있다.
   - componentWillMount: 컴포넌트가 DOM에 렌더 되기 전에 실행된다.
   - render: 컴포넌트 정의에 의해 브라우저에 컴포넌트를 반환한다.
   - componentDidMount: 컴포넌트 생성과 렌더 후 호출된다. AJAX나 타이머를 생성하는 코드를 작성하는 부분이다.
4. 업데이트 시 flow
   - componentWillReceiveProps: 컴포넌트가 prop를 새롭게 받았을 때 실행, props에 따라 state를 업데이트 해야 할 때 활용
   - shouldComponentUpdate: props, state가 변경될 때 렌더를 할지 말지 결정하는 단계, re-render 전이기 때문에 전-후 비교 가능
   - componentWillUpdate: 컴포넌트가 업데이트 되기 전에 실행
   - render: setState로 업데이트를 감지한 후 브라우저에 한 번 더 컴포넌트를 반환한다.
   - componentDidUpdate: 업데이트에 의해 렌더가 된 후 호출된다.
5. 제거 시 flow
   - componentWillUnmount: 컴포넌트가 DOM에서 삭제된 직후 실행되는 메소드, 컴포넌트 내부에서 타이머나 AJAX를 사용하고 있을 때 이를 제거하기에 좋은 시기이다.
     - [참고자료]
       -  https://www.youtube.com/watch?v=t-JV5tXpXJw
       -  https://velopert.com/1130

### Functional component vs Class component

1. React에서 컴포넌트를 생성하려면 일반적인 함수 생성 방법과 클래스 형식의 생성 방법 중 선택할 수 있다.

   - Functional component(Simple components) : es6 arrow function과 비구조화 문법을 이용한 함수형 생성 방식이다. prop 값의 변경 없이 바로 렌더하고자 할 때 사용한다.

   - Class components: 클래스 형식으로 작성한다. 반드시 render라는 method를 사용해야 하고, 클래스 내에서 state 관리 할 수 있고, life cycle에 맞춘 함수 관리가 가능하다.

     

2. 함수형 컴포넌트 생성 방식

   ```js
   const PrintHello = (props) => {
       return <div>Hello {this.props.name} </div>;
   }
   ```

3. 클래스 컴포넌트 생성 방식

   ```js
   class PrintHello extends React.Component {
       render() {
           return( <div>Hello {this.props.name}</div> );
       }
   }
   ```

