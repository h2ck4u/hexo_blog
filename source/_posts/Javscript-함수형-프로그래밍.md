---
title: '[Javscript] Reduce, Map, Filter'
date: 2019-04-30 23:21:41
tags: [Javascript, FunctionalProgramming]
category: [Programming, Javascript]
---

# 함수형 프로그래밍 (Functional Programmming)
함수형 프로그래밍은 오늘날의 토론 주제이다.
많은 프로그래밍 언어는 람다와 같은 개념을 최신버전에 포함하고 있다. (ex: Java > 7이상)
Javascript에서는 함수형 프로그래밍에 대한 구조를 오래전부터 지원해왔다.
우리가 깊게 배워야 할 3가지 주요한 함수들이 있다.
Mathematical 함수는 몇가지 입력(input)을 가지고 출력(ouput)을 반환한다.
순수 함수는 주어진 입력에 대해 항상 같은 출력을 반환한다.
우리가 논의 할 함수는 순수함수를 만족한다.

# Map
map함수는 Javascript에서 배열에 사용 할 수 있다.
map함수를 사용하면 우리는 배열에 있는 각각의 요소에 transformation함수가 적용된 새로운 배열을 얻을 수 있다.
JS 배열의 map함수의 일반적인 문법은 다음과 같다.
~~~javascript
arr.map((elem){
    process(elem)
    return processedValue
}) // returns new array with each element processed
~~~
우리가 최근에 작업하고 있는 serial keys에 원치않는 문자들이 입력되었다고 가정하자.
우리는 그것들을 제거해야 한다. 반복하며 찾으면서 문자를 지우는 대신에, 우리는 map을 사용하여 동일한 작업을하고 제거된 배열을 얻을 수 있다.

~~~javascript
var data = ["2345-34r", "2e345-211", "543-67i4", "346-598"];
var re = /[a-z A-Z]/;
var cleanedData = data.map((elem) => {return elem.replace(re, "")});
console.log(cleanedData); // ["2345-34", "2345-211", "543-674", "346-598"]
~~~
### 참고 : JavaScript ES6의 Arrow Function을 사용했습니다.
map은 함수를 인자(parameter)로 받는다. 인자로 받은 함수를 인자를 가진다. 그 인자는 배열로부터 선택된다.
우리는 처리된(인자로받은 함수를 수행한) 요소를 반환해야하고 배열에 있는 모든 요소에 수행될 것이다.

# reduce
Reduce 함수는 주어진 리스트를 하나의 최종 결과로 감소시킨다. 우리는 배열을 반복하며 중간 결과값을 변수에 저장하면서 같은 일을 할 수 있다. 하지만 배열을 줄이는 깔끔한 방법이 있다. JS의 reduce의 일반적인 문법은 다음과 같다.


~~~javascript
arr.reduce((accumulator,
           currentValue,
           currentIndex) => {
           process(accumulator, currentValue)
           return intermediateValue/finalValue
}, initialAccumulatorValue) // returns reduced value
~~~

**accumulator** 는 중간값과 최종 값을 저장한다. 
**currentIndex**와 **currentValue**는 배열의 요소의 인덱으와 값이다.
**initialAccumulatorValue**는 해당값을 accumulator의 인자로 전달한다.

배열안의 배열을 flattening 할 수 있게하는 현실적인 application이다.
Flattening은 안쪽의 배열을 하나의 단일 배열로 변환시킨다.

~~~javascript
var arr = [[1, 2], [3, 4], [5, 6]];
var flattenedArray = [1, 2, 3, 4, 5, 6];
~~~

우리는 일반적인  반복을 통해 달성 할 수 있다. 하지만 reduec를 사용하면 직관적인 코드가 된다.
~~~javascript
var flattenedArray = arr.reduce((accumulator, currentValue) => {
    return accumulator.concat(currentValue);
}, []); // returns [1, 2, 3, 4, 5, 6]
~~~
filter

이것은 함수형 프로그래밍의 세번째 컨셉이다.
filter는 배열의 각 요소를 처리한다는 점과 마지막에 새로운 배열을 반환한다는점이 map과 비슷하다.

필터된 배열의 길이는 원본 배열의 길이와 같거나 혹은 더 적을 수 있다.

왜냐하면 우리가 통과 한 필터링 조건은 출력 배열에서 일부분의 입력을 제외시킬 수 있기 때문이다.

일반적인 구문은 아래와 같다.

~~~javascript
arr.filter((elem) => {
   return true/false
})
~~~

여기에서 **elem**는 배열의 요소 데이터이고 필터링 된 요소의 포함/제외를 나타내기 위해 함수에서 true/false를 리턴해야한다.
일반적인 예제는 배열을 주어진조건으로 시작하고 끝나는 단어를 필터하는 것이다.
우리는 '**t**'로 시작하고 '**r**'로 끝나는 단어를 배열에서 필터링 해야한다고 가정해보자

~~~javascript
var words = ["tiger", "toast", "boat", "tumor", "track", "bridge"]
var newData = words.filter((elem) => {
   return elem.startsWith('t') && elem.endsWith('r') ? true:false;
}); // returns ["tiger", "tumor"]
~~~

언제든지 누군가가 너에게 자바스크립트의 함수형프로그래밍의 측면을 물어볼 때 3가지 함수는 너의 손안에 있어야 한다. 
위에서 본 것 처럼 3가지 예제 모두 원본배열은 변화하지 않았다.
세가지 함수의 순수성을 제공한다.