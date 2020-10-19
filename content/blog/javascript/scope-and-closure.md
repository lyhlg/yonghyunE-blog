---
title: Scope and Closure
date: 2020-10-19 16:10:33
category: javascript
thumbnail: { thumbnailSrc }
draft: true
keywords: ['javascript', 'javascript' , 'scope', 'closure', '자바스크립트 기초']

---

# 스코프와 클로저

## 스코프란?
스코프는 특정 장소에 변수를 저장하고 그 변수를 찾을 수 있도록 한 정의된 규칙이다.  
스코프는 변수(variable)의 접근성을 결정한다.  
자바스크립트(ES6)는 함수 레벨과 블록 레벨의 **렉시컬 스코프규칙**을 따른다.

## 컴파일러 이론
자바스크립트는 일반적으로 '동적' 또는 '인터프리터'언어로 분류하나 '컴파일러 언어'이다. 소스코드가 실행되기 전에 컴파일레이션(Compilation)단계를 거친다.

### 토크나이징 / 렉싱 / 렉스타임(Tokenizing / Lexing / Lex-time)
코드를 토큰 단위로 분리하여 의미를 매핑시키는 단계  
__토크나이징__: 문자열을 나누어 토큰 이라 불리는 의미 있는 조각으로 만드는 과정이다.  
__렉싱__: 토큰 처리과정에서 토큰을 분석하여 생성된 토큰에 의미를 부여하는 행위이다.
__렉스타임__: 렉싱 처리 과정을 Lex-time이라고 하며, 소스 코드 문자열을 분석하여 상태 유지 파싱의 결과로 생성된 토큰에 의미를 부여하게 되며 이 과정을 통해 렉시컬 스코프(Lexical Scope)이 형성 된다.

```javascript
// var a = 2; 는 아래처럼 각각 토큰으로 나눌수 있다.
var
a
=
2
;
```
위 문자열을 보고 컴파일러는 다음과 같이 동작한다.
1. `var a`를 만나면 스코프에게 변수 a가 특정한 스코프 컬렉션 안에 있는지 묻는다.(local scope / global scope)  
변수 a가 이미 있다면 컴파일러는 선언을 무시하고 지나가고, 그렇지 않다면 컴파일러는 새로운 변수 a를 스코프 컬렉션 내에 선언하라고 요청한다.
2. 그 후 컴파일러는 `a = 2` 대입문을 처리하기 위해 나중에 엔진이 실행할 수 있는 코드를 생성한다. 엔진이 실행하는 코드는 먼저 스코프에게 a라 부르는 변수가 현재 스코프 컬렉션 내에서 접근할 수 있는지 확인한다.  
가능하다면 엔진은 변수 a를 사용하고, 아니라면 엔진은 자신의 상위 스코프에 a값이 선언되어 있는지 확인한다.
3. 선언이 되어 있지 않다면 `RefferenceError`를 뱉게 되고 상위 스코프에 a가 선언되어 있다면 해당 값을 사용한다.

#### _참고_
**ReferenceError**: 스코프 체인을 통해 최상위 scope까지 올라갔지만 대상을 찾지 못했을 때 발생하는 에러  
```javascript
var a = 3;
function foo() {
    var b = 4;
    console.log(a);
    return a + b; // 7
}
console.log(b) // Reference Error
```
**TypeError**: 스코프 체인을 통해 스코프 검색은 성공 했으나, 결과값을 가지고 적합하지 않거나 불가능한 시도를 한 경우에 나타난다.
```javascript
var bar = 3;
bar(); // Type Error
```

## 렉시컬 스코프(Lexical Scope)
렉시컬 스코프에서는 소스코드가 작성된 그 문맥에서 결정된다.  
**다시 말하면 변수 또는 함수가 선언(호출이 아니다)된 곳에 따라 스코프가 결정된다.**
```javascript
var a = 10;

function foo() {
    var a = 3;
    console.log(a) // 3;
    bar();
}

function bar() {
    console.log(a); // 10
}

foo(); // 10
bar(); // 10
```
위와 같은 경우에 bar 함수에서 a를 찾는데 bar 함수는 전역에 선언되어 있기 때문에 전역에 상위 스코프는 전역 scope이다. 그래서 `a = 3`이 된다.

## 함수 vs 블록 스코프
### 함수 스코프 (Function-level scope)
자바스크립트는 함수 레벨 스코프를 사용한다. 함수 내에서 선언된 매개변수와 변수는 함수 외부에서는 유효하지 않다.
```javascript
function foo(a) {
    var b = 2;
    function bar() {
        console.log(b, c); // 2, undefined
    }
    bar();
    var c = 3;
    return a + b;
}
foo(3); // 5
console.log(a) // ReferenceError
console.log(b) // ReferenceError
console.log(c) // ReferenceError
console.log(bar) // ReferenceError
```
아래는 함수 내부 외부에 동일한 변수가 선언 되어 있을 때 어떻게 참조 하는지를 보여준다. 중첩 스코프는 가장 인접한 지역을 우선하여 참조하기 때문에 foo 내부의 a는 가장가까운 local에서 a를 찾고 검색을 멈추게 된다.
```javascript
var a = 'global';

function foo() {
    var a = 'local';
    console.log(a);
}

console.log(a); // global
foo(); // 'local'
```

## 블록 스코프 (Block Scope) 
var로 선언했을 경우에는 블록스코프의 영향을 받지 않는다. 
let으로 선언하였을 경우에는 해당 블록 스코프를 이용하게 되어 내부에서만 사용 된다. 
```javascript
var x = 0;
{
  var x = 1;
  console.log(x); // 1
}
console.log(x);   // 1

let y = 0;
{
  let y = 1;
  console.log(y); // 1
}
console.log(y);   // 0
```

<br />
<br />
<br />
<br />

### Reference
[You Don't Know JS](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch1.md)  
[자바스크립트의 스코프와 클로저](https://meetup.toast.com/posts/86)  
[Understanding Variables, Scope, and Hoisting in JavaScript](https://www.digitalocean.com/community/tutorials/understanding-variables-scope-hoisting-in-javascript)  
[blog](https://poiemaweb.com/js-scope)