---
title: You Don't Know JS Chapter1 - this
date: 2020-10-12 15:10:61
category: javascript
thumbnail: { thumbnailSrc }
draft: false
---

> You Don't Know JS 책 내용을 토대로 이해한 내용들을 정리합니다. 

![uDontKnowJS](img/youDontKnowJS.jpg)

# 들어가기전에
해당 Chapter를 읽으면서 프론트엔드 개발자로 업무를 진행해 나가면서 this 때문에 고통 받았는지 고통 받지 않기 위해 회피해서 써왔는지 되돌아 볼 수 있는 계기가 되었다. 이전 블로그 작성 때 Prototype을 학습하고 this의 바인딩을 학습하면서도 조금 더 이해가 잘 되었던 것 같다.  
React를 사용할 때 (hook을 사용하기 이전 15버전 이었던가..)잘 기억이 안나는데 함수를 매번 바인딩 해서 써왔었다. 당시에는 성능이 더 좋다 라고만 이해하고 사용 했었는데 이번 학습을 통해서 왜 this로 바인딩 하는 기본 함수를 작성하였고, arrow 함수로 작성된 함수를 지양 하였는지 알 수 있었다.

<br />
<br />

# This에 대한 오해
### this가 함수 그 자체를 가리킨다. (X)
```javascript
function foo(num) {
    this.count = num;
}
foo.count = 0;
foo(3);
console.log(foo.count); // 0
console.log(window.count) // 3
```
> 위의 count는 전역객체 브라우저에서 window를 바인딩 하고 있다.

### this가 바로 함수의 스코프를 가리킨다. (X)
this는 어떤 식으로도 함수의 렉시컬 스코프(Lexical Scope)를 참조 하지 않는다. -> 연결 통로 따윈 없다.

<br />

**어떤 함수를 호출하게 되면 실행 콘텍스트(Execution Context)가 만들어진다. 여기엔 함수가 호출된 근원(Call-stack)과 호출 방법, 전달된 인자 등의 정보가 담겨 있다. This 레퍼런스는 그 중 하나로, 함수가 실행되는 동안 이용할 수 있다.**

<br />
<br />

---
<br />
<br />

# This의 호출부
this 바인딩의 개념을 이해하려면 먼저 호출부(Call-site), 즉 함수 호출(선언 아님) 코드부터 확인하고 'this가 가리키는것' 이 무엇인지 찾아야 한다.
호출 스택(현재 실행 지점에 오기까지 호출된 함수의 스택)을 생각해보아야 한다. 이 중 호출부는 현재 실행 중인 함수 '직전'의 호출 코드 '내부'에 있다.

```javascript
function baz() {
    // 호출 스택: 'baz'
    // 호출부는 전역 스코프 내부
    console.log('baz');
    foo();
}
function foo() {
    // 호출 스택: 'baz -> foo'
    // 호출부는 baz 내부
    console.log('foo');
}
baz(); // baz 호출부
```

# 그럼 호출부는 This가 무엇을 참조 할지 어떻게 결정하지?
아래 4가지 규칙을 확인한다.

## 기본 바인딩
평범한 함수 호출 (단독함수실행-Standalone function invocation)에 관한 규칙 이며, 나머지 규칙에 해당하지 않을 경우 적용되는 <u>this의 기본 규칙</u>이다.

### 일반적인 경우
```javascript
function foo() {
    console.log(this.a);
}
var a = 2;
foo(); // 2;
```
기본 바인딩이 적용되어 foo 함수 호출시에 this.a는 **전역 객체의 a**를 가리킨다.

### 엄격 모드(Strict Mode)
```javascript
function foo() {
    "use strict"
    console.log(this.a);
}
var a = 2;
foo(); // Uncaught TypeError: Cannot read property 'a' of undefined
```
엄격 모드에서는 전역 객체가 기본 바인딩 대상에서 제외되어 this는 **undefined** 가 된다.

## 암시적 바인딩 (Implicit Binding)
호출부에 콘텍스트 객체가 있는지, 즉 객체의 소유/포함(Owning/Containing) 여부를 확인하는 것이다. 

### 일반적인 경우
```javascript
function foo() {
    console.log(this.a);
}
var obj = {
    a: 2,
    foo,
}
obj.foo(); // 2
```
obj 객체의 foo 프로퍼티에 foo() 함수의 레퍼런스를 할당했다. (obj에서 foo() 함수를 Property로 참조하고 있다.) 여기서 주의할 점은 obj 객체는 실제로 함수를 소유 또는 포함 하고 있는 상태는 아니다! 하지만 호출부(obj.foo())는 obj 콘텍스트로 foo()를 참조 하므로 호출 시점에는 함수의 레퍼런스를 소유/포함 한다고 볼 수 있다.  
콘텍스트 함수객체(obj)가 함수 호출시 this에 바인딩 된다.<br />**<u>foo() 호출시 obj는 this가 되므로 this.a는 obj.a가 된다.</u>**

### 암시적 소실
바인딩이 소실되는 경우 전역객체로 바인딩이 된다. (엄격 모드일 경우에는 undefined임)

```javascript
function foo() {
    console.log(this.test);
}
var obj = {
    test: 2,
    foo,
}
var bar = obj.foo; 
bar(); // undefined
```
위와 같은 문제는 명시적 바인딩을 통해 해결 할 수 있다.

## 명시적 바인딩 (Explicit Binding)
암시적 바인딩처럼 함수 레퍼런스 속성을 객체에 더하지 않고, 어떤 객체를 this 바인딩에 이용하겠다는 것을 명시적으로 나타낸다.
```javascript
    // example
    var obj = {
        ...
        foo: foo,
    }
```

### call, apply 를 이용한다. 
call, apply는 javascript Function 원형 객체에서 제공하는 메소드 이다. 함수로 선언된 (위에 예제에서 foo 함수) 값들은 [[[Prototype](../prototype)]]을 이용하여 자신의 원형 객체에 접근할 수 있어, 위 메소드들을 바로 사용할 수 있다. 
<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/call" target="_blank">call</a>,
<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/apply" target="_blank">apply</a>는 this에 바인딩 할 객체를 첫번째 인자로 받아 함수 호출 시 이 객체를 this로 셋팅한다.  
this를 지정한 객체로 직접 바인딩 하는 형태를 명시적 바인딩 이라고 한다.

일반적인 경우
```javascript
    function foo() {
        console.log(this.a);
    }
    var obj = {
        a: 2,
        // foo: foo -> 암시적 바인딩의 함수 레퍼런스 객체 추가 없이 가능하다.
    }
    foo.call(obj); // 2
```
foo.call()에서 명시적으로 this를 obj로 바인딩 하도록 함수를 호출한다.

## new 바인딩
```javascript
function Foo(str) {
    this.something = str;
}
var foo = new Foo('hello');
console.log(foo.something) // hello;
```

<br />
<br />

# 바인딩 예외
## this 무시
call, apply, bind메서드의 첫번쨰 인자로 null이나 undefined를 넘기면 this 바인딩이 무시되고 기본 바인딩 규칙이 적용된다.
```javascript
function foo() {
    console.log(this.a);
}
var a = 2;
foo.call(null); //2
```
이러한 경우는 foo에서 딱히 this의 범위 지정이 필요 없을 경우에 많이 사용한다.
```javascript
var list = [-20, -1, 12, 13, 59];
var max = Math.max.apply(null, list);
console.log(max) // 59
```

# 어휘적 this
ES6부터는 앞에 4가지 (일반, 암시적, 명시적, new 바인딩)규칙들을 따르지 않는 특별한 함수인 Arrow 함수가 있다.
Arrow 함수는 _function_ 이라는 키워드를 사용하지 않고 '=>' 로 표현한다.  
4가지 표준 규칙 대신 함수 또는 전역을 보고 this를 알아서 바인딩 한다.

(아래는 [김정환님의 블로그](https://jeonghwan-kim.github.io/2017/10/22/js-context-binding.html) 내용이 좋아서 example 예제를 참고 했습니다.)

## Arrow 함수를 쓰지 않은 예제
```javascript
function hello() {
  setTimeout(function callback() {
    console.log(this.name)
  }, 1000)
}

var obj = {
  name: "chris",
  hello: hello,
}

var name = "global context!"

hello() // 'global context!'
obj.hello() // 'global context!'
hello.call({ name: "chris" }) // 'global context!'
```
setTimeout함수는 1초 뒤에 callback 함수를 실행 시킨다.  
내장 함수 setTimeout 으로 호출하면 this 가 전역객체를 바라본다.
그래서 위처럼 this는 전역객체를 가리키고 있기 때문에 일반, 암시적, 명시적 으로 호출한 결과가 'global context'로 동일 하다.

## Arrow 함수를 사용하여 this를 상위 함수로 지정한 예제
```javascript
function hello() {
  setTimeout(() => {
    console.log(this.name)
  })
}
var obj = {
  name: "chris",
  hello: hello,
}
var name = "global contenxt!"

hello() // 'global contenxt!'
obj.hello() // 'chris'
hello.call({ name: "alice" }) // 'alice'
```
hello() 호출시에는 따로 지정해준 this scope가 없기 때문에 전역으로 바라보고 암시적으로 obj를 this의 범위로 한정하거나, 명시적으로 `{ name: "alice" }`를 넘겨줌으로서 this의 범위를 지정해주었다.

<br />
<br />

# 정리
함수 실행에 있어서 this 바인딩은 함수의 직접적인 호출부에 따라 달라진다.  
**일단 호출부를 식별한 후 다음 4가지 규칙 순서에 따라 우선순위 적용된다.**
1. **new 바인딩:** new로 호출했다면 새로 생성된 객체로 바인딩 된다. 
2. **명시적 바인딩:** call/apply/bind로 호출됐다면 주어진 객체로 바인딩된다. 
3. **암시적 바인딩:** 호출의 주체인 콘텍스트 객체로 호출됐다면 바로 이 콘텍스트 객체로 바인딩 된다.
4. **기본 바인딩:** 엄격 모드는 undefined 그밖엔 전역 객체로 바인딩 된다.

<br />
<br />

# React에서 일반적인 함수선언을 지향하고 Arrow 함수선언을 지양 했던 이유
**결론**: 함수 선언을 하게 되면 Prototype에 선언이 되어 공유 메소드 처럼 사용 할 수 있게 되어 메모리를 절약 할 수 있으나, Arrow 함수 선언을 할 경우에는 상속 받은 모든 객체에서 Arrow 함수로 선언된 함수들을 모두 상속 받는다.

```javascript
class A {
  constructor() {
    this.counter = 0;

    this.handleClick = () => {
      this.counter++;
    };
  }
  
  handleLongClick() {
    this.counter++;
  }
}
var a = new A();
console.log(a)
// A를 그대로 상속 받아서 counter 및 handleClick을 갖고 있으며 __proto__객체로 상위 A 함수를 가리키고 있다.
// counter: 0
// handleClick: () => { this.counter++; }
// __proto__: Object
console.log(a.__proto__)
// __proto__를 통해 A 함수의 prototype (공유메서드)에 접근할 수 있다.
// {constructor: ƒ, handleLongClick: ƒ}
```



<br />
<br />
<br />

#### Reference
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/call
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/apply
https://jeonghwan-kim.github.io/2017/10/22/js-context-binding.html
https://medium.com/@charpeni/arrow-functions-in-class-properties-might-not-be-as-great-as-we-think-3b3551c440b1