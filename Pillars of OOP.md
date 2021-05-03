The four pillars of OOP are:
- Abstraction
- Polymorphism
- Inheritance
- Abstraction

They are all related, and mix together.
All of these things together can allow us to build hierarchies of behavior without repeating ourselves.
# Polymorphism
This comes from the Greek for "many shapes".
We have covered the polymorphism of the `+` operator (`String`s vs `int`s).
Function overloading is also seen as a form of polymorphism in the OOP paradigm.
Polymorphism lets us deal with multiple different things similarly.
Take for example the Cartesian and polar implementations of `Point`.
# Inheritance
The general idea of inheritance is that we use some behavior of another class, while adding some of our own.

We have covered how some of this works to some extent and will cover it further in the future.
Note that various implementations inherit the abstractions provided in `Polygon` and `Point`.

When we write something like `class MyClass`, this means `class MyClass extneds Object`.
This allows us to using things like `.toString` from `Object`.

In the above example, `MyClass` is a subclass of `Object`.
Equivalently we can say that `Object` is its superclass.

The keyword `super` refers to the superclass.
We can use it to call a constructor defined in `super`.
If another constructor of `super` is not called, then `super()` will be called implicitly in the constructor.
We can also use it to call the methods we override.

When no constructors are specified, Java adds the "default constructor".
This isn't really inheritance, but it is similar in principle.

Inheritance makes the `protected` access modifier actually useful.
Protected allows subclasses but not clients to see given instance variables.
Other classes in the package can also access these instance variables.

Sources disagree on whether composition is inheritance.

## `abstract class`es
Abstract classes somewhere between concrete `class`es and `interfaces`.
We can put the common data and behavior of multiple `class`es in an `abstract class`.
We cannot directly instantiate `abstract class`es, but in exchange for this, we can define `abstract` methods.
Like with concrete implementors of an `interface`, concrete subclasses of an `abstract class`must implement all the `abstract` methods of the abstract class.

One interesting difference between an `interface` and an `abstract class` is that, by overriding a method with an abstract method, an abstract class can force its concrete subclasses to override methods (e.g. `.toString`).

An `abstract class` can be subclasses of another `abstract class`, in which case, it does not need to implement its superclass's abstract methods.

In class we did an example of this with `Polygon` and its subclasses.

## A Silly Animal Kingdom
This is not a biology class. 
It is not biologically accurate (for instance we pretend all birds can fly), but the interesting bit is the inheritance.

We have the `interface Animal`, containing only the method `yell`.
`Bird` implements `Animal`, and `Eagle` and `HummingBird`. 
`Bird` adds the methods fly (which is abstract) and peck (which is concrete).
This means that `Eagle` and `HummingBird` must each implement `yell` and `fly`.
Because `Eagal`s are awesome, and Red-tailed Hawks have the best sound, we will have a *totally awesome* biologically inaccuracy where `Eagal.yell` make Red-tailed Hawk noises.

Each fish has a list of `Fin`s.
`JellyFish` has no `Fin`s so that list is empty.
Sharks do have `Fin`s, so that list is non-empty.

![AnimalDiagram.png "Summary of the Silly Animal Kingdom"]

# Encapsulation
Encapsulation allows us to keep separate concerns separate.
That's the definition.
Abstractions like `interface`s can make things better encapsulated.
`Point` and `Polygon` define how the client can interact with variables of those types.
We encapsulate the implementation.
# Abstraction
The `Point` and `Polygon` `interface`s give us nice abstractions.
The Cartesian and polar implementations of Point, and classes like`Rectangle` provide the implementation.
## Declaring and implementing `interface`s
In java `interface`s are like classes.

When we want to create an interface, we declare it in the same way with a couple of small differences.
We use the keyword `interface` rather than class.
We don't have private data in `interface`s.
We define `abstract` methods, rather than defining methods.
We can say, for example `int numberOfSides();` to declare a `public abstract` method.
All methods are `public abstract` implicitly, and all data is `public static final`.

It may seem counterintuitive that an `abstract` method that all `class`es have.
This just doesn't do anything, but can be useful for documentation.
We did this with `toString` for polygon.

We can also declare `default` methods in `interface`s.
A `default` method is one with an implementation that is provided by default.
It can be declared like
```java
default String getInstitution(){
	return "CSUCI"; // GO DOLPHINS!!
}
```

To create a class that implements `Polygon`, we can say `class Rectangle implements Polygon`.
We must also implement all of the required methods.

## Using `class`es implementing `interface`s
We can say either `Rectangle rectangle = new Rectangle(1,1)` or `Polygon rectangle = new Rectangle(1,1)`.
In the first case, the variable can only hold `Rectangle`s, but in the second, it could hold any `Polygon`, such as `HousePentagon` or `RegularHexagon`.
We using a variable of type `Polygon`, we can only use methods declared in `interface Polygon` and `class Object`.
Notably, we cannot use methods that only exist on `Rectangle`.

## Using multiple `interface`s
In `interface`s, the `A extends B` , means that any `class` that implements `A` implements `B`.
Note that this is transitive.
We may want to have an `interface Person`, `interface Faculty extends Person`, and `interface Student extends Person`.
If they both have a method `getInstitution`, then we probably want to create a new `interface Academic extends Person`, and have `Student` and `Faculty` extend `Academic` rather than `Person`.
We may want to have a `class TA implements Student, Faculty`.
In order to implement `Student` or `Faculty`, we must also implement `Academic` and `Person`
We implement all the methods in all four of these `interface`s, and our `class` works as expected.

## Casting
As we go from one type to another, except for a more specific type to a less specific type, we must cast using the syntax `(type) expr`.
For example We can say:
```java
Person p1 = new TA("Not Me");
Student s1 = (Studnet) p;
Faculty f1 = (Faculty) p1;
Faculty f2 = (Faculty) s1;
Person p2 = s1;
TA t1 = (TA) p2;
Student s1 = t1;
```
I've only included casts where necessary.

# Task 3
The starter code is [here](https://github.com/arewhyaeenn/OOP_PILLARS_1/blob/master/point.zip).
Please read comments as you modify it.
This section is rather terse, see the lecture or links.
Important lessons are listed throughout this document
We will be using points in Cartesian and [polar form](https://mathworld.wolfram.com/PolarCoordinates.html).
Keep in mind that we are using radians and the java method [atan2(y,x)](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#atan2-double-double-).
If we used the normal [atan(theta)](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#atan-double-), we would get a result in the first quadrant whenever we wanted one in the third.
Note that the getters and setters here are nontrivial; we perform a change of coordinate systems in them.

# Task 5
If you've been running on Cloud9, you will need to set up java locally.
Take a look at tasks 1 and 5 of (this README)[https://github.com/arewhyaeenn/OOP_HELLO_WORLD].
You should probably have already done this in class.

# Enums

Enum are really useful.
They allow us to give names to finite lists of possibilities.
We have a `PRIMARY_COLOR` enum.
They cannot contain any extra data.
