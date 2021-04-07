# Posted Lectures
*You should view the posted video lectures and read the README.*
# Reminder
Variables, methods, classes and should have meaningful names.
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
We do this for the `.negate` and `.reciprical` methods.
