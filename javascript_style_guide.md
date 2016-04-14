### Javascript Style Guide

#### Contents

- [Best Practices](#best-practices)
  - [Closures](#closures)
- [Frameworks](#frameworks)
  - [Angular](#angular)

-

#### Best Practices

This section focusses on recommendations of how to write and arrange clean javascript-code.

###### Closures

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

#### Frameworks

##### Angular

An Angular Directive is a marker on an HTML element that tells Angular to run or reference JS code.
An Angular Module capsules pieces of the application and can manage Dependencies.
An Angular Expression is evaluated Javascript inside HTML-elements contained by an Angular app.
