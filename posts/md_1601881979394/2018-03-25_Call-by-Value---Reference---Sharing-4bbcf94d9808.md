---
title: Call by Value / Reference / Sharing
description: 'Call by Value, Call By Reference, Call By Sharing'
date: '2018-03-25T06:06:29.482Z'
categories: []
keywords: []
slug: /@lyhlg0201/call-by-value-reference-sharing-4bbcf94d9808
---

function change(num, obj1, obj2) {

  num = num \* 10;

  obj1.item = "changed";

  obj2 = { item2: "changed" };

}

var num = 10;

const obj1 = { item: "unchanged" };

const obj2 = { item: "unchanged" };

change(num, obj1, obj2);

  
console.log(num);                 // 10

console.log(obj1.item);           // changed

console.log(obj2.item);           // unchanged

Call by Value, Call By Reference, **Call By Sharing**

위문제를 통해서 “_Call By Sharing_”이라는 개념을 알게 되었다.

전체적으로 이해한 바로는 아래와 같다.

> 1\. 값던지면 값을 지역 변수로만 사용 -> 전역에 있는 값은 변경 되지 않음 (Value)

> 2\. 객체의 인자를 던지면 그 객체가 가지고 있는 속성의 값을 변경은 가능 (Reference)

> 3\. 함수 내부로 할당 받은 객체에 새로운 메모리 값으로 할당은 불가능

설명 내용

1\. 값던지면 값을 지역 변수로만 사용 -> 전역에 있는 값은 변경 되지 않음 (Value)

function change(num) {

   num = num \* 10;

}

var num = 10;

change(num);

  
console.log(num);                 // 10

2\. 객체의 인자를 던지면 그 객체가 가지고 있는 속성의 값을 변경은 가능 (Reference)

function change(obj1) {

   obj1.item = "changed";

}

var num = 10;

const obj1 = { item: "unchanged" };

change(obj1);

console.log(obj1.item);           // changed

3\. 함수 내부로 할당 받은 객체에 새로운 메모리 값으로 할당은 불가능

function change(obj2) {

   obj2 = { item2: "changed" };

}

const obj2 = { item: "unchanged" };

change(obj2);

console.log(obj2.item);           // unchanged