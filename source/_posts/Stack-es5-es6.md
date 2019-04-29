---
title: Stack es5->es6
date: 2019-04-08 20:23:07
tags: [Javascript,Stack,DataStructures, es6]
category: [Programming, DataStructures]
---

# Stack 코드 정리
> es5문법을 es6로 변경해보자!

### es5문법으로 작성된 코드.
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

### es6문법으로 작성된 코드.
<pre><code>class Stack() {
    constructor() {
        this.items = [];
    }
    
    push(element) {
        this.items.push(element)
    }

    pop() {
        return this.items.pop();
    }

    peek(element) {
        return this.items[this.items.length - 1];
    }

    isEmpty(element) {
        return this.items.length === 0;
    }

    clear(element) {
        this.items = [];
    }

    size(element) {
        return this.items.length
    }
}</code></pre>