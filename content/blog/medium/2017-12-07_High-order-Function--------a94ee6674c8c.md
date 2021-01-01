---
title: High-order Function (고차함수)
description: 고차함수란?
date: '2017-12-07T09:41:57.214Z'
category: 'javascript'
keywords: []
draft: true
slug: >-
  /@lyhlg0201/high-order-function-%EA%B3%A0%EC%B0%A8%ED%95%A8%EC%88%98-a94ee6674c8c
---

### 고차함수란?

> 하나 이상의 함수를 인수를 취하는 함수를 말한다.

> 좀더 자세히 말하면 _‘함수를 인수 또는 반환값으로서 취급하는 함수’ 를 고차 함수(High-order function)이라고 하며, Array객체의 forEach, map, filter등의 메소드는 모두 고차 함수에 속한다._

함수의 인수도 함수 (고차함수)를 공부하면서 해당 개념을 이해하기에 쉬운 예제 하나를 첨부했다.

function foo (arr, func){  
 for ( var key in arr ){  
 func(key,arr\[key\]);  
 }  
}

var arr = \[1,2,3,4,5\];  
foo(arr,function(key, value){  
 console.log("key/Value : " , key, "/",value);  
});

\-----------------------------------------------------

\[result\]  
key/Value : 0 / 1  
key/Value : 1 / 2  
key/Value : 2 / 3  
key/Value : 3 / 4  
key/Value : 4 / 5

익명함수(위의 예제에서는 ‘func’)를 인자로 전달하지 않고 함수를 정의한다음 함수 객체를 넘겨도 되지만, 위처럼 사용하는게 코드를 더 간결하게 만들 수 있다.
