The four pillars of OOP are: 
- Abstraction
- Polymorphism
- Inheritance
- Abstraction
# Polymorphism
We have covered the polymorphism of the `+` operator (`String`s vs `int`s).
That's the definition.
Function overloading is also seen as a form of polymorphism in the OOP paradigm.
# Inheritance
We have covered how some of this works.
# Encapsulation
Encapsulation allows us to keep separate concerns separate. 
That's the definition.
# Abstraction
## Declaring `interface`s
In java `interface`s are like classes.

When we want to create an interface, we declare it in the same way with a couple of small differences.
We use the keyword `interface` rather than class.
We don't have private data in `interface`s.
We define `abstract` methods, rather than defining methods.
We can say, for example `int numberOfSides();` to declare a `public abstract` method.
All methods are `public abstract` implicitly, and all data is `public static final`.

It may seem counterintuitive that an `abstract` method can override a method.
This just ends up meaning that the method must also be overridden in the class that implements the interface.
We did this with `toString` for polygon

To create a class that implements `Polygon`, we can say `class Rectangle implements Polygon`.
We must also implement all of the required methods.
