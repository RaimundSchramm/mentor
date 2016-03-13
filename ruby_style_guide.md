####Ruby Style Guide

In the words of Russ Olsen *Eloquent Ruby*:
> ... good code tells the reader exactly what it is trying to do. Great code shouts its intent.

Basically nothing I know yet is better than [bozhidars style guide](https://github.com/bbatsov/ruby-style-guide) which I use in general and adjust if necessary to my preferred style.

Besides I here try to come up with an own style guide. It should lead to nearly the same result.
---

##### Contents
- [1. General](#1-general)
  - [1.1 Indentation](#11-indentation)

---
#### 1. General
##### 1.1 Indentation
Indent each subordinated line of code by exactly two spaces. Also do not use tabs for this.

```ruby
1  class MyClass
2    attr_reader :my_attribute
3  end
```

```ruby
1  my_array = [
2    'I am',
3    'very long,
4    'so split me up over several lines' ]
```
Exception:

For readability I sometimes prefer a little difference in the following example.
```ruby
1  my_array = ['I am',
2              'very long,
3              'so split me up over several lines' ]
```
This can be ugly to handle if you try to vetically align this with different sizes or multiple parameters per line.
```ruby
1  my_array = ['I am',
2              'very long,
3              'so split me up over several lines' ]

1  my_array_with_a_longer_name = ['I am',
2                                 'very long,
3                                 'so split me up over several lines' ]

```
or in Gemfile
```ruby
gem 'some gem', 'version'
gem 'some gem with a very long name', 'version'
group :name do
  gem 'some gem with an even longer name', 'version'
end
```
vs
```ruby
gem 'some gem',                            'version'
gem 'some gem with a very long name',      'version'
group :name do
  gem 'some gem with an even longer name', 'version'
end
