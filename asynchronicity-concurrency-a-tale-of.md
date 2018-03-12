# Asynchronicity: concurrency. A tale of

_(a.k.a: the subtle art of making a PB&J sandwich)_ by **Joel Lord** _@joel__lord_

**PHP** tends to be very synchronous.

**Javascript** tends to be very asynchronous.



## Slides

This talk was heavily reliant on really well made slides.

https://javascripteverything.com/slides/async-confoo.pdf



## Event Loop

### Classic architecture (PHP, Java)

Everything get's its own thread (new process).

## Callbacks

A function passed as an argument to another function. Could be synchronous or asynchronous.

## Promises

Representation of a callback.

## Generators

Yield a value in the middle of the function (creates an Iterable).

## Async/Await

Combination of Promises and Generators

## Reactive Stream