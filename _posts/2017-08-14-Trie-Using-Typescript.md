---
layout: post
title: "Trie Using Typescript"
date: 2017-08-14
---


<h3> What ia a Trie ? </h3>

A Trie is a tree structure commonly used for storing words in a compact way. Unlike a tree , the trie is a representation of a sequence rather than a single entity.

A Trie Node contains a Map . The keys are the characters and the value is another Trie Node .
Each node also has a boolean value that determines if the Node represents the end of the word. The node which has 
this boolean set to true is known as a leaf node.

Traversing the Trie from the root node to the leaf node results in a word .

A common application of a Trie is the autocomplete dictionary as searching in a Trie is very fast and requires O(m) time where
m is the length of the word.






<iframe width="100%" height="300" src="//jsfiddle.net/pree888/ofoukg0o/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

