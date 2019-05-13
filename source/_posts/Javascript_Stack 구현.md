---
title: JavascriptStack 구현
date: 2019-04-06 22:36:08
tags: [Javascript,Stack,DataStructures]
category: [Programming, DataStructures]
thumbnail: /images/logo-header.png
---

# Stack이란!?

> Stack은 LIFO원리에 따라 정렬된 컬렉션이다.
> 스택의 자료는 항상 동일한 종단점에서 추가/삭제된다. 
> 스택에서 종단점은 꼭대기(top)과 바닥(base) 둘 뿐인데, 가장 최근 자료는 꼭대기 근처에, 가장 오래된 자료는 바닥 근처에 위치한다.

# Stack을 구현하는데 필요한 메소드들

* push(): 스택 꼭대기(top)에 새 원소를 추가한다.
* pop(): 스택 꼭대기에 있는 원소를 반환하고 해당 원소는 스택에서 삭제한다.
* peek(): 스택 꼭대기에 있는 원소를 반환하되, 스택은 변경하지 않는다. (삭제하지 않는다.)
* isEmpty(): 스택에 원소가 하나도없으면 true, 스택의 크기가 0보다 크면 false를 반환한다.
* clear(): 스택의 모든 원소를 삭제한다.
* size(): 스택의 원소 개수를 반환한다. 배열의 length 프로퍼티와 비슷하다.

# Stack 만들기

#### 스택의 기본 틀.
<pre><code>function stack() {
    var items = [];
}
</code></pre>

#### push 메소드.
<pre><code>this.push = function(element) {
    items.push(element)
}</code></pre>

#### pop 메소드.
<pre><code>this.pop = function() {
    return items.pop();
}</code></pre>

#### peek 메소드.
<pre><code>this.peek = function(element) {
    return items[items.length - 1];
}</code></pre>

#### isEmpty 메소드.
<pre><code>this.isEmpty = function(element) {
    return items.length === 0;
}</code></pre>

#### claer 메소드.
<pre><code>this.clear = function(element) {
    items = [];
}</code></pre>


#### size 메소드.
<pre><code>this.size = function(element) {
    return items.length
}</code></pre>


### 전체 코드.
<pre><code>function stack() {
    var items = [];

    this.push = function(element) {
    items.push(element)
    }

    #### pop 메소드.
    this.pop = function() {
        return items.pop();
    }

    this.peek = function(element) {
        return items[items.length - 1];
    }

    this.isEmpty = function(element) {
        return items.length === 0;
    }

    this.clear = function(element) {
        items = [];
    }

    this.size = function(element) {
        return items.length
    }
}</code></pre>