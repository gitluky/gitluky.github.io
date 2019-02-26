---
layout: post
title:      "The cliffnotes on Classes and Objects"
date:       2019-02-26 04:12:10 +0000
permalink:  the_cliffnotes_on_classes_and_objects
---


Classes and objects are essentially the foundation of Object Oriented Programming. I have been working with them for a while a now and don't really put much thought into it while I'm smashing out new code on my keyboard anymore. But in the beginning when I was first learning it, it was a bit daunting. I felt I've reached a huge revelation - Morpheus had just given me the red pill and shown me how I should really be looking at the world. Instead of viewing/building everything as a continous sequential stream of code, conceptualize everything as separate objects...people, cars, building, the woman in the red dress, etc. Let's dive deeper into the rabbit hole, and that!...will be the last of Matrix references. A simple way to look at it is that the class itself is the blueprint as well as the manager for creating the objects (instance of the class). A blueprint, as in, it defines all the things the class and the object can do (methods) as well as what data they store (variables). For an example, given a Car class, the class Car itself is like the car factory and the purpose of this class is to provide a blueprint to make objects, specifically cars. In this class, it will define all the instance variables to store information on what attributes each car object will have, i.e, color, type, wheelsize, transmission, weight...anything really. There will be instance methods, things that each car will be able to do, i.e. turn, honk, accelerate, brake...yada yada yada. That covers the blueprint duties of a class, now the managerial part...the Car class also contains class variables and class methods that allows it to be the all knowing and all powerful manager of all cars. As the factory, it can have a variable to keep track of each car that has been made. This can be accomplished by creating a class variable like @@all = [] and on instantiation of each car, add the car to @@all. '@@' in front of a variable means that it's a class variable.  It can have methods to operate on these variables as well, like finding all cars created from this class that are red, @@all.select {|car| car.color == 'red'}. Below is an example of what using class/instance methods and variables will look like.

`#a ruby file

#To create  instances of a class, an object, cars in this case:

car_a = Car.new('red', 'sedan', '17 inch', 'automatic')

car_b = Car.new('blue', 'coupe', '16 inch', 'manual')

car_c = Car.new('red', 'suv', '18 inch', 'automatic')


#To read and write to a instance's variable

car_b.color = 'green'

car_b.color #will return 'green'


#To view all the cars that were created

Car.all

#To view all the red cars that were created

Car.find_all_cars_of_color('red')



#class file

class Car

	attr_accessor :color, :type, :wheelsize, :transmission

#attr_accessors are creating 2 methods for each variable
#for example, it will create #color and #color= methods
#color is a reader, it will allow a user to ask a car for it's color by typing car_a.color
#color= is the writer, it will allow a user to define a car's color by typeing car_a.color = 'red'


	@@all = []

	def initialize(color, type, wheelsize, transmission)
		@color = color
		@type = type
		@wheelsize = wheelsize
		@transmission = transmission
		@all << self   #here the car is adding itself to @@all
	end

	def self.find_all_cars_of_color(color)
		@@all.select {|car| car.color == color}
	end


#self when defined in method name means it is a class method, refer to line 23
#self when defined within an instance method, means the instance of the object itself

end``

```

