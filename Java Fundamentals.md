# Housekeeping 
There is an exam next week. Take a look at the calendar. For best
results, take the exam during class. Read Ryan's READMEs after
class. They are excellent. Ryan's favorite IDE is InteleJ. You can use
that if you'd like.

# Program Structure
All Java code lives in class. Every Java program has at least one
class, and at least one main method. The name of the class must match
the name of the `.java` file.

```java
class MyClass
{
	public static void main(String[] args(){
		// Your code goes here for now
	}
}
```

Comments are notes from programmers to each other, including their
future selves. They don't not slow your program down. We should try to
write code so clearly that comments are unnecessary, but this is, in
general, impossible. There are two ways to indicate that text is a
comment. Single-line comments started with `//` continue to the end of
the line. Multi-line comments contain arbitrary text between `/*` and
`*/`.

Each of the pairs of curly braces (`{ ... }`) introduces a
scope. Scopes are where variables live. Variables must be declared
before they are used. The syntax for this is `Type name;` where Type
is the type of the variable, and name is its name. Assignments give
variables their values. Assignment has the following syntax `name =
value;` where value is the new value of the variable named `name`.

We call the names of variables identifiers. Identifiers must start
with a Java letter and can be followed by Java letters and
digits. Java letters are ordinary letters, as well as `_` and
`$`. This implies that identifiers cannot contain white-space (e.g.,
spaces, tab, newlines). Identifiers cannot be keywords. Keywords
include `int`, `public`, `static`, and `void`. Keywords are
syntax-highlighted.

# Exercise 4

1. `asdf` Identifier
2. `ASDF` Identifier
3. `aSDf` Identifier
4. `as df` Not an identifier. Contains spaces
5. `$asdf` Identifier
6. `myvariable` Identifier
7. `for` Not an identifier. `for` is a reserved word.
8. `var1` Identifier
9. `1var` Not an identifier. Starts with a number

# Conventions
This is not required by the Java compiler, but is required if you want
other people to be able to read your code. Consistency is more
important than any given rule. The goal here is readability.

- Class names should be in `PascalCase`.
	- Ryan will be picky about this one. Any sane group of people will
      name classes like this.
- Variable names should be in `cammelCase`.
- Constants (i.e., final variables) should be in `UPPER_SNAKE_CASE`

# Expressions (Assignment) Statements and Blocks
Expressions e.g., `1 + 1` have value. Statements do not. Statements
simply perform tasks. Examples include `int myInteger;` and `x = 1 +
y;`. Statements are terminated by semicolons. Statements and
expressions can span multiple lines. We can also write `int x = 1` to
both declare and assign. Wherever we can use a statement, we can use a
block instead. A block is made up of multiple statements between curly
braces (`{}`). Blocks define scopes. We will demonstrate the
usefulness of this later.

We can reassign variables. Take for example the statement `x = x + 1`. 
This increases the value of x by 1. The first assignment is
special. It's called initialization, and must happen before using a
variable. This is a compile-time error. We must convince the file that
the variable is definitely initialized before using it. We cannot
re-declare variables.

# Constants

Constants can be initialized, but not subsequently assigned. Declaration
is like that of variables, but the type must be preceded by the
reserved word `final`. Use them to make your program more DRY.

# Primitive Data Types
Primitive data types are passed by value.

```java
int x=0;
int y=x;
x=1;
```

After the above code, y is still `0` even though x has been changed to `1`.

## The types
|name |bits|range                                      |
|---- |----|-------------------------------------------|
|byte |8   |[-128, 127]                                |
|short|16  |[-32768, 32767]                            |
|int  |32  |[-2147483648, 2147483647]                  |
|long |64  |[-9223372036854775808, 9223372036854775807]|

We also have two types, `float` and `double`, which approximate real numbers. They are the binary equivalent of scientific notation. The type `float` is smaller (32 bits compared to 64 bits for `double`), but `double` gives us a better approximation.

To write a `long` literal, use the suffix L. Take for example 9223372036854775807L.

## Behavior
When we try to store a number that is to large in an integral type, the value wraps around.
```java
byte x = 127;
x++;//x bcomes -128
```
# To be Continued ...
