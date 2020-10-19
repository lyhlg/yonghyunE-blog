---
title: var, let and const 차이점
date: 2020-10-19 17:10:95
category: javascript
thumbnail: { thumbnailSrc }
draft: true
keywords: ['javascript', 'javascript 기초', 'var', 'let', 'const', 'var let const 차이']

---

# var, let, const 차이점
var, let, const는 scope, hoisting, 재선언 및 재할당으로 구분할 수 있다.

| Keyword | Scope | Hoisting | 재선언 | 재할당 |
|---|---|---|---|---|
| `var` | Function scope | O | O | O |
| `let` | Block scope | X | O | X |
| `const` | Block scope | X | X | X |

## var 
var로 선언된 변수의 범위는 현재 실행 문맥인데, 그 문맥은 둘러싼 함수(local), 혹은 함수의 외부에 전역(global)으로 선언된 변수도 될 수 있다.

### scope
Function scope를 가지며 내부에 선언된 `console.log(a)`는 가장 가까운 a 변수를 참조 하게 된다. 
```javascript
var a = 3;
function foo() {
    var a = 10;
    console.log(a); // 10
}
console.log(a) // 3
```
var는 block scope가 아니기 때문에 아래와 같은 경우에는 블록스코프 영향을 받을 수 없다.
```javascript
var a = 3;
{
    var a = 7;
}
console.log(a); // 7
```

### 호이스팅(hoisting)
호이스팅이 가능하기 때문에 선언문(`var a`)는 컴파일레이션 단계에서 처리가 된다. 이렇게 되면 변수와 함수 선언된 위치에서 코드의 꼭대기로 끌어 올려지게 되며 호이스팅 된다.
```javascript
console.log(a); // undefined 
var a = 2; 
```
위코드는 아래코드 처럼 인식된다
```javascript
var a;
console.log(a); // undefined 
a = 2; 
```
함수 선언문과 함수표현식은 조금 다르게 동작한다.  
함수 선언문
```javascript
foo();
function foo() {
    // ...
}
```
함수 표현식
```javascript
foo(); // TypeError
var foo = function bar() {
    // ...
}
```


<br />
<br />
<br />

#### Reference
[MDN - javascript var](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/var)