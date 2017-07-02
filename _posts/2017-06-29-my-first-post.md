---
layout: post
title: "Rx JS"
date: 2017-06-29
---

<h3> What is Reactive Programming </h3>

Reactive programming is a programming paradigm that help us to work on streams of data. The stream could be a series of mouse events , data arriving from a network request or even as simple as an array of integers.

When we talk about data there will always be a sender and a receiver , In reactive programming they are known as a publisher and consumer . Reactive programming deals about moving the data from the publisher to the consumer without having to worry about the details of how its being done. In other words <b> declarative </b> style of programming is used.

Rx programming model was developed in Microsoft and has implementations in many languages which include java,scala , java script . This blog will talk about the javascript implentation Rx Js.

<h3> Inspiration </h3>

Long long ago when the GOF design patterns was conceptualised , no one ever thought that the observer and the iterator patterns were related to each other as shown be the diagram  <a href="http://idiotechie.com/gang-of-four-gof-design-pattern"/> here </a>

But then after several years people started realising the symmetry between both the patterns.

Both the patterns deal with data . In the observer pattern which we generally associate with events (mouse click , key press etc ) the publisher of the event is in control . The consumer has no control over whether the event will even happen or the amount of data that it will produce.The model is a <b> push model </model> with the publisher pushing data to the consumer

The iterator design pattern commonly used to iterate over collections , the consumer is in control . The consumer invokes the next() method to pull data from the publisher until a) there are no more elements in the collection b) an error occurs

When the symmetry was noticed people came up with the idea of Reactive programming where it was able to have a common interface to deal with pushed data (like data coming from events , data from a request over the network , web sockets)
and static data like arrays .

<h3> Rx Js api </h3>

The Rx Js api is available <a href="https://www.learnrxjs.io">here</a>

<h3> Applications </h3>





Rx JS 
<iframe width="100%" height="300" src="https://jsfiddle.net/pree888/vLxxe5rn/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

Hot and Cold Observables


Inspiration
