---
layout: post
title:  Meteor was great
subtitle: but I'm back to Earth
date:   2016-03-01
categories: meteor blaze
---

Yes, it's been a while, but I'm back. I was completely consumed by the work in a startup called Onist, where I was doing full-stack JS using Meteor, Node and Redis.

Now that I'm back to RESTfull APIs, sane client-side JS and good old angular, I can take a moment to reflect on my experience with Meteor.

Meteor is amazing! 

- Full stack JS
- [Tracker](https://www.meteor.com/tracker) (genius idea!)
- [DDP](https://www.meteor.com/ddp)
- Fibers on the server
- Code reuse across client and server
- Observing DB changes (mongo)

But there are few challenges with Meter (and some are really annoying):

- global namespace
- proprietary packaging system (as opposed to NPM) 
- no unit-testing infrastructure
- blaze framework
- hard to control reactive updates

(Some of it are changing as we speak, which is great...)

Lets look into some of these...

### Global namespace

Well, there is not much to say bout this. Its just bad. First of all, it forces you to use really long names for your entities. But the most importantly - its really hard to test. Every time you want to test a component you have to recreate (mock) all the global dependencies! 

### NPM

While its possible to use NPM with meteor, its really cumbersome, and meteor's own packaging is nothing like NPM. Meteor's own [package repository](https://atmospherejs.com) hosts adopted versions of some NPM packages, but they are always few versions behind. Fortunately MDG has recognized this (after long and continuous resistance), and NPM will be supported as a first class citizen.

### No unit-testing infrastructure
 
This is probably the most annoying thing about Meteor. Its actually unbelievable that an engineering masterpiece such as Meteor wasn't built with unit testing in mind. Globally scoped dependencies makes it even harder to unit test anything. Fortunately JS is very dynamic, and lets you work around this obstacle by mocking global dependencies. I might talk more about it in my next blog. 

### Blaze UI framework

Blaze is pretty powerful, very flexible and lets you build UI with reusable components very fast. Unfortunately as the hierarchy of blaze components grow, its really hard to understand whats going on especially given the reactive nature of Meteor. Blaze API is also very confusing with a lot of different ways to do the same thing. And some simple things are hard to do, like sharing state across components. Fortunately Blaze is being replaced with more mature alternatives like React or Angular.  

### Hard to control reactive updates

Reactive state changes are unpredictable, which might be not what you want your user's experience to be. On one hand, its pretty powerful to update your UI reactively when state changes on the backend, but on the other, you have to build some kind of UX to not surprise your user with unexpected updates.

### Conclusion 
Meteor is very powerful, and as you know, with great power comes great responsibility. 
You can build powerful things with Meteor, but it requires a skill to make those powerful things elegant and maintainable.
