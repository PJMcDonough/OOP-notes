# Posted Lectures
*You should view the posted video lectures and read the README.*
# Reminders
1. Variables, methods, classes and should have meaningful names.
2. DRY code is good
# Up to and including Task 2
If a variable is declared in class scope and does not bear the `static` modifier, one exists for each instance of the class.
If a method does not bear a `static` modifier, then each call to the method is associated with an instance, which must precede the method with a `.`. 
It will also receive an implicit argument called `this`.
The `this.` prefix can be omitted if there is not some other variable (e.g. an argument) that it would refer to.
We can prevent the use of methods and by declaring them `private`.

We can ensure certain properties hold for all instances of our class by keeping things private. 
We must also only allowing mutation in such a way as to ensure that when these properties remain true.
In the case of `Fraction` we ensure that we ensure that our fractions are simplified.

I introduce a few terms here.
Each of them can be used either as a adjective to modify method, or as a noun.
Getter methods are methods that simply return an instance variable.
They are usually named like `getTheThingWeWantToGet`.
Accessors are more general.
They may also be named similarly, but they do not necessarily just return an instance variable.
They may also do calculations.
All getter methods are Accessors, but not vice versa.
Setters simply set an instance variable.
Mutators are a generalized version of setters, they may also do calculations and modify many variables.

We can cause the program to crash by using the code `throw new RuntimeException("0 in Fraction denominator")`.
This will provide the string in the crash at runtime.

`Fraction` is immutable, meaning we don't modify instances once we create them.
This may seem useless, but we can return instances of a class from methods of that class.
We do this for the `multiply`, `.divide`, `.add`, `.subtract`, `.negate` and `.reciprocal` methods.
We implement `.subtract` in terms of `.add` and `.negate`, and `.divide` in terms of `.multiply` and `.reciprocal`.
This makes our code DRYer, and DRY code is good.

We can do method overloading with both `static` and non`static` methods, but we can call `static` methods from instances.
This means that we need to have different in-source argument lists (i.e. neglecting `this`).

Ryan implemented much of`FractionCalculator` in lecture, but you should modify it to also test `.equals`.
Also take a look at the rigorous testing he does for other methods.
You don't need to test the getters.
They are too simple to need tests.

# Task 5: Triangles
We can use the keyword `final` to prevent a variable from changing.
We used `private final` to declare the array `sides`.
This prevents us from reassigning `sides`, but does not prevent us from mutating the elements behind the pointer.
In fact, we *do* mutate behind the pointer; we sort the `sides`.
We don't return `sides` because that would allow the client to mutate them; instead we make a copy.
We also have several accessors that do computation.

Since we sorted the sides, we can use that in the `equals` method. 
We can also access anything in the other argument because the `Triangle` class has free reign over all `Triangles`, not just `this`.

When we write the `toString` method, we are overriding the corresponding method of `Object`.
IntelliJ indicates this.
If we hadn't done this, then `Triangle` would use the `toString` method in `Object`.
It is customary to indicate that you are overriding a method using the `@Override` syntax.
This is useful for documentation and makes clear you actually intended to override the method.

We can use the `instanceof` operator to see if something is, in fact, e.g, a `Triangle`. 
We wrote, in effect, `otherObject instanceof Triangle` to determine whether `otherObject` was a `Triangle`.

**NB**: We decide to allow triangles with 0 area provided the sides actually line up. 

## Exceptions
We wrote an exception class: `InvalidTriangleException`.
```java
public class InvalidTriangleException extends RuntimeException{
	public InvalidTriangleException(double[] sides){
		super("sides are:"
			+ sides[0] +","
			+ sides[0] +", and"
			+ sides[0] 
			)
	}
}

```

Exceptions would not be all that useful if they always resulted in the program crashing.
For that reason, java has two keywords to help us with this.
The `try` keyword indicates a block of code which may throw an exception we want to handle.
The `catch` keyword indicates a block of code which handles some type of exception, and what kind of exceptions it can handle.
We can have multiple different `catch` blocks (as shown below).

```java
try{
	doStuff()
}catch (ExceptionType1 e){
	handleExceptionType1(e);
}catch (ExceptionType2 e){
	handleExceptionType2(e);
}catch (Exception e){
	e.printStackTrace(); // but we still don't crash!
}
```
