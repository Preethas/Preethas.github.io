---
layout: post
title: "Three helpful dots in ES6"
date: 2017-08-03
---

<h3> Spread operator </h3>

<p> With ES6 comes the spread operator that is helpful in many ways.The spread operator spreads an array into individual entries  </p>

<h3> Copying arrays </h3>

<h6> Pre ES6 </h6>

<div class="code">

<p>var arr = [1,2,3]; </p>
<p>var copy  = arr.slice();</p>

</div>

<h6> ES6 </h6>

<div class="code">

<p>var arr = [1,2,3]; </p>
<p>var copy  = [...arr]</p>

</div>


<h3> Placing an array in a specific index within another array </h3>
<h6> Pre ES6 </h6>

<div class="code">
<p>var arr1 = [1,2,3,4,5];</p>
<p>var arr2 = [21,22];</p>
<p>var result = arr1.slice( 0, 2 ).concat( arr2 ).concat( arr1.slice( 2 ));</p>
</div>

<h6> ES6 </h6>

<div class="code">
  var result = [1,2,...arr,3,4];
</div>

<h3> Concat arrays </h3>

<h6> Pre ES6 </h6>

<div class="code">
  var arr3 = arr1.concat(arr2);
</div>

<h6> ES6 </h6>

<div class="code">
  var arr3 = [...arr1,...arr2];
</div>

<h3> Call methods that have several parameters </h3>

<h6> ES6 </h6>

<div class="code">
<p>function a(param1,param2,param3) {</p>
  
<p>}</p>
<p> var arr = [param1,param2,param3]; </p>
<p> a(...arr); </p>
</div>


<iframe width="100%" height="300" src="//jsfiddle.net/pree888/f53hc7Lj/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>


