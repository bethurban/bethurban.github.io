---
layout: post
title:      "Ruby iterators: `each` vs. `map` vs. `collect`"
date:       2019-10-18 18:13:28 +0000
permalink:  ruby_iterators_each_vs_map_vs_collect
---

Ruby iterators allow us to pull out every element in an array and perform some sort of action with that element. Iterators let you loop through an array and do something with every element inside.

## `each`

Ruby's built-in `each` method can be called on an array. It accepts a *block* of code that tells it what to do with each element inside the array. 

**Important:** The return value of `each` is the *original array* that it was called on. It will not return the updated elements; instead, it will return the original array with no changes to the elements.

### Example

```
numbers = [1, 2, 3, 4, 5]

numbers.each do |number|
  number + 1
end
```

The above code will loop over each element in the `numbers` array. In the first line of the `each` setup, we've assigned each element in `numbers` a value of `number` — that's the variable name that will represent each element in `each`'s code block, which follows. We can use any value for that variable, but `number` makes sense here because each element of `numbers` is an integer.

The code block (`number + 1`) will add `1` to each element (here represented with `number`) of the `numbers` array.

Note that `each` requires an `end` to close it up.

The return value of the code above? The original `numbers` array: `[1, 2, 3, 4, 5]`

### How can we return the updated elements using `each`?

What if we want the return value of the code example above to be an array of the updated elements — an array where each element's value has increased by `1`?

We'll need to first define a variable that's equal to an empty array. Then, on each loop of `each`, we'll add the element's new value to that array. After the `each` loop has completed, we'll return the new array, which will now contain the new values for all of the elements.

```
numbers = [1, 2, 3, 4, 5]

updated_array = []

numbers.each do |number|
  updated_array << number + 1
end

updated_array
```

The final return value of the code above will be `[2, 3, 4, 5, 6]` — we used `<<` inside of the `each` code block to add each element plus `1` to `updated_array`.

## `map`

Just like `each`, Ruby's built-in `map` method will loop over an array's elements and execute a code block on each loop. The major difference?

**Important:** The return value of `map` will be a new array with the updated elements. But the value of the original array that `map` is called on *will not change* — `map` is nondestructive.

### Example

```
numbers = [1, 2, 3, 4, 5]

numbers.map do |number|
  number + 1
end
```

The return value of the code above is `[2, 3, 4, 5, 6]` — an array of the elements of `numbers` with `map`'s code block (`number + 1`) applied to each.

But if we were to call `numbers` to check the original array's value, we'd see that it still returns `[1, 2, 3, 4, 5]` — `map` did not affect its value.

## `collect`

So what about `collect`? Easy! `collect` and `map` are synonyms in Ruby — they operate the same way and can be used interchangeably (though it may be helpful to only use one in a codebase just to keep things orderly and easy to read).
