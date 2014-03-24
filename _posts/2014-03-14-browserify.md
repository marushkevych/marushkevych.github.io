---
layout: post
title:  "Browserify"
date:   2014-03-14 17:00:00
categories: angularjs
---

Last few days I was trying to come up with easiest way to manage packages and dependencies in AngularJS projects. 
I discovered [Browserify](http://browserify.org) and its awesome cause it allows you to use `npm` and node style 'require' in your code.

Here is what I'm going to try:

- use [grunt-maven-tasks](https://www.npmjs.org/package/grunt-maven-tasks) to publish JS packages to maven
- use npm to install packages from maven
- use browserify to import those packages in angular project

Also [here](https://groups.google.com/forum/#!starred/angular/ytoVaikOcCs) is interesting approach to decoupling from angular modules.

Yet a better way to decouple is to declare components as pure functions:

```js
function PhoneListCtrl($scope, $http) {...}
PhoneListCtrl.$inject = ['$scope', '$http'];
module.exports.PhoneListCtrl = PhoneListCtrl;
```

And then later

```js
var PhoneListCtrl = require('PhoneListCtrl');
App.controller('PhoneListCtrl', PhoneListCtrl);
```
