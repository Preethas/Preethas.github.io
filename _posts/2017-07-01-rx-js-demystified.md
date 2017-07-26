---
layout: post
title: "Rx JS Demystified"
date: 2017-07-01
---

<h3> What is Reactive Programming </h3>

Reactive programming is a programming paradigm that help us to work on streams of data. The stream could be a series of mouse events , data arriving from a network request or even as simple as an array of integers.

When we talk about data there will always be a sender and a receiver , In reactive programming they are known as a publisher and consumer . Reactive programming deals about moving the data from the publisher to the consumer without having to worry about the details of how its being done. In other words <b> declarative </b> style of programming is used.

Rx programming model was developed in Microsoft and has implementations in many languages which include java,scala , java script . This blog will talk about the javascript implentation Rx Js.

<h3> Inspiration </h3>

Long long ago when the GOF design patterns was conceptualised , no one ever thought that the observer and the iterator patterns were related to each other as shown be the diagram  <a href="http://idiotechie.com/gang-of-four-gof-design-pattern"> here </a>

But then after several years people started realising the symmetry between both the patterns.

Both the patterns deal with data . In the observer pattern which we generally associate with events (mouse click , key press etc ) the publisher of the event is in control . The consumer has no control over whether the event will even happen or the amount of data that it will produce.The model is a <b> push model </b> with the publisher pushing data to the consumer

The iterator design pattern commonly used to iterate over collections , <b> the consumer is in control </b> . The consumer invokes the next() method to pull data from the publisher until 
<ul>
<li> a) there are no more elements in the collection </li>
<li> b) an error occurs </li>
</ul>

When the symmetry was noticed people came up with the idea of Reactive programming where it was able to have a common interface to deal with pushed data (like data coming from events , data from a request over the network , web sockets)
and static data like arrays .

The Observable is central to the Rx pattern but instead of the consumer requesting values from the publisher (as in the iterator) the observable pushes values to the observer as soon as it is available . Its like saying <i> "Dont call us , we'll call you " </i>

<h3> Rx Js api </h3>

The Rx Js api is available <a href="https://www.learnrxjs.io">here</a>

<h3> Applications </h3>

<b> A very basic example of Rx Js used in search </b>

Observables can be created from events , promises or even plain arrays .
<ul>
<li> Here we create an observable out of the key up event </li>
<li> The event is 'debounced' , instead of tracking all the keyup events , these events are tracked once in 3 seconds . </li>
<li> Map function projects the event into the value entered in the text box. </li>
<li> Filter helps to filter out those events when the user has entered a value greater than or equal to a length of 3 . </li>
<li> DistinctUntilChanged captures distinct text values , thus ignores events where the current value of the input equals the previous value.</li>
<li> Map function calls the searchFor which is a dummy function that returns an array of values to simulate a network query.</li>
</ul>

<div class="code">   

Rx.Observable.fromEvent(q, 'keyup')
                   .debounce(() => Rx.Observable.timer(3000))
                   .map(function (ev) { return ev.target.value; })
                   .filter(function (text) { return text.length >= 3; })
                   .distinctUntilChanged()
                   .map(searchFor)

</div>

<iframe width="100%" height="300" src="//jsfiddle.net/pree888/b3Los8j5/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>



<b> Autocomplete using switchMap </b>

Problems while implementing an autocomplete

<ul>
<li> The results fetched over a network query does not match the data typed in by the user . If the user types in ab , the network request will be sent once for a and then for b . But if the response is late then we get the result for 'a' , which will be set to the results instead of that for 'ab'.</li>
</ul>

<b> switchMap </b> comes to our rescue here . This function ensures that the result matches thelast text typed in by the user.

<iframe width="100%" height="300" src="https://jsfiddle.net/pree888/vLxxe5rn/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

<b> Rx Js with Promises </b>

An Observable can be created from Promise . It can have multiple subscribers as shown in the example below.
Note that 'Init Observable' will be called only once despite the observable having multiple subscriber



<iframe width="100%" height="300" src="//jsfiddle.net/pree888/7eczw2hb/8/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

<img src="https://preethas.github.io/assets/test.png"/>

