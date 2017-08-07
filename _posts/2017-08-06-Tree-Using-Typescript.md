---
layout: post
title: "Tree Using Typescript"
date: 2017-08-06
---


<h3> Binary Search Tree </h3>

A tree is a collection of nodes , where every node can have one or more child nodes . Root node
is present at the top of the tree.

<img src="https://preethas.github.io/assets/Tree.png"/>

A binary search tree is a tree where each node can have 0 , 1 or 2 children.

For each node the element on its left will be less than the current node and the element on the
right will be greater than the current node.

<ul>

<li> A tree is a full binary tree if every node has exactly 2 children and all the leaf nodes are at the same level </li>
<li> The number of nodes in a full binary tree is 2^ (h + 1) - 1 . Since there are h levels we need to add the nodes
at all levels [2^0 + 2^1 + 2^2 + ...2^h] which is 2^ (h + 1) - 1 </li>
<li> There are 6 different ways in which a tree can be traversed , but since the classification depends on the position
of the current node , this resolves to 3 ways </li>
<li> Preorder (DLR) traversal </li>
<li> Inorder (LDR) traversal </li>
<li> Postorder (LRD) traversal </li>
<li> There is another traversal called Level Order Traversal which drew its inspiration from Breadth First Search </li>
<ul>

<h4> Level order traversal </h4>

```Typescript

levelOrderTraversal(root:Node,result:[]) {
     var queue = [];
     queue.push(root);
     while(queue.length>0){
       var temp = queue.shift();
       result.push(temp.data);
       if (temp.left)  queue.push(temp.left);
       if (temp.right) queue.push(temp.right);
     }
    }
```

<iframe width="100%" height="300" src="//jsfiddle.net/pree888/oxt0wd9f/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>
