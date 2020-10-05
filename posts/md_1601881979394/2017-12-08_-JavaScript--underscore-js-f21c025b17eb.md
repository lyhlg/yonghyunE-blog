---
title: '[JavaScript] underscore.js'
description: underscore 과제를 하면서 뭐하나 “와! 쉽다” 라고 생각하면서 푼 문제는 없다.
date: '2017-12-08T04:11:05.003Z'
categories: []
keywords: []
slug: /@lyhlg0201/javascript-underscore-js-f21c025b17eb
---

underscore 과제를 하면서 뭐하나 “와! 쉽다” 라고 생각하면서 푼 문제는 없다.

이 과제는 [underscore](http://underscorejs.org) (underbar) library를 일부 작성해보는게 목적이다.

링크를 참고해보면 약 70개? 정도 되는 함수를 제공한다. (세어보진 않았다 어디서본거같다)

일부는 javascript에 built-in 되어 있는 것들과 동일한 기능이 있고, 어떤 것들은 동일한 기능을 하는데 이름이 조금 다른 것들이 있다.

이중 내가 어려움을 겪었던 것들은 [higher order function](https://medium.com/@lyhlg0201/high-order-function-고차함수-a94ee6674c8c) 이 대부분이었다. 함수에 함수가 던져지고.. 어렵다. ^^

### \_.each

먼저 `_.each` 함수 이다.

> \_.each(list, iteratee, \[context\])

list를 반복하여 값을 하나씩 꺼내 iteratee에 해당하는 함수에 집어 넣는다.

아래는 `_.each` 사용 예제 이며 결과 값이다.

var letters = \['a', 'b', 'c'\];  
var iterations = \[\];

\_.each(letters, function(letter,index) {  
   iterations.push(\[letter, index\]);  
});

\----------------------------------  
console.log(iterations);     // \[\['a',0\] \['b',1\] \['c',2\]\];

위 결과는 쉽게 값을 대입해보면 구할수 있지만, 위처럼 결과값을 구할 수 있도록 `_.each` 함수를 만드는것이 목적이다.

먼저, array일 경우와 object일 경우를 나눠서 생각을 했다. 위에는 모두 표현 하지 않았지만 마지막 parameter로 context를 받게되는데 이건 그냥 array나 object의 이름을 말한다.

array 일 경우 / object일 경우 ( 나는 constructor 속성을 사용했다. ) 서로 index 표현법이 다르니 그 부분만 바꿔서 아래와 같이 소스코드를 작성하였다.

\_.each = function(collection, iterator) {  
    if ( collection.constructor === Array){  
      for ( var i = 0 ; i < collection.length ; i ++ ){  
        iterator(collection\[i\], i, collection);  
      }  
    }  
    else if ( collection.constructor === Object){  
      for ( var key in collection ){  
        iterator(collection\[key\], key, collection);  
      }  
    }  
};

### \_.reduce()

두번째로는 `_.reduce()` 함수이다. (이건어렵다. 내가작성한 것도 있지만, 좀더 최적화된 코드를 가지고 여기서는 다룬다.)

> \_.reduce(list, iteratee, \[memo\], \[context\])

list(array, object)를 iteratee에 넣어서 결과값을 return 한다.

이때, `memo`값이 존재하면 해당 값을 초기 값으로 하며, 만약 `memo` 값이 존재하지 않을 경우에는 `list`의 첫번째 요소를 초기 값으로 한다.

var result = \_.reduce(\[1, 2, 3\], function(memo, item) {  
   return memo - item;  
}, 10);  
console.log(result); // 4 

memo값 (초기값)이 존재 할 때와 안할 때를 고려 해야 하며, 위에서 설명했던 `_.each` 함수를 이용하여 구현한다.

\_.reduce = function(collection, iterator, accumulator) {  
    var hasAcc = arguments.length > 2;  
    \_.each( collection, function (item, index){  
      if (!hasAcc){  
          accumulator = item;  
          hasAcc ++;  
          return;  
      }  
      accumulator = iterator(accumulator,item);  
    });  
    return accumulator;  
};

분명 위 코드는 내가 작성한 코드는 아니다. (나는 `_.each` 함수를 이용하지 않고 for 문을 이용하였다. 당시에는 응용하기가 어려웠다.)

위 소스코드를 간단히 설명하면, `accumulator`가 존재 하지 않으면 초기값을 배열의 첫번째 `item`으로 설정하고 hasAcc값을 true로 변경한다음 리턴한 후 `_.each` 문을 돌린다. 그렇게 되면 초기값이 `collection` 의 첫번째 값으로 설정이 된 후 부터 `iterator` 함수를 돌려 `accumulator` 에 넣는다. `accumulator` 는 계속 축적된 값을 갖고 가게된다.

`_.memoize` `-.shuffle` 은 굉장히 어려웠다.

설명은 나중에..