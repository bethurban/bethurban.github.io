---
layout: post
title:      "What are Ruby arguments (and how can we use them)?"
date:       2019-08-16 15:26:27 +0000
permalink:  what_are_ruby_arguments_and_how_can_we_use_them
---


As a Flatiron School technical coach, I often see students confused about what Ruby method arguments are and how they can be used. Students have a tendency to want to hard-code, often using data that they've found in their test files, rather than using and operating on arguments. For example:

```
def add(1, 2)
  1 + 2
end
```

The above hard-codes the two arguments for the `add` method as `1` and `2` and then adds those two values together. The return value of the `add` method in this case will always be `3`.

Another hard-coding example:

```
def add(a, b)
  1 + 2
end
```

In this case, the student correctly defines argument names (`a` and `b`) — more on that in a minute — but doesn't operate on or use those arguments inside the method. In this case, the return value of the `add` method will still always be `3`.

One more hard-coding example:

```
def add(a, b)
  a = 1
  b = 2
  a + b
end
```

Here, the student has passed in argument names (`a` and `b`), but then reassigns those arguments' values by using `a = 1` and `b = 1`. Thus, even though the student is operating on `a` and `b` with `a + b`, the return value of this method will still always be `3` because `a` and `b` have been given hard-coded values inside the method.

## There is a better way!

A Ruby arguments allow you to pass values *that have not yet been defined* into methods. This makes methods much more versatile. We can write an `add` method that can take any two numbers in as arguments and deliver their sum as a return value. That makes that `add` method much more useful than a hard-coded `add` method that can only return `3`!

Argument names serve as placeholders for those undefined values. You can name your arguments anything you want, though it's a very good idea to give your arguments names that will help you remember the values that they'll stand for.

Examples of good argument naming:

```
def add(num1, num2)
  num1 + num2
end
```

```
def add_element(array, element)
  array.push(element)
end
```

```
def split_string(string)
  string.split(" ")
end
```

In the examples above, the arguments for each example method tell you the type of values that will be passed in when the methods are invoked. An argument named `num1` will stand for an integer, while an argument named `array` will represent an array of elements.

## Operating on and using arguments inside methods

The final piece to the Ruby arguments puzzle: Using them inside of your methods.

Since we know that the arguments that you've passed to a method represent data that will be provided to the method when it's invoked, we can operate on them the same way that we'd operate on the data itself.

If we have two arguments of `array` and `element`, for example, and we know that our method should add `element` to the end of `array`, we could write:

```
def add_element(array, element)
  array << element
end
```

As you see above, we're using the shovel operator (`<<`) on `array` and `element` just as if we were working with an actual array and element.

Say we had an array of letters and a letter that we wanted to add to the end of that array. We can use the above method to do that like so:

```
add_element(["a", "b", "c"], "d")
```

The return value would be: `["a", "b", "c", "d"]`.

When we invoke `add_element`, we give it the `array` (`["a", "b", "c"]`) and `element` (`"d"`) that we told it to expect when we defined the method and gave it arguments.

Because we used arguments and avoided hard-coding when we defined the `add_element` method, we can use it whenever we have an array and an element that we want to add to it — all we have to do is invoke `add_element` and pass in the array and element.

```
add_element([1, 2, 3], 4)
```

Return value: `[1, 2, 3, 4`








