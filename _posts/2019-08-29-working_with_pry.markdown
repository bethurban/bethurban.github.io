---
layout: post
title:      "Working With Pry"
date:       2019-08-29 14:29:44 +0000
permalink:  working_with_pry
---


[Pry](https://github.com/pry/pry) is an excellent debugging tool when working in Ruby. It allows you to stop your code at a certain point that you set so that you can then check variable values, operations, etc. Think of it as allowing you to go under the hood and check what your code is doing as it runs.

## Setting up Pry
First, you want to make sure that Pry is available for you to use. There are a few ways of doing this. If you have a Gemfile, add `gem 'pry', '~> 0.12.2'` to that file, then run `bundle install` in your terminal. You can also simply run `gem install pry` in your terminal.

Now that you have the Pry gem installed, you'll want to make sure that your files can access it. At the top of any file that you'd like to use Pry in, enter `require 'pry'`.

Now you're ready to set some break points!

## Using `binding.pry`
Wherever you want your code to stop, put `binding.pry`. Then, when you run your code — either by running the tests that run your code to check it (for Flatiron School students, that means when you run `learn`) or by running the file itself and calling your methods at the end of that file — your code will pause on the line where you entered `binding.pry`. All of the variables and methods that have been defined before that line will be available for you to play with in your terminal.

Example:

```
def say_hello(name)
  binding.pry
  puts "Hello, ${name}!"
end
```

When you run a test on the above code, the code will pause in your terminal and you'll see the following:

```
    3: def say_hello(name)
 => 4:   binding.pry
    5:   puts "Hello, ${name}!"
    6: end
```

You can see that the code is paused on line 4, where the `binding.pry` is. Now, if you wanted to check what the value of the `name` argument was, you could simply enter `name` to see what the test passed in. You could also check to see if the code following `binding.pry` would operate as expected — you could run `puts "Hello, ${name}!"` to see if that outputs what you expect.

When you're done with your Pry session, simply run `exit` in your terminal.

Note: Running `exit` will exit the loop or test that your code is currently in. That may sometimes be enough to exit Pry entirely. But if you're in the middle of a loop in your code or there are more tests that will run the particular block of code where `binding.pry` is, `exit` will exit that loop or test and move onto the next. If you want to exit Pry entirely in that case, run `exit!` (note the exclamation point).

## What if `binding.pry` doesn't cause my code to pause?
If you've put `binding.pry` on a line in your code, and the code doesn't pause as you expect when you run your tests or the file, that itself is a helpful debugging tool.

When your code doesn't pause on `binding.pry` as you expect, that means that for some reason, your code never gets to the line where you've put `binding.pry`. In these cases, it's usually a good approach to move `binding.pry` up in your code until you get to a point where the code does pause. Then you can check your code inside of Pry to see why things aren't progressing afterwards as you had expected.

