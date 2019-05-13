---
title: '[Javascript] Hoisting '
date: 2019-05-13 21:39:57
tags: [Javascript, hoisting]
category: [Programming, Javascript]
---
**호이스팅**이라는 단어는 많은 자바스크립트 블로그에서 식별자 해석(identifier resolution)을 설명하는데에 사용된다. 단어 그대로의 의미를 사용하면, 호이스팅은 변수와 함수의 선언이 어떻게 전역스코프 또는, 함수의 최상단으로 올라가는지 설명하기위해 사용된다.

While this does provide a basic understanding of how JavaScript scoping works, a deeper dive helps to build a stronger foundation.

이것은 자바스크립트의 scoping이 어떻게 동작하는지 기본적인 이해를 제공하지만, 더깊게 파고들면 강한 구조를 세우는데 도움이 된다.

기본원리를 더 잘 이해하기 위해서는, 호이스팅이 정확히 무엇을 의미하는지 다시한번 살펴보아야한다. **Javascript**는 컴파일언어가 아닌 코드가 줄단위로 실행되는 해석형 언어이다 .

다음 예제를 살펴보자.

~~~javascript
console.log(notyetdeclared);
// prints out 'undefined'

var notyetdeclared = 'now it is declared';

hoisting();

function hoisting(){
  console.log(notyetdeclared);
  // prints out 'undefined'
  
  var notyetdeclared = 'declared differently';
  
  console.log(notyetdeclared);
  // prints out 'declared differently'
}
~~~

상단의 코드를 분석해보면, 몇가지 질문이 있다.

6번째 줄에서 선언되기 전에 어떻게 함수에 접근 할 수 있을까 ?

notyetdeclared 변수가 존재하지 않을때 1번째 줄에서 왜 에러를 던지지 않을까?

notyetdeclared 변수가 이미 전역 스코프에서 선언 되었는데 9번째 줄에서 undefined가 프린팅 될까?

자바스크립트는 매우 논리적이며, 모든 기이함에는 명확한 이유가 있다.

최상단으로부터 보면, 자바스크립트에서 코드가 실행될때, **execution contenxt**가 구성 된다.  자바스크립트에는 2가지  **execution contenxt** 타입이 있다. **Global execution contenxt**과 **Function execution contenxt**이다. 자바스크립트는 싱글스레드 실행 모델에 기반하고 있고, 한번에 오직 한개의 코드조각이 실행된다. 위 코드에서는 다음과 같은 과정을 가진다.

![](/image/20190513/callstack.png)

This process is self explanatory but doesn’t really explain the anomalies we saw during the execution of the code sample. While the execution context keeps track of the execution of the code, Lexical environment keeps track of the mapping of identifiers to specific variables. Lexical environment basically is an internal implementation of the JavaScript scoping mechanism. 
Generally, the lexical environment is associated with a specific structure of the JavaScript code for example a function or a block of code like a for loop. Whenever a function is created, a reference to the lexical environment in which it was created is passed in an internal property named [[Environment]].

이과정은 따로 설명이 필요없지만,  실제로 코드 샘플을 실행하는 동안 보았던 변칙을 설명하지는 않습니다. 실행컥텍스트가 코드의 실행을 추적하는동안 Lexical environment는 특정 변수에대한 식별자 매핑을 추적한다.
Lexical environment는 자바스크립트 scoping 메커니즘의 내부 구현이다. 일반적으로 Lexical environment는 자바스크립트 코드의 특별한 구조 예를들면 함수 또는 for loop와 같은 블록코드와 관련되어있다. 
함수가 생성되었을 때, Lexical environment의 참조는 [[Environment]]라는 내부 속성에 전달된다.

Covered by all this jargon is a simple and an extremely logical concept. Lets break it down. Lexical environment is a fancy name for something that keeps track of variables and functions within a block of code. In addition to keeping track of local variables, function declarations and parameters, each lexical environment keeps track of its parent lexical environment. So the Javascript Engine’s resolution of the above code sample would look something like this:

이 모든 특수한 경우가 적용되는 것은 단순하고 매우 논리적인 개념이다. 그것을 깨뜨리자. Lexical environment은 코드 블록내에서 변수와 함수를 추적하는 멋진 이름이다. 지역 변수, 함수선언 및 매개변수를 추적하는 것 외에도 각 Lexical environment는 부모 Lexical environment를 추적 한다. 상단 코드의 자바 스크립트 엔진의 Lexical environments 다음과 같다.

![](/image/20190513/lexicalenvironment.png)

To resolve an identifier within a lexical environment, the JS engine checks the current environment for a reference. If no reference is found, it moves on to the outer environment by using [[environment]]. This goes on until either the identifier is resolved or a ‘not defined’ error is thrown.

Basically, the execution of JS code happens in two phases. The first phase registers all the variables and function declarations within the current lexical environment. After that is done, the second phase — Javascript execution begins!