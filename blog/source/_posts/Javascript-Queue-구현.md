---
title: Javascript_Queue 구현
date: 2019-04-11 22:04:24
tags: [Javascript,Stack,DataStructures]
category: [Programming, DataStructures]
thumbnail: /images/logo-header.png
---

# Queue란!?

> FIFO 원리에 따라 정렬된 컬렉션이다.
> 새 원소는 뒤로 들어가서 앞에서 빠져나가는 구조다.
> 따라서 마지막에 추가된 원소는 큐의 뒷부분에서 제일 오래 기다려야한다.

# Queue을 구현하는데 필요한 메소드들

* enqueue(): 큐의 뒤쪽에 원소를 추가한다.
* dequeue(): 큐의 첫 번째 원소를 반환하고 큐에서 삭제한다.
* front(): 큐의 첫 번째 원소를 반한하되 큐 자체는 그대로 놔둔다.
* isEmpty(): 큐가 비어 있으면 true를, 그 외에는 false를 반환한다.
* size(): 큐의 원소 개수를 반환한다. 배열의 length와 같다.

# Queue 만들기

#### 큐의 기본 틀.
<pre><code>function queue() {
    var items = [];
}
</code></pre>

#### enqueue 메소드.
<pre><code>this.enqueue = function(element) {
    items.push(element)
}</code></pre>

#### dequeue 메소드.
<pre><code>this.dequeue = function() {
    return items.shift();
}</code></pre>

#### front 메소드.
<pre><code>this.front = function(element) {
    return items[0];
}</code></pre>

#### isEmpty 메소드.
<pre><code>this.isEmpty = function(element) {
    return items.length === 0;
}</code></pre>

#### size 메소드.
<pre><code>this.size = function(element) {
    return items.length;
}</code></pre>


### 전체 코드.
<pre><code>function queue() {
    var items = [];

    this.enqueue = function(element) {
        items.push(element)
    }

    this.dequeue = function() {
        return items.shift();
    }
    
    this.front = function(element) {
        return items[0];
    }
    
    this.isEmpty = function(element) {
        return items.length === 0;
    }

    this.size = function(element) {
        return items.length;
    }
}</code></pre>