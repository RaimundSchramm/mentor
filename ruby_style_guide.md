####Ruby Style Guide

...please fill me with guidance and best practices...

Basically nothing I know yet is better than [bozhidars style guide](https://github.com/bbatsov/ruby-style-guide) which I use in general and adjust if necessary to my preferred style.

Besides I here try to come up with an own style guide. It should lead to nearly the same result.

##### Contents
- [General](#general)

##### General

- indent each subordinated line of code by exactly two spaces

```
1  class MyClass
2    attr_reader :my_attribute
3  end
```

```
1  my_array = [
2    'I am',
2    'very long,
3    'so split me up over several lines' ]
```
or
```
1  my_array = ['I am',
2              'very long,
3              'so split me up over several lines' ]
```
