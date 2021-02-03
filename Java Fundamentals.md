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

We also have two types, `float` and `double`, which approximate real
numbers. They are the binary equivalent of scientific notation. The
type `float` is smaller (32 bits compared to 64 bits for `double`),
but `double` gives us a better approximation.

To write a `long` literal, use the suffix L. Take for example
9223372036854775807L.

## Behavior
When we try to store a number that is to large in an integral type,
the value wraps around.
```java
byte x = 127;
x++;//x bcomes -128
```

# Day 2
Floating point numbers come in two types. The larger type `double` is
the default floating point type. The smaller type, `float` requires a
suffix on literals. The literal `0.5` is a double, while `0.5F` is a
float.

Character literals approximate the idea of a character. They are
notated surrounded with single quotes (`'a'`, `'$'`). We also have
escape characters like `'\n'` for newlines, `'\t'` for tabs, and
`'\r'` to make you life worse.

The `bool` datatype (from the word Boolean), has two types `true` and
`false`.

Strings can contain multiple `char`s. We use double quotes (`"Quick"`,
`"Rápido"`). Strings are not primitives, they are objects, but there
some corner cases.

## Arithmetic operations
We have `+ - * / %`. The `%` operator gives a remainder and is also
called the modulus operator. These operators follow the order of
operations (like PEMDAS). Multiplication, division, and modulus have
the same precedence for order of operations. Addition and subtraction
are done left to right as a group

We also have `+= -= *= /= %=`. The statement `x+=5` is equivalent to
`x = x+5`. The other shortcut operators work similarly. There are four
more shortcuts. The expressions `x++`, and `++x` work like `x+=1`,
except that `x++` evaluates to the old value of `x` and `++x`
evaluates to the new value of x. We, analogously have `x--` and `--x`
for `x-=1`.

## Casting
Consider the following working snippet
```java
int x = 5;
byte y = x;
```
The following does not work.
```java
int x = 5;
byte y = x;
```
We must cast
```java
int x = 5;
byte y = (byte) x; 
```
We can get wraparound for some values of x,
```java
int x = 128;
byte y = (int) x; 
```
This applies whenever we go from one type to a type that cannot hold
all the values of the first type. We call this a lossy
conversion. Casts are not, however needed when going from integral
types to floating point types.

Casting from floating point types truncates. We have `(int)4.99 == 4`
and`(int)-4.99 == -4`
## Polymorphism
The `+` operator does different things for different types. In other
words, it's polymorphic. We've seen several different forms of
arithmetic addition, and string concatenation. `"Crème" + " " +
"brûlée"` gives us `"Crème brûlée"`. Note that `+` is always left to
right. `1+1+"nd Day` gives us `"2nd Day"`, but `"Day " + 1+1` gives us
`"Day 11"`.

Division. Dividing integers gives integers, but if either argument is
a floating point type, then the result is a floating point type. This
means `(double)(6/5) == 1.0`, to get an accurate answer, we must use
`(double)6/5` which is equivalent to `((double)6)/5`.

## Floating Point Rounding errors
Floating point math, in general, only gives an approximately correct
value. For this reason, we don't use `==` with floating point values
in most cases.
## The Math Class
Googling for documentation is a good idea. Try it.
## The `.` operator
This works somewhat like `/` in URLs. It allows us to access members
of classes and packages.
