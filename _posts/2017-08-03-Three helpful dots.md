---
layout: post
title: "Three helpful dots in ES6"
date: 2017-08-03
---

<h3> Spread operator </h3>

<p> With ES6 comes the spread operator that is helpful in many ways.The spread operator spreads an array into individual entries  </p>

<h5> Copying arrays </h5>

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

<hr>

<h5> Placing an array in a specific index within another array </h5>
<h6> Pre ES6 </h6>

<div class="code">
<p>var arr1 = [1,2,3,4,5];</p>
<p>var arr2 = [21,22];</p>
<p>var result = arr1.slice( 0, 2 ).concat( arr2 ).concat( arr1.slice( 2 ));</p>
</div>

<h6> ES6 </h6>

<div class="code">

</div>

<h5> Concat arrays </h5>


<h5> Call methods that have several parameters </h5>



