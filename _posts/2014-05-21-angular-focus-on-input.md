---
layout: post
title:  How to enable 'focus' in Angularjs forms
tagline:  
date:   2014-05-21 10:00:00
categories: angularjs
---

Surprisingly there is no built-in angular directive for focusing in form fields.
But its pretty trivial to create one:

```js
function focus(){
  return {
    link: function(scope, element) {
      element[0].focus();
    }
  };
}
```

And use it like this:

```html
<input type="text" name="address" focus>
```

The example above will focus on load. But what if you need to focus on condition, say when the form becoms visible?
We can add a boolean `@` attribute to our directive to comminucate when to focus. But there is a little catch: we need to use `timeout()` to call `focus()`.

