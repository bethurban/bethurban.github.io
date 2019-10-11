---
layout: post
title:      "Still a little confused about Ruby arguments?"
date:       2019-10-11 19:08:30 +0000
permalink:  still_a_little_confused_about_ruby_arguments
---


## Let's build a simple calculator to help!

Ruby arguments represent values that are passed into methods when the methods are run. They allow objects like strings, integers, arrays and hashes to be given to the method so that the method can operate with them. Arguments also make methods *flexible* — they allow a method to be run with different values that are always operated on in the same way.

A great example is a calculator method.

### Basic addition calculator

Let's say you want a method that will act as an addition calculator. It will add together *any* two numbers that you give it and return the sum. The two numbers that will be added will be passed into the method via arguments.

```
def add(number1, number2)
  number1 + number2
end
```

In the code above, the `add` method accepts two arguments: `number1` and `number2`. Those arguments represent the numbers that `add` will be called with. Inside the method, the arguments are added together, and the method will return their sum.

Here's how this method can be used:

```
add(1, 2)
  => 3

add(3,5)
  => 8

add(10,20)
  =>30

add(250, 250)
  =>500
```

In the code above, the `add` method is run four times, each time with different numbers. When we defined the method, we told `add` to expect to be given two numbers to operate on by giving it the `number1` and `number2` arguments. Those arguments were *placeholders* for the numbers that `add` would be given when it ran.

### Try it yourself

In your terminal, enter `irb` to start a new Interactive Ruby session, which will allow you to test out and play around with Ruby.

Enter in our method definition:

```
def add(number1, number2)
  number1 + number2
end
```

Now, run the `add` method to see what the sum of `237` and `916` is. (Hint: If you're not sure how to run the method and get that sum, check out the examples above.)

Run the method again, this time passing in any two numbers that you'd like. As you can see, the method will return a different value each time, because its return value is entirely based on the arguments that you give it.

When you're done, you can run `exit` to end the IRB session.


