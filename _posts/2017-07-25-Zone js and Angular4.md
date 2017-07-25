---
layout: post
title: "Zone js and Angular 4"
date: 2017-07-25
---

<h3> What is zone js</h3>

<i>Zone js is an execution context that persists across async tasks</i>

Java script is single threaded by nature , ie it can run only one command at a time .

The commands are stored in the call stack . However the asynchronous operations are not a part of the call stack 

When the async operations are resolved , they take their place in the event queue . The event loop polls the event queue 
for new entries and places them in the call stack <b>if and only if the call stack is empty </b>.

Methods are thrown off the call stack post execution.

Suppose we want to measure the performance of a method

```javascript
    function x() {
       startTime = currTime();
       x1();
       setTimeout(x2,2000);
       timeToExecute = currTime() - startTime;
    }

```

The `timeToExecute` method will not measure the time taken for the method execution correctly  as the
async task in setTimeout is in a different context and will be placed on the call stack only after 
timeToExecute has been blown off the call stack.

This is where zone js comes to our rescue

If we wrap the function x within a zone context as below then the entire function runs within the same zone context
and it is possible to perform tasks in "hooks" specified in a zone specification.

```javascript
zone.fork(zoneSpecification).run(x);

```

<h3> Angular 4 and Zone js </h3>

Angular js offers two way binding , when the data is updated the view gets updated automatically and vice versa.
It does this by a change detection mechanism which tells angular when the DOM needs to be updated.

A change detection is required in one of the following cases

<ul>
  <li> As the result of an XHR request to a server to fetch data </li>
  <li> As the result of an event - say click event </li>
  <li> As a result of calling setTimeout or setInterval </li>
</ul>

All  these 3 cases are asynchronous and when they happen angular needs to fire the DOM update .


  
  
  






