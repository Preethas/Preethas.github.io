---
layout: post
title: "How to think recursively"
date: 2017-10-05
---

<h3>How to think recursively</h3>

Recursion is when a function calls itself . I knew I had to use it when I wanted to traverse a binary tree , I knew I had to use it to compute factorial . After my first encounter with Functional Programming I realised that recursion was used to replace loops as loops were mutable and Functional Programming advocates immutability.
Though not a Functional Programming concept , recursion is used in Functional Programming to replace loops . Then I figured out that any logic that made use of a loop could be made into a recursive function.

Think of how we would write a program to compute sum of the numbers in a list.

```
int sum(int[] list) {
  int total = 0; // Clearly total is mutable
  for (int n:list)  total += n;
  return total;
}
```
How can we write the same program without using the “for loop”

Here is the code in java

```
int sumRecursive(int total,List<Integer> list){
  return (list.size()>0) ?
  sumRecursive(list.get(0) + total,list.subList(1, list.size()))
                                                          :   total;
}
```


<img src="https://preethas.github.io/assets/Recursion.png"/>

Imagine we passed this function to another developer to call
The first question would be “What do I pass to total ?” Ideally it should be 0 .
What happens if I pass some other value ? The function wouldn’t work as expected.

Fortunately this problem has an easy solution . We wrap the recursive function with another function.

```
sum(int[] list){
  sumRecursive(0,list);
}
```

Many functions on collections can be written recursively . Here are a few examples .

<b>Counting the number of elements in a list</b>

<script src="https://gist.github.com/Preethas/883b79625eebf43e288fd78985c8329b.js"></script>

<b>Searching for an item in a list</b>

<script src="https://gist.github.com/Preethas/2c4af6e25dceadb1d77c442f83346782.js"></script>

<b> Finding the last item in a list </b>

<script src="https://gist.github.com/Preethas/9d1159e5ece79926d94b0b757d4bcc0a.js"></script>





