---
layout: post
title:      "Looping through arrays using `for` in JavaScript"
date:       2019-08-23 21:07:17 +0000
permalink:  looping_through_arrays_using_for_in_javascript
---


The `for` loop is a simple way to iterate over each element of an array. The following code will `console.log` each element in `array`.

```
var array = ["a", "b", "c"]

for (let i = 0; i < array.length; i++) {
  console.log(array[i])
}

// Logged:
"a"
"b"
"c"
```

## Syntax

`for` takes three arguments: an initializer, a condition and an incrementer:

```
for ( initializer; condition; incrementer)
```

A common pattern is to set `i` (or any variable name you'd like to use) to `0` as the initializer:

```
for (let i = 0;
```

Then set the condition to `i < array.length` — which tells the `for` loop to run as long as the value of `i` is less than the length of `array`:

```
for (let i = 0; i < array.length;
```

Then set the incrementer to `i++`, which will increment the value of `i` by one on each loop:

```
for (let i = 0; i < array.length; i++) {
  // code goes here
}
```

In the above example, if `array` has three elements, the loop will run three times. On the first loop, `i` will equal `0`, and `i` will be less than `array.length`. On the second loop, `i` will be `1`, and it will still be less than `array.length`. On the third loop, `i` will be `2`, and it will still be less than `array.length`.

On the fourth loop, `i` will be `3`, and it will no longer be less than `array.length`, so the loop will stop running and exit.

## Using `i` inside the loop

When iterating over an array, the value of `i` on each loop can be used to pull each element from the array and operate on it. Since `i` in our example will start at `0` and increase by one on each loop, calling `array[i]` inside the loop will start by pulling the first element (`array[i]` will equal `array[0]`) and then pull the next element as `i`'s value increases on each loop.

Example - takes an array of numbers and `console.log`s each number plus `10`:

```
var numbers = [1, 2, 3, 4]

for (let i = 0; i < numbers.length; i++) {
  console.log(numbers[i] + 10)
}

// Logged:
11
12
13
14
```


