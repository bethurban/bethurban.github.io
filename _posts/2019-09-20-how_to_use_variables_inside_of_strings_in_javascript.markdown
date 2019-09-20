---
layout: post
title:      "How to use variables inside of strings in JavaScript"
date:       2019-09-20 19:06:25 +0000
permalink:  how_to_use_variables_inside_of_strings_in_javascript
---


We often want to make use of variables inside of returned or logged strings in JavaScript, but we need special syntax in order to do so.

A [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) is usually denoted by using single quotes (`'`) or double quotes (`"`) around it. When we want to use the value of a variable inside of a string, however, we need to use backticks around the string:

![](https://ibb.co/ssdg2vk)

In the code above, we first define a variable `name` that is equal to a string of `"Beth"`. We want to use the value of `name` inside of the string that we're `console.log`-ing, so we use backticks around that logged string.

A string that allows embedded expressions such as interpolated variables is called a [template literal](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals).

The other key thing to note is the syntax used to interpolate, or evaluate and retrive a value from, variables: `${ variableName }`. Use `${ }` around the variable name that you want to interpolate inside of the string so that it knows it's a variable that represents another value.


