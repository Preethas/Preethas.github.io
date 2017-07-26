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

In order to understand how the java script event loop works refer to <a href="http://latentflip.com/loupe/">Loupe</a>
which helps us to visualise the scenario.

Suppose we want to measure the performance of a method

```javascript
    function x() {
       startTime = currTime();
       x1();
       setTimeout(x2,2000);
       timeToExecute = currTime() - startTime;
    }

```

The `timeToExecute`  will not measure the time taken for the method execution correctly  as the
async task in setTimeout is in a different context and will be placed on the call stack only after 
timeToExecute has been blown off the call stack.

This is where zone js comes to our rescue

If we wrap the function x within a zone context as below then the entire function runs within the same zone context
and it is possible to perform tasks in "hooks" specified in a zone specification.

```javascript
zone.fork(zoneSpecification).run(x);

```

<h3> Angular 1 Change Detection </h3>

Angular 1 forced us to use $scope.$apply to force DOM updation . Any changes done out of angular context 
(say in a setTimeout function) would not be reflected in the DOM as angular doesnt know that it had to update
the UI. Angular triggered the digest cycle as a result of asynchronous operations like $timeout , $http .

<iframe width="100%" height="300" src="//jsfiddle.net/pree888/qqymy5bn/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>


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

Zone js does a monkey patching of methods like setTimeout , setInterval and other events like click .

Angular 4 has its implementation of zone js called ngZone . The ngZone emits the onTurnDone event when
it completes an asynchronous operation.

Angular subscribes to the onTurnDone event of the zone and calls the `tick()` method which triggers the change detection.

<a href="https://github.com/angular/angular/blob/3dca9d522a79d037b3c2deba537ed547fc3f65b8/modules/angular2/src/core/application_ref.ts#L374"> Refer to the code here
</a>



<h3> Sample of zone js to intercept the click event  </h3>

<iframe width="100%" height="300" src="//jsfiddle.net/pree888/pv4a7pfj/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

<h3> Use cases for zone js </h3>

Zone js can be used to intercept methods to add additional logging , to come up with detailed error stack trace ,
for view rendering as in angular js , measuring performance of methods.







