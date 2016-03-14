####Ruby Style Guide

In the words of Russ Olsen *Eloquent Ruby*:
> ... good code tells the reader exactly what it is trying to do. Great code shouts its intent.

Basically nothing I know yet is better than [bozhidars style guide](https://github.com/bbatsov/ruby-style-guide) which I use in general and adjust if necessary to my preferred style.

Besides I here try to come up with an own style guide. It should lead to nearly the same result.

---

##### Contents
- [1. General](#1-general)
  - [1.1 Indentation](#11-indentation)
  - [1.2 Spacing](#12-spacing)
  - [1.3 Comments](#13-comments)

---

#### 1. General
##### 1.1 Indentation

a) Indent everything according to its scope and relatively to each other.
b) Indent each subordinated line of code by exactly two spaces. Also do not use tabs for this.

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
```

---

##### 1.2 Spacing

Put a new line between semantically different statement

```ruby
gem 'gem for each environment',            'version'
gem 'another for each environment',        'version'

group :gems_for_this_specific_environment do
  gem 'some gem with an even longer name', 'version'
end
```

***

##### 1.3 Comments

In a perfect world the code is completely easy to read and understand. Therefore no comments would be needed.
From my experience unless you are very familiar with Ruby (or any other language) you will have difficulties understanding
good written code. And if you understand even badly written code than you still have to understand its semantically meaning
inside the domain it is written for.

So judge what is not human readable and clear for a domain newby and put an explaining comment there.

```ruby
class MyClass

  # calculates the price of items under that condition
  def my_elegant_method
    ...here is the best code you have ever seen
  end

end
```

###
