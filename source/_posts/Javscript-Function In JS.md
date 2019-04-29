---
title: '[Javscript] 자바스크립트에서 함수란?'
date: 2019-04-29 21:28:44
tags: [Javascript, Function]
category: [Programming, Javascript]
---
# 함수
자바스크립트의 함수에 대해 공부를 하다보면, "자바스크립트에서 함수는 1급객체(first class object)이다." 라는 글을 많이 보게 된다.

여기서 말하는 1급 객체란 무엇일까?

먼저 1급객체의 어원에 대해서 알아보자.

# 1급 시민(first class citizen)의 정의
Christopher Strachey는 1967년 수업에 사용한 노트1에서 다음과 같이 1급 시민(first class citizen)과 2급 시민(second class citizen)을 소개했다. 아주 정확하게 정의한 것은 아니지만 ALGOL의 실수(real number)와 프로시져(procedure)를 비교하면서 설명하였다.
> In ALGOL a real number may appear in an expression or be assigned to a variable, and either may appear as an actual parameter in a procedure call. A procedure, on  the other hand, may only appear in another procedure call either as the operator (the most common case) or as one of the actual parameters. There are no other  expressions involving procedures or whose results are procedures. Thus in a sense procedures in ALGOL are second class citizens—they always have to appear in person  and can never be represented by a variable or expression (except in the case of a formal parameter), while we can write (in ALGOL still)

# 1급 객체의 조건
1. **변수(variable)**에 담을 수 있다
2. **인자(parameter)**로 전달할 수 있다
3. **반환값(return value)**으로 전달할 수 있다

------

자바스크립트에서의 함수는 **1급 객체**의 3가지 조건을 다 만족한다.

##### 변수(variable)에 담을 수 있다
~~~javascript
let sum = function(a, b) {
    return a+b;
}
~~~

##### 인자(parameter)로 전달할 수 있다
~~~javascript
function _each(list, func) {
    for (var i = 0, endi = list.length; i < endi; i++) {
        func(list[i], i)
    }
}

let arr = [1,2,3,4,5];
_each(arr, function(item, index, list){
    console.log(item, index, list)
});
~~~
위 코드는 주어진 배열을 모두 순회하는 forEach함수를 구현한 것으로, 
예제와 같이 _each함수에 인자(parameter)로 함수를 전달 할 수 있다.

간단한 예로는 jQeury의 on,off 메소드, DOM API의 addEventListener와 같은 함수도 위에 해당한다.

##### 반환값(return value)으로 전달할 수 있다
~~~javascript
function add(a) {
    return function(b) {
        return a + b;
    }
}
~~~
add 함수는 a라는 인자를 가지고 있다가, b인자를 받는 **함수**를 반환합니다. 
a는 반환 된 **함수**가 생성 된 클로저 때문에 두 번째 내부 함수에서 a를 기억하게 된다.
~~~javascript
let add5 = add(5);
~~~
위와 같이 add5라는 변수에 인자로 5를 넘겨 주었다.
add5라는 변수는 b인자를 받는 **함수**로 선언되었고,
**b를 인자로 받는 함수**가 생성 되었을 때, a = 5; 라는 a변수를 기억 하고 있게 된다.
~~~javascript
console.log(add5(3)); // a(5) + b(3) => 8
console.log(add5(10)); // a(5) + b(5) => 10
~~~
위와 같이 호출을 할 경우, b인자를 받는 함수가 실행되어 a에 할당되어있는 5와 b인자를 더하여 리턴하게 된다.
결과값은 8과 15가 된다.

# 정리
위에서 언급한 몇가지 예로 보았을 때, 자바스크립트의 함수는 일급객체의 3가지 조건에 모두 충족하게 된다.
자바스크립트의 함수는 **1급 객체**이다.
다음에는 클로저와 함수형 프로그래밍에 대해 공부해보자.