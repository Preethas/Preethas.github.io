---
layout: post
title: "Linked List Using Typescript"
date: 2017-08-04
---

Linked list is a collection of nodes where every node has data and pointer to the next node. It is often compared to an array
as it can be used to implement other data structures like queue or stack .

<img src="https://preethas.github.io/assets/Linkedlist.png"/>

```Typescript
class ListNode {
  data:number;
  next:ListNode;
  
  constructor(data:number){
   this.data = data;
  }
  
  setNext(next:ListNode){
    this.next = next;
  }
  
  getNext(){
   return this.next;
  }

  getData() {
      return this.data;
  }
  
}

class LinkedList{
    head: ListNode = null;

    add(data: number) {
        if (this.head == null) {
            this.head = new ListNode(data);
        } else {
            var newNode = new ListNode(data);
            var current = this.head;
            while (current.getNext() != null) {
                current = current.getNext();
            }
            current.setNext(newNode);
        }
    }
    
    indexOf(data:number) {
      var found = false;
      var current = this.head;
      var index = 1;
      while (current != null && !found) {
        if (current.getData() == data){
          found = true;
          break;
        }else{
          current = current.getNext();
          index ++;
        }
      }
      return index;
    }
    
    elementAt(index:number){
     index = index-1;
     var current = this.head;
     var element = null;
     var cnt = 0;
     while (current != null){
       if (cnt == index){
        element=current.getData();
        break;
       } else{
        cnt++;
        current = current.getNext();
       }
     }
     return element;
    }
    
    remove(data:number){
      var current = this.head;
      if (current.getData() == data){
        this.head = this.head.getNext();
      } else{
        var prev = null;
        while(current != null && current.data != data){
          prev = current;
          current = current.getNext();
        }
        if (current  != null) {
         prev.setNext(current.getNext());
        }else{
         console.log("The data " + data +  "was not found");
        }
      }
    }
    
    size() {
      var current = this.head;
      var cnt = 0;
      while(current != null){
       cnt++;
       current = current.getNext();
      }
      return cnt;
    }

    print(){
      var current = this.head;
      var result = "";
      while(current != null){
        result += current.getData();
        if (current.getNext() != null)
        result += "-->";
        current = current.getNext();
      }
      console.log(result);
    }
}

var list = new LinkedList();
var arr = [100,200,300,400,500,600,700,800,900,1000];
arr.map(data => {
 list.add(data);
})

list.remove(5080);
list.print();
console.log("The size is "  + list.size());
console.log("The element at 4rth position : " + list.elementAt(4));
console.log("The index of 200 is " + list.indexOf(200));

 

```

