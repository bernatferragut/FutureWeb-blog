---
layout: post
title: "FW - RxJs and Cryptocurrencies"
description: "How the RxJs library is changing the web"
date: 2017-06-07
tags: [design, future web, webvr, angular]
comments: true
share: true
---

# CRYPTOS & RxJS

Lately I have been very interested in purchasing Cryptocurrencies. During this time I have seen how almost all the sites that deal with Cryptos they have to offer Real-Time information to their clients, it's critical for any exchange to provide this kind of reactive data all the time.

And it's here where I discovered the reason why now everybody is talking about reactive programming and specifically about the library Rxjs. 

Rxjs is not a new concept, it was invented during the 90's by "" and "" on the paper called "" about Reactive animations. So it's a way of thinking that has been very well tested over time.

# Observables - The heart of React Javascript

Instead of creating variables that change state in specific times a new concept called streams is introduced,which allows to use lists ov values that change asyncronously over time. This values can be anything, an array of numbers, strings, objects and they are called Observavles. 

Once the 'Stream/Observable' or blueprint ( it's basicaly like a class ) has been created you can later Subscribe to it to activate it or unsuscribe to go out of it.

That way when you are suscribed you have a stream of data being updated in real time, and there you have the great power of it. Nowadays in Internet almost everything is reactive and in real time, so that means that allmost everything are or can be thought as streams or Observables. Yes, this is the present and the future of the Internet right now.

It takes some time to pick up how they work but once you understand the combinational possibilities they offer with their 'operators' the sky is the limit.

## Tutorials

Here I present you with 3 tutorials that I do believe are the best I have found about Observables.

1. All you needed to know about Observables
2. A short but very well explained introduction to Observables with Angular2
3. A cvery interesting combination of Observables and Animations

# Bitcoin and Ethereum PWA

To apply some of the possibilities that Observables bring to us I decided to make my own Progressive Web App with Angular2 about these
Cryptocurrencies that are surrounding us more and more. I have created a main page where I can update manually the trading values of the two main currencies: The bitcoin BTC and the Ethereum ETH.

At the same time I have created two more pages to show a more in depth amount of data about each of them, one for BTC and another ETH. All the values are bascially angular services that provide through subscription of the observables real time data based on different API's.

The result gives us a beautiful, simple and well design UX where I can see clearly and big exactly the data I'm interersted in real time.

> You can see the fina l result here : "" web
> And the code for it is here.

## Rxjs

This is only the beginnng, I'm very excited to learn and create more with this new technology, this will be the bread and butter of the internet in the near future. I hope you got the interest to start investigating about it !
