---
layout: post
title: "FW - RxJs and Cryptocurrencies"
description: "How the RxJs library is changing the web"
date: 2017-06-07
tags: [design, future web, webvr, angular]
comments: true
share: true
---

## CRYPTOS & RxJS

Since 2015 I have been very interested in purchasing Cryptocurrencies. During this time I have seen how almost all the sites that deal with Cryptocurrencies have to offer 'Real Time' information to their clients, it's critical for any exchange to provide this kind of reactive data service all the time.

And it's here where I discovered the reason why everybody is talking about 'reactive programming' and especially about the library Rxjs. 

Rxjs is not a new concept, it was first implemented nearly a decade ago (2009), stemming from ideas by Conal Elliott and Paul Hudak two decades ago (1997), in describing functional reactive animations (interesting). So it's really battle-tested.

## Observables - The heart of React Javascript

Instead of creating variables that change state in specific times a new concept called 'streams' is introduced. Streams allow to use lists ov values that change asynchronously over a period of time. These values can be anything: an array of numbers, strings or objects and they are called 'Observables'. 

Once the 'Stream/Observable' or blueprint ( it's basicaly like a class ) has been created you can later 'Subscribe' to it and activate it. To finalize you have to unsubscribe from it.

So when you are subscribed you recieve a stream of data that is updated in real time, and there resides its great power. Nowadays in Internet almost everything is reactive and in real time, so that means that allmost everything is or can be thought as a stream or as an Observable. Yes, this is the present and the future of the Internet right now.

It takes some time to 'pick up' how it works but once you understand the combinational possibilities they offer with their 'operators' the sky is the limit.

### Tutorials

Here I present you with 3 tutorials that I do believe are the best I have found about Observables.

1.[The introduction to Reactive Programming you've been missing](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754)

2.[This is a quick introduction into the concept of Reactive Programming in Angular with RxJS.](https://codecraft.tv/courses/angular/reactive-programming-with-rxjs/overview/)

3.[An Animated Intro to RxJS](https://css-tricks.com/animated-intro-rxjs/)


## Bitcoin and Ethereum PWA

To apply some of the possibilities that Observables bring to us I decided to make my own Progressive Web App with Angular2 about these
Cryptocurrencies that are surrounding us more and more. I have created a main page where I can update manually the trading values of the two main currencies: The bitcoin BTC and the Ethereum ETH.

At the same time I have created two more pages to show a more in depth amount of data about each of them, one for BTC and another ETH. All the values are bascially angular services that provide through subscription of the observables real time data based on different API's.

The result gives us a beautiful, simple and well design UX where I can see clearly and big exactly the data I'm interersted in real time.

> Final result: [RxJs and Cryptocurrencies App](https://bernatferragut.neocities.org/#/home)
> Final code: [RxJs and Cryptocurrencies github code](https://github.com/bernatferragut/cryptos)

### Rxjs

This is only the beginnng, I'm very excited to learn and create more with this new technology, this will be the bread and butter of the internet in the near future. I hope you got the interest to start investigating about it !

> [RxJs library](http://reactivex.io/)
