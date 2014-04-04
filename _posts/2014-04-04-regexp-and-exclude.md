---
layout: post
title:  Regular Expressions with exclusions and "and" conditions
date:   2014-04-04 10:00:00
categories: angularjs javascript regexp
---
In my [previous](/2014/03/26/angular-html5mode-refresh.html) post i mentioned connect-modrewrite middleware, 
which can be use to handle browser refresh button in angular app. When I was trying to implement regexp for modrewrite, 
I foung it was really challenging to have regular expression with exclusions and "and" conditions.

The solution is to use inverted conditions and the negate the whole expression. 
Here is the example: Say you need to configure rewrite rule for all request starting with `/fr` and not containing `.js` extention.
So the way to do it is to create invert refular expression

```js
// not starting wiht /fr or containing .js
"^/(?!fr)|\\.js$"
```

And then negate it in the modrewrite rule:

```js
modRewrite([
    '!^/(?!fr)\\.js$ /fr/index.html [L]'
]),
```
