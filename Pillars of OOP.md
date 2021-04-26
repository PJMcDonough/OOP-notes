The four pillars of OOP are: 
- Abstraction
- Polymorphism
- Inheritance
- Abstraction
They are all related, and mix together.
All of these things together can allow us to build hierarchies of behavior without 
# Polymorphism
We have covered the polymorphism of the `+` operator (`String`s vs `int`s).
That's the definition.
Function overloading is also seen as a form of polymorphism in the OOP paradigm.
# Inheritance
We have covered how some of this works.
# Encapsulation
Encapsulation allows us to keep separate concerns separate. 
That's the definition.
Abstractions like `interface`s can make things better encapsulated.
# Abstraction
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
