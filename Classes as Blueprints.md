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
# Task 6: Linked Lists
Linked lists are like arrays.
They allow us to have more than one of something in a given variable.

A linked list is composed of links.
Each link has data and a pointer to the next link in the list.
In addition to the `Link` class, which will have a `head`, and `tail` pointer.
The `head` pointer points to the first item, and `tail` to the last.
We are making a singly linked list of `int`s.
A doubly linked list also has links in the opposite direction.

CSUCI's Java style generally follows the principle that we should not usually directly access instance variables.
Instead, it uses getters and setters heavily.
The rationale for this is encapsulation; this makes it easier to add validation, or change the way data is stored.

Constructors can call each other.
The syntax for this is `this(args)` for any list of arguments `args`.
We use this as `this(DEFAULT_VALUE)` in `LinkedListNode`.

We maintain some invariants in `LinkedList`. 
The field `this.length` is always correct, and the fields `this.head` and `this.tail` point to the first and last elements respectively if they exist, else null.
This implies that if and only if the list is one item long `this.head == this.tail`.

We can append to an empty `LinkedList` by setting the head and tail pointers to the new element `Link`.
For a non-empty `LinkedList`, instead of setting the head pointer, we set the next pointer in the old `tail` `Link`.
It is very important that we do these in the right order. 
After this, we must update the length.

In order to prepend (i.e. insert at the beginning of the list), we set our new node's next to the head, and then head to our new node.
If the list was empty, we must also set the tail pointer.

We can iterate over the items of a linked list by looking at the `next` field of each node. We can append to a `LinkedList`. 
We stop when we get to a `null`.
This is also how we get an element at a specified index.
On indexing, however, we would like to throw and `IndexOutOfBounds` exception whenever we have a negative index or one that is greater than or equal to length.
For `toArray`, we must first allocate an `int[length()]`, and while we iterate, we keep track of how far we are into the array.

For the method `popLeft`, we want to remove the `head` node and return it's data. 
For an empty `List`, we can simply return `null` to indicate that there is no data left.
For a non-empty list, we set `head` to the next value of the current `head`, and if the list becomes empty, we `null` `tail`.

For `popAtIndex`, we can abstract out the logic of `getNodeAtIndex` into a new method.
If the index passed in is `length`, we need to notice that this is an invalid index, and throw an `IndexOutOfBoundsException`. 
We must do the same if we have a `length` of zero because `popLeft` returns `null` when we want an exception.
We've already written the special case for popping `head` in `popLeft`. 
We can just call that.
Otherwise we need to find the node before the one we want to pop.
The node before the one we want to pop must have its `next` modified to point to the whatever the node we pop's `next` points to.
If we are returning `tail`, we must set it to the new tail (i.e. the node before the one we popped).
Here we use the `==` operator rather than the `.equals` method because we don't want to compare innards.
We are actually just comparing whether they are literally the same object.

Now we consider `insertAtIndex`
Note that prepend is the `0` case, and append is the `length` case.
If we don't fall into either of these cases, we want to insert between two nodes, or we have an invalid index.
We can use `prev = getNodeAtIndex(index-1)`.
After this we set the `next`s.
It is important that we set `newNode`'s first.
We finally increment size.

Instead of initializing instance variables in constructors, we can initialize them at the declaration site.
If we don't initialize at the constructor site, they are initialized to default values.
This is `0` for numeric types, `'\0'` for characters, and `null` for objects.
