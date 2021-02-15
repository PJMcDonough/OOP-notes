# Methods
- They keep your program DRY
  - This means Don't repeat yourself
	- Defining DRY is one of the only times you can be WET (We enjoy typing).
	- In music and education, repetition legitimizes. This is not the case in code.
We used this in Ryan's Implementation of [Exercise 1](https://github.com/arewhyaeenn/OOP_CLASSES_OBJECTS_METHODS#exercise-1).
This is what `UserWrangler` was for.
# Importing
```java
//Ex
import java.util.Scanner
// Now we don't have to type out the whole name
```
But we don't have to import anything from `java.lang` because it is automatic.
# Constructing Objects
We say the following. `new` is the only reserved word here.
```java
Type name = new Type(args);
Scanner scan = new Scanner(System.in)
```
# Scanner's Weirdness
Methods like `.nextInt` and `.nextBoolean` don't consume
newlines. This can result in `.nextLine` reading a blank line when
first called. The second call will return the following line, which is
frequently what you want.

# `if` Statements
The only reserved word in the following code is `if`.
```java
if(condition){
	whenTrue();
}else{
	whenFalse();
}
```
# What is a `class`?
A class is a collection of data and methods. There are two kinds of
data `static` and non-`static`. Non-`static` data is different for each
instance (made using the `new` keyword).

There are several board categories. We have object-blueprints e.g.,
`Scanner`, Collections of data and static methods, and client classes
which exist mainly as entry points.

# `final`
Things can be marked final, which prevents them from changing

# `static` methods

The `static` keyword makes something a property of the class, rather
than of an instance. We've encountered these before. Consider
`Math.abs` as compared to `Scanner.nextInt`.

The syntax is 
```java
static <type> <indentifier>(<arg list>)
{
	<body>
}
```

The code inside the method will run top to bottom until we get to a
return statement (or in the case of a `void` function, the bottom of
the function). For a non-`void` function, the value of the function
call will be the expression in the return statement.

These are still technically not functions. Functions don't live in
classes. There are no functions in Java, only methods. People will say
the wrong thing. The two words are sort of interchangeable even though
there is technically a difference.
