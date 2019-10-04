---
layout: post
title:      "The difference between Ruby classes and objects"
date:       2019-10-04 21:38:16 +0000
permalink:  the_difference_between_ruby_classes_and_objects
---


Ruby is an object-oriented programming language that has *classes* and *objects*. What's the difference?

In a nutshell:

* A **class** is a template from which objects are built.

* An **object** is an instance of a class.

Classes are used to create objects. Objects can be called with the methods and attributes that were defined within their class.

## How to define a class

Ruby classes are defined with the `class` keyword and an `end`. The first letter of the name of the class is capitalized. All of the class's methods and attributes are defined in between.

```
class Team

  def initialize(name)
	  @name = name
	end
	
	def go_team
	  "Let's go, #{@name}!"
	end

end
```

In the above example, an instance (or object) of the `Team` class is given a `name` when it's initialized, or first made:

`philly = Team.new("Eagles)"`

In the code above, the `philly` variable is equal to a new instance of `Team` with the `name` of `"Eagles"`. (Note that any value can be used for the variable, but it makes sense to use a variable that corresponds with the object that you're creating.) You can then call:

`philly.go_team`

The return value would be:

`"Let's go, Eagles!"`

To create another object, or instance, of `Team` to represent another team:

`cleveland = Team.new("Browns")`

And to cheer on that team, you can run:

`cleveland.go_team`

To get a return value of:

`"Let's go, Browns!"`

To reiterate: In the above example, `Team` is the class. `philly` and `cleveland` are equal to two difference instances, or objects, of that class.

## Another example

The `Car` class has two attributes, `make` and `model`, and two methods: `vroom`, which returns `"Off we go!"`, and `sweet_ride`, which returns a string using the object's make and model:

```
class Car

  def initialize(make, model)
	  @make = make
		@model = model
	end
	
	def vroom
	  "Off we go!"
	end
	
	def sweet_ride
	  "I really like your ${@make} ${@model}!"
	end
	
end
```

Let's see it in action:

```
civic = Car.new("Honda", "Civic")

civic.vroom
 => "Off we go!" 
 
civic.sweet_ride
 => "I really like your Honda Civic!" 
 
mustang = Car.new("Ford", "Mustang")

mustang.sweet_ride
 => "I really like your Ford Mustang!" 

mustang.vroom
 => "Off we go!" 
```

`Car` is the class. `civic` and `mustang` are objects, or instances, of the class.
