## What is an object?
An object is a collection of data with associated behaviors. 

An object combines data (the properties and attributes) and functions (usually called methods). The data represents the state of the object and the methods represent the behavior and operations that the object can perform.   
Object oriented means functionally directed toward modeling objects. 


### Properties 

Properties is data that represents characteristics of a certain object. This properties or attributes store data related to this properties or attributes like weigh, color and size. Some times the properties are read only. 

## Behaviors

Behaviors are actions that can occur on an object. The behaviors that can be performed on a specific class of object are called methods. The methods are like simple functions in structured programming but with the big difference that the methods have access to all the data associated with this object. 

## Encapsulation 

It refers to the combination of data and behaviors related or attached in an object and to the concealment of some intern details of the object. This allows modularity, safety and helps to the mantain of the code stablish limits between system components. 
Encapsulation restric the access of private methods because this methods are only used internally by the class and is not exposed to other outside methods. This is helpfull cause this avoid and prevents the incorrect use of methods and attributes of the class object. 


## Inherintance 
Inherintance is a mechanism by which a class can inherit attributes and methods from another existing class, known as a parent class or super class. The inherinting class is known as child class or subclass.

The inherintance allows the code reuse and the creation of class hierarchies. The subclass(Child class) inhertis methods and properties from superclass (father class) and the subclass can add new attributes and methods if is necessary. This helps to modularity, code maintance and class organization. 

In the constructors of the child class is a good practice call the father class constructor from the child class. This allows correctly initialize the inherited attributes and configure the initial state of the father class(super class)
