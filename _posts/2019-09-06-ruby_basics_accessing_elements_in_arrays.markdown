---
layout: post
title:      "Ruby basics: Accessing elements in arrays"
date:       2019-09-06 21:08:31 +0000
permalink:  ruby_basics_accessing_elements_in_arrays
---


## What is an array?
According to Ruby-Doc.org, arrays are "[ordered, integer-indexed collections of any object](https://ruby-doc.org/core-2.4.1/Array.html)." An array can be a collection of strings, integers, etc., and the array syntax is the elements of an array arranged between square brackets, separated by commas:

```
# Array of strings:
["a", "b", "c", "d"]

#Array of integers:
[1, 2, 3, 4]
```

## Array indexing
The elements in every array are numbered by the order that they appear in the array, and each element's number is called its **index**. The first element in any array starts with an index of **0**, and the indexes count up for each subsequent element.

Note: Since the first element of an array has an index of `0`, that means the second element's index is `1`, the third element's index is `2`, and so on.

## Accessing array elements using indexes
Pulling a specific element out of an array is easy using index numbers. You simply call the square brackets (`[ ]`) on the array with the index number of the element that you'd like in between.

For example, say you had a variable of `letters` defined as this array: `["a", "b", "c", "d", "e"]`. If you wanted to see the second element in `letters`, you'd run:

```
letters[1]
```

*Remember that the second element has an index of `1` since indexes start at `0`.*

The result of the above code would be `"b"`, or the second element in the `letters` array.

Another example:

```
[10, 9, 8, 7, 6, 5, 4, 3, 2, 1][0]
```

In the above case, we have an array of integers that hasn't been assigned to a variable: `[10, 9, 8, 7, 6, 5, 4, 3, 2, 1]`. We're looking to pull out the first element in that array by calling `[0]` on the array. This code will return `10`, or the first element in the array.





