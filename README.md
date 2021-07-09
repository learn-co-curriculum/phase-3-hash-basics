# Hash Basics

## Learning Goals

- Define a hash in Ruby
- Use common methods to work with hashes

## Introduction

You've already encountered Ruby hashes and learned some of their characteristics
in the lesson on Ruby data types. As a refresher:

Hashes are Ruby's equivalent of a plain old JavaScript object. They are composed
of key/value pairs. Each key points to a specific value, just like a word and a
definition in a regular dictionary.

In this lesson, we'll explore hashes in more detail, and discuss what makes a
hash in Ruby distinct from an object in JavaScript. Make sure to follow along
with the examples using IRB.

## Creating a Hash

There are a few ways of writing hashes. You can create a hash by simply writing
key/value pairs enclosed in curly braces:

```rb
{ key1: "value1", key2: "value2" }
```

Using the JSON-style syntax above will create a hash with **Symbols** for keys.
To access data from this hash, you can use the bracket notation and pass in the
symbol for they key you are trying to access:

```rb
my_hash = { key1: "value1", key2: "value2" }
my_hash[:key2]
# => "value2"
```

Trying to access a key that does not exist will return `nil`:

```rb
my_hash[:key3]
# => nil
```

You can also use the bracket notation to assign a new value to a key:

```rb
my_hash[:key2] = 42
my_hash
# => {:key1=>"value1", :key2=>42}
```

Or to assign a new key-value pair:

```rb
my_hash[:key3] = true
my_hash
# => {:key1=>"value1", :key2=>42, :key3=>true}
```

Unlike JavaScript, you cannot use the dot notation to access keys on hashes
&mdash; only the bracket notation will work:

```rb
my_hash = { key1: "value1", key2: "value2" }
my_hash.key2
# NoMethodError (undefined method `key2' for {:key1=>"value1", :key2=>"value2"}:Hash)
```

This is because dot notation has a different meaning in Ruby &mdash; dot
notation is only used for calling _methods_ on objects, which is why the code
above throws a `NoMethodError`.

> Even the "bracket notation" used for Hashes and Arrays in Ruby are technically
> methods defined on those classes! `my_hash[:key2]` is syntactic sugar (a nicer
> way of writing) the same thing as a method call: `my_hash.[](:key2)`.

You can also create hashes with Strings for keys:

```rb
{ "i'm a key" => "i'm a value!", "key2" => "value2" }
```

This syntax is known as the **hash rocket** syntax, and is useful if you need
String keys for Symbols; however, in general, using Symbols for keys is
preferred.

Like JavaScript, you can also create **nested** hashes in Ruby, which can be
useful to represent complex data structures:

```rb
user = {
  name: "Duane",
  address: {
    street: "123 Fake Street",
    city: "Queens",
    state: "NY"
  }
}
user[:address][:city]
# => "Queens"
```

## Common Hash Methods

Ruby has a few common methods for working with hashes. In addition to using
bracket notation to access values, you can also delete values from a hash with
the delete method by passing in a key:

```rb
pizza_toppings = { cheese: true, topping1: "mushroom", topping2: "sausage" }
pizza_toppings.delete(:topping2)
pizza_toppings
# => {:cheese=>true, :topping1=>"mushroom"}
```

It also has methods for accessing an array of all the keys or an array of all
the values, similar to JavaScript's `Object.keys` and `Object.values` methods:

```rb
pizza_toppings.keys
# => [:cheese, :topping1]
pizza_toppings.values
# => [true, "mushroom"]
```

It has the `#empty?` method to check if there are no key-value pairs defined on
the hash:

```rb
pizza_toppings.empty?
# => false
{}.empty?
# => true
```

Lastly, it has the `#merge` method to join together multiple hashes:

```rb
more_toppings = { topping2: "peppers", topping3: "onions" }
pizza_toppings.merge(more_toppings)
# => {:cheese=>true, :topping1=>"mushroom", :topping2=>"peppers", :topping3=>"onions"}
```

We'll explore a few more methods you can use with hashes to iterate over all the
key-value pairs in upcoming lessons, but you can also view all the methods in
the [Ruby Hash documentation][hash docs].

## Conclusion

Hashes are one of the most common data structures you'll work with in Ruby,
along with Arrays. You've already seen what kind of scenarios you'd use objects
in JavaScript, so you should be comfortable using hashes in similar situations
in your Ruby code. Keep the documentation handy so you can take advantage of
some of the special methods Ruby has to offer as well!

## Resources

- [Hash documentation][hash docs]

[hash docs]: https://ruby-doc.org/core-2.7.3/Hash.html
