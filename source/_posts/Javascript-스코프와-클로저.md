---
title: '[Javascript] 스코프와 클로저'
date: 2019-05-07 22:42:38
tags: [Javascript, scope, closures]
category: [Programming, Javascript]
---

# 자바스크립트 스코프 잘 이해하기.

자바스크립트의 Scope는 판도라상자이다. 수백가지의 어려운 면접 질문들은 이 개념으로부터 구성 될 수 있다.
Scope는 세 가지의 종류가 있다.

1. Global Scope (전역 스코프)
2. Local Scope / Function Scope (지역 스코프 / 함수 스코프)
3. Block Scope (ES6에서 도입됨)

우리가 일반적으로 말하는 글로벌 스코프.
~~~javascript
x = 10;
function Foo() {
    console.log(x); // Prints 10
}
Foo()
~~~

함수 스코프는 변수를 지역적으로 선언할 때이다.
~~~javascript
pi = 3.14;
function circumference(radius) {    
     pi = 3.14159;
     console.log(2 * pi * radius); // Prints "12.56636" not "12.56"
}
circumference(2);
~~~

ES6 표준에서는 주어진 괄호블록에서 변수의 스코프를 제한하는 새로운 블록스코프를 도입했다.

~~~javascript
var a = 10;

function Foo() {
    if (true) {
        let a = 4;
    }

    alert(a); // alerts '10' because the 'let' keyword
}
Foo();
~~~

함수와 조건은 블록으로 간주된다. 위의 예는 조건문이 실행 되기 때문에 4를 알럿 시켜야한다.
하지만 ES6는 블록 변수를 파괴하고 스코프는 전역으로 변경 되었다.

이제는 magical 스코프를 보자.
**클로저**를 사용하여 달성 할 수 있다. 
Javascript 클로저는 다른 함수를 반환하는 함수이다.

만약 누군가가 이 문제를 물어본다면. 문자열을 받아서 문자를 반환하는 설계를 작성해라. 만약에 새로운 문자열이 주어진다면 이전 문자열을 교체해야한다. 이것은 generator라고 불린다.

~~~javascript
function generator(input) {
      var index = 0;
      return {
           next: function() {
                   if (index < input.length) {
                        index += 1;
                        return input[index - 1];
                   }
                   return "";
           } 
      }
}
~~~

실행을 하면 다음과 같이 동작한다.

~~~javascript
var mygenerator = generator("boomerang");
mygenerator.next(); // returns "b"
mygenerator.next() // returns "o"

mygenerator = generator("toon");
mygenerator.next(); // returns "t"
~~~

scope는 중요한 규칙으로 수행된다. 클로저는 다른함수를 반환하고 데이터를 감싼 함수이다.
위의 string generator는 클로저에 알맞다. **index** 값은 여러 함수가 호출 될때 보존된다.
내부에 정의된 함수는 부모의 함수에 정의된 변수에 접근 할 수 있다. 이는 다른 스코프이다. 
만약 너는 하나의 함수를 두번째 레벨의 함수에 정의한다면 그 함수는 모든 부모의 변수에 접근 할 수 있다.