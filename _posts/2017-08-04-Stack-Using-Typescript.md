---
layout: post
title: "Stack Using Typescript"
date: 2017-08-04
---

Stack is a last in first out (LIFO)  data structure . The last item to be pushed into the stack will be the first
item to be retrieved. It resembles a pile of books . The common operations in a stack are push and pop.

<img src="https://preethas.github.io/assets/Stack-structure.png"/>

```Typescript

class Stack {

  data: any[];
  count: number = 0;
  size: number = 10;

  constructor(){
   this.data = new Array(this.size);
  }
  
  constructor(size: number) {
    this.size = size;
    this.data = new Array(size);
  }

  push(item: any) {
    if (this.count < this.size) {
      this.data[this.count] = item;
      this.count++;
    } else {
      console.log("The stack is full");
    }
  }

  pop() {
    if (!this.isEmpty()) {
      const index = this.count - 1;
      const value = this.data[index];
      this.count--;
      return value;
    }
  }

  sizeOfStack() {
    return this.count;
  }

  isEmpty() {
    return this.count == 0;
  }

  print() {
    this.data.map(item => {
      console.log(item);
    })
  }

}




```

<iframe width="100%" height="300" src="//jsfiddle.net/pree888/846x2qo7/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>
