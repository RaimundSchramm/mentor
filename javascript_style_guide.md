### Javascript Style Guide

#### Contents

- [Closures](#closures)

##### Closures

I still don't get it. From my last reading, I suppose a closure in Javascript is an implicit language feature which results from having a function using a local variable which has the same name as a local variable of a parent scope, for example

```javascript
var outer = 'something'
function() {
  alert(outer);
};
```

Use cases where closures are useful seem to be when the function that uses the inner variable with the value of the outer scope needs to run after it has been run before, for exampe the single time it is run on page load.

By not using this technique correctly there can be memory leaks or just not necessarily running code.

-
