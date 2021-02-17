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

# `File`s
To open a file, and read from it use the following code.
```java
public static void main(String[] args) throws java.io.FileNotFoundException{

	File inputFile = new File("path/to/the file");
	Scanner inputFileScanner = new Scanner(inputFile);
}
```

This is to say that Scanners can work with files specified by paths,
not just the standard input.

# `while` loops
The `while` loop will evaluate the condition, and if it's true, run
the code. It will keep doing this until it becomes false.
```java
//Print inputfile with each word on a new line
while(inputFileScanner.hasNext(){
	System.out.println(inputFileScanner.next());
}
```

# References vs primitives
See Ryan's Readmes for examples and a more intuitive, but equivalent
explanation. One way of thinking about how things are passed in java
is as follows. Assignment always makes a copy of the variable on the
right-hand-side, and other operations also make copies for their
use. The only tricky thing about this is that, except for primitive
types, the value stored in the variable is just an address. Ryan's
description of an address is delightful. It's a treasure map to
whatever type we have put there.

Note that the `==` operator checks references for equality by
comparing where the data is stored. To compare the contents of the
data, we must use the `.equals` method.

# Debugging
Debuggers allow us to step through code. A breakpoint is a point at
which the debugger will stop. These can be inserted manually. The
"step over" button allows us to go line by line. When a line is
highlighted by the debugger, that means it is about to be run. We can
look at variables when we are debugging. We can also use "step into"
and "step out" to see what happens in a function, and to run until we
return from a function respectively. The "resume program" will keep
running until it hits another breakpoint. If you run into an infinite
loop, the "pause" feature of the debugger may be helpful.
