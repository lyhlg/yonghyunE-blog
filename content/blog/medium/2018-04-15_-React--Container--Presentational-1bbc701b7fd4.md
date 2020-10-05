---
title: '[React] Container, Presentational'
description: Frontend 개발자로 취업하고 업무를 시작한지 일주일이 지났다.
date: '2018-04-15T06:24:13.486Z'
category: 'javascript'
keywords: []
draft: false
slug: /@lyhlg0201/react-container-presentational-1bbc701b7fd4
---

Frontend 개발자로 취업하고 업무를 시작한지 일주일이 지났다.

급급히 발생되는 업무를 쳐내야 하는 실무 업무는 업무대로 처리하고

급히 쳐내는 만큼 기초가 탄탄하지 않으면 나중에 남는게 없다고 생각이 든다.

그래서 틈틈히 React에 대한 기본 지식과 방법론 같은 것들을 공부하려고 한다.

이번 포스팅은 리액트 component 작성시 방법론이다.

React Component를 구분하는 데에는 아래와 같은 표현 방식이 있다.

**Container vs. Presentational**

**Stateful vs. Stateless**

**Smart vs. Dumb**

**Pure vs. Unpure**

이런 방식들이 왜 나왔나 생각해 보면 모든 언어에서 그렇겠지만 React 특성상 Component Reusable을 하지 못한다면 굉장히 비효율 적일 것이다.

하나의 Component에서 Data Fetch 및 Data Render를 같이표현하게된다면?

하나일때는 동일하게 표현 될 수 있지만 Render 하는 부분이 중복이 될경우 Component 마다 Render부분을 구현해야 될 것이고 코드의 중복이 발생될 것이다.

이러한 문제 때문에 우리는

1.  주로 데이터를 가져오고 상태를 관리하는 Container와 같은 존재
2.  데이터를 Props로 받아 화면에 보여주고 뿌려주는 Presentational 같은 존재로 구분할 필요 가 있다.

위에서 말한 React Component를 구분 방식은 사실 어떻게 누가 표현하냐에 따라 다른것 같다.

그리고 구분도 명확하게 딱딱 맞출순 없다. (개발환경에 따라 얼마든 바뀔수는 있으니)

하지만 주된 임무는 명확한것 같다.

#### Container : _how things work_.

1.  Data를 fetching 하는것이 주 목적
2.  연관된 서브 component 를 render 한다.
3.  일부 wrapping을 제외하고는 DOM markup 이나 style(css)이 없다.
4.  데이터의 소스 역할을 하기 때문에 거의 stateful 하다.

#### **Presentational : how things look.**

1.  자체 DOM markup 뿐만 아니라 style(css)도 가지고 있다.
2.  props를 통해 data 및 callback을 수신한다.
3.  State를 가지지는 않으나, 상황에 따라 갖게 된다면 data의 변경이 아닌 UI State 용도로 사용한다.
4.  State, lifecycle, Performance optimization이 필요한 경우가 아니면 Function component로 작성한다.

예전엔 stateful / stateless로 구분을 하면서 약간 덜 깊게 공부했다라 할까.. 난 지금 해당 Presentational Component를 stateful로 표현을 해야 하는데 약속대로 라면 stateless로 표현하는게 맞고.. 이걸 어떻게 해야할까 고민을 했던적이 있었다.

사실상 이러한 구분은 데이터를 가져오는 부분과 보여주는 부분으로 나눴을 뿐 정확하게 Component를 함수형으로 써야한다 state형으로 써야한다라는 구분은 없었다.

[**Presentational and Container Components**  
\_You’ll find your components much easier to reuse and reason about if you divide them into two categories.\_medium.com](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0 'https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0')[](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)

위 글을 읽고 위 부분을 내 입맛대로? 정리해보았고, 많은 도움이 되었다.
