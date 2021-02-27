---
layout: single
title: "TIL - 리액트 - Redux"
---

### Redux

1. redux란?
   - ‘컴포넌트 바깥에서 state(상태, 정보)를 관리하기 위한 목적’으로 고안된 라이브러리![img](https://media.vlpt.us/post-images/naseriansuzie/8ccc8b30-3227-11ea-80bb-6b2f352c268d/image.png)[Redux 구조]
  
2. react와 redux를 함께 사용할 때 사용되는 개념 3가지
   - Action : 어떠한 행동(Action)과 그에 따라 상태를 변경해주는 메소드들(methods)의 집합
   - Store : 컴포넌트들의 상태를 저장
   - Reducer : 개념적으로 Store 내부에 존재하며 Action 메소드에서 변경한 상태를 받아 기존의 상태를 새로운 상태로 변경하는 역할
3. 별도 state 관리
   - 보통 js로 클라이언트 개발을 할 때 react와 redux를 함께 쓴다고 한다. 그 이유는 React에서 사용하는 state와 컴포넌트 간 props 구조가 너무 복잡해지면 코드의 복잡도는 올라가고, 가독성은 낮아지기 때문이다.
   - 이 상황에서 redux는 "state와 관련된 별도 관리"라는 방법론으로 문제를 보완해준다. redux는 react의 state를 별도 store에 담고, state의 변경을 야기하는 action들도 별도의 action 파일에서 관리하면서 변경이 발생했을 때 reducer를 통해서 state를 업데이트 한다.
4. store & action
   - redux는 1) 액션 감지 2) 상태 변경을 효율적으로 관리할 수 있다.
   - 여기서 1) 액션 감지와 그에 따른 상태 변경을 위해 action 파일이 존재한다.
   - 2) 상태를 관리하는 store 파일이 존재한다.
5. redux의 장단점
   - 앞에서도 언급했듯이 redux는 기존 react-only로 컴포넌트 사이 복잡했던 state, props 관리를 교통정리 해주는 장점이 있다.
   - 다른 상태관리 라이브러리에 비해서 보일러 플레이트가 복잡한 편이다.
6. reducer 쪼개기 및 combineReducers

   - 서비스가 커지면서 action 또한 많아지게 된다. 이 경우에는 주요 기능별로 reducer를 나누고, combineReducers를 통해서 하나의 통합된 reducer로 만드는 별도의 작업이 필요하다.