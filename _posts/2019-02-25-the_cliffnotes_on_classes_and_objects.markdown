---
layout: post
title:      "The cliffnotes on Classes and Objects"
date:       2019-02-25 23:12:10 -0500
permalink:  the_cliffnotes_on_classes_and_objects
---


Classes and objects are essentially the foundation of Object Oriented Programming. I have been working with them for a while a now and don't really put much thought into it while I'm smashing out new code on my keyboard anymore. But in the beginning when I was first learning it, it was a bit daunting. I felt I've reached a huge revelation - Morpheus had just given me the red pill and shown me how I should really be looking at the world. Instead of viewing everything as a continuous sequential stream of code, everything is viewed as separate objects modelled after the real world...people, cars, building, the woman in the red dress, etc. Let's dive deeper into the rabbit hole, and that!...will be the last of Matrix references. 
A simple way to look at it is that the class itself is the blueprint as well as the manager for creating the objects (instance of the class, instance and object will be used interchangeably here). A class is blueprint, as in, it defines all the attributes the object has and things it can do(methods). For an example, given a Car class, the class Car itself is like the car factory and the purpose of this class is to provide a blueprint to make objects, specifically cars, as well as manager all the cars in its inventory. It will define all the instance variables to store information on each car such as make, model, color, type, transmission…anything really. Instance methods will be defined to interact with these instance variables and also allow the car to do things like turn, honk, accelerate, brake...yada yada yada. 
That might have been confusing, but let’s go through the works. This is how you define a class:
![](https://photos.app.goo.gl/7uVVF2iS8yTLT4Pv6)
Figure 1
Awesome! We have a car class, an empty a Car class, but a class nonetheless. 
To create (instantiate or initialize) a car, we tell the class to make one:
 ![](https://photos.app.goo.gl/SW8uEDLeieaWqdvn7)
Figure 2
In this case, we’ve created a new car and assigned that car to the variable car_1. As of now, we haven’t given the car and attributes or methods so it’s pretty useless, but shown below in Figure 3 and Figure 4 is we want to be able to do with our car - set attributes for the car and get them when we want them.
Setting instance variables:
 ![](https://photos.app.goo.gl/LYS1ZUEEKxtenBVu6)
Figure 3
And calling the instance variable to get the attributes for the car:
 ![](https://photos.app.goo.gl/LYS1ZUEEKxtenBVu6)
Figure 4

To be able to do this, instance variables have to be defined:
 ![](https://photos.app.goo.gl/JH9PqzpauYb4aKmw5)
Figure 5
Instance variables have a @ in front of them, to differentiate from local variables which cannot be used across instance methods; the scope of local variables will be contained in the scope in which they are defined while instance variables can be called from all the instance methods. Before we can start interacting with the instance variables like we did in Figure 3 and Figure 4, we need to create some instance method. In Object Oriented Programming this is either called getter and setters OR readers and writers because they’re made to do just that. When we write car_1.make = “Honda”, we are actually calling a method called make= on car_1, to set the value to “Honda” and when we want to get the make that is set, we need a get method, make, to call on car_1 to reveal the instance variable to us.

