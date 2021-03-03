*This is my favorite section. It is incredibly interesting.*
# Boolean Expressions
The simplest expressions are the Boolean literals `true` and `false`.
We have operations corresponding to mathematics which can be used in Boolean expressions.
Note though, that these Cannon be chained `0<1<2` is a compile-time error.
| Java | Math |
|------|------|
| <    | <    |
| <=   | ≤    |
| ==   | =    |
| !=   | ≠    |
| >=   | ≤    |
| >    | >    |

The `!` in `!=` is meant to be reminiscent of `!(a==b)`.
This is because `!` is the negation operator. 
The expressions`!false` and `!true` are `true` and `false` respectively.
The operators `&&` and `||` are logical 'and' and 'or' respectively.
The order of operations is `!`, `&&`, `||` , `==`,  et cetera.
Unlike the `*` operator, the `&&` and `||` operators short circuit.
This means that the right hand side will only be evaluated if it can change the result.
A more concrete statement of this is that `||` will only evaluate the right hand side if the left hand side is `false`, and `&&` will only do so if the left hand side is `true`.

DeMorgan's Laws are the following two identities:
- `!(a||b)` if and only if `!a&&!b`
- `!(a&&b)` if and only if `!a||!b`
-  It is also often useful that, more generally, `!` distributes through n-ary `&&` and `||` except that `&&` and `||` are swapped

# `if` Statements
If statements may take the form:
```java
if(<condition>){
	<true block>
}
<after if>
```
The condition must be a Boolean expression.
The `true` block must be a series of 0 or more statements.
If the condition is true, the `true` block will be run, and then the after-`if` block will be.
If the condition is false, the `true` block will be skipped.
We can also have an else.
```java
if(<condition>){
	<true block>
}else{
	<false block>
}
<after if>
```
The `false` block will be run only if the condition evaluates to false.
The braces may be omitted if the block is a single statement.
We can nest if statements.
This means, we can have if statements in if statements.
When we nest in such a way that we get an `else if`, we call this chaining.
Chaining allows us to check many conditions in sequence, and chose a corresponding action.
# The Ternary Operator `a ? b : c`
The ternary operator is an operator that we can use in expressions.
The statement `int x = a ? b : c` is equivalent to the following.
```java
int x;
if(a){
	x = b;
}else{
	x = c;
}
```
Where I used `a`, `b`, and `c`, we could, of course use any expressions. 
The expressions are only evaluated when they would be in the if statement.
# `while` Statement
A `while` statement, also called a `while` does what it says on the tin. 
It's like an if statement, without an else, except that after executing, control returns to the top of the function.
It is frequently useful to nest loops.
# `do` `while` Loops
A `do` `while` loop has the following syntax.
```java
do{
	body();
}while(cond());
```
It is similar to a while loop. 
The only difference is that the conditional is evaluated after running the loop body.
This is equivalent to evaluating it before the loop body, except that we run the body once *unconditionally*.
We frequently use `do` `while` loops to get user input.
The body gets the input, and the condition checks whether the input was valid.
We can't do this simply with just a while loop because we need to get the input before we check its validity.
# `for` loops
The prototypical `for` loop is
```java
for(int i=0;i<10;i++){
	body();
}
```
which is equivalent to the following code. 
(The outer braces limit the scope of `i`.)
```java
{
	int i=0;
	while(i<10){
		body();
		i++;
	}
}
```
This is the standard way to count 0, 1, 2, 3, ..., 9.
The statements in the for header are given the following names: `for(initializer;condition;end of iteration)`.
The monstrosity `for(;cond;)` is equivalent to the non-monstrosity `while(cond)`.
Actually useful, is the fact that `for(;;)` (pronounced forever) is the header for an infinite loop.
We can also use `while true` for this.


# Bugs: Infinite Loops
It is possible to write a loop that runs forever because the condition never evaluates false. 
This will result in either a flurry of prints, or a silent hang.
One common cause of this is an errant semicolon after a while conditional e.g., `while(i<1);`.

# `break` and `continue` statements
The `break` statement exits the innermost loop we are in.
The `continue` statement goes to the bottom of the innermost loop we are in.
We can also think of this (as our debugger does) of going back to the condition.
These are useful when we want to do something mid-iteration.

# Some techniques
We will frequently branch on a Boolean variable.
We call this a flag.
We may reserve a special value of a variable.
We may, for example break upon seeing that value.
We call this value a sentinel.

# `switch` 
We can do the following.
The switch statement compares dayName to each of the cases.
We have to include the `break` statements.
Otherwise, control would flow through to the next case.
We would always end up with a `0`.
```java
class DateUtils
{
    static int dayToInt(String dayName)
    {
        int dayInt;
        switch (dayName)
        {
			case "Sun"
            case "Sunday":
                dayInt = 1;
                break;
            case "Mon":
            case "Monday":
                dayInt = 2;
                break;
            case "Tue":
            case "Tuesday":
                dayInt = 3;
                break;
            case "Wed":
            case "Wednesday":
                dayInt = 4;
                break;
            case "Thu":
            case "Thursday":
                dayInt = 5;
                break;
            case "Fri":
            case "Friday":
                dayInt = 6;
                break;
            case "Sat":
            case "Saturday":
                dayInt = 7;
                break;
            default:
                dayInt = 0;
        }

        return dayInt;
    }
}
```
The most common use of a missing `break` is an empty block.
This works somewhat an or.

# Strings
Strings can be indexed into.
We count from `0` because we a programmers.
There are good reasons for this, but their beyond the scope of this lecture.
For example `"Sunday".charAt(0)` is `'S'`, `"Sunday".charAt(1)` is `'u'`, and `"Sunday".charAt(5)` is `'y'`.
We will get a `StringIndexOutOfBoundsException` if we pass a negative value, or one that is passed the end to `charAt`.
`String.length()` gives us the length of the string which is one more than the max index.
We can loop of characters using `for(int i=0;i<myString.length())` allows us to loop over the indices of `myString`.
The substring method allows us to specify a starting index and optionally an exclusive ending index.
For example, `"Sunday".substring(0,1)` is `"S"`, `"Sunday".substring(1,3)` is `"un"`, and `"Sunday".substring(3)` is `"day"`.
We can also get a `StringIndexOutOfBoundsException` using `String.substring`.

# Task 5
We will print out a diamond of stars.
Ryan demonstrated the following method.
Here I describe the functioning of the final project not the development process.
In a method called `repeatPrint` We use a for loop to print a given string a given number of times.
We need a method to print a row, which we call `printDaimondRow`, which simply calls `repeatPrint` twice.
It takes the number of spaces we want to print, as well as the number of asterisks.
In `printDaimond`, We can then call `printDaimondRow` in a `for` loop.
We use some dirty math tricks to avoid having to use a second loop (making it DRYer).

The trick is as follows. We could also count from `-width` to `width`, and that might be simpler.
```java
int width * 2;
for(int row=1; row < doubleWidth; row++){
	nSpaces = Math.abs(width-row);
	printDaimondRow(Math.abs(width-row), nSpaces);
}
```
By making our code DRYer, we have made it easier to read.
By using small methods, we have removed the need for comments, and made the methods easy to read or debug.

# Task 6
**Cloud9 Note**: On cloud 9, when you hit run, the working directory is the directory the `.java` file is in.
This is also the directory the `.class` file is in.

**`Scanner` and `File` Note**: `Scanner`'s constructor throws the `FileNotFoundException`.
`File`'s does not.

We will read a file containing a bunch of integers. 
We will do no validation, except we detect an empty file.
We will compute the minimum, maximum, sum, and average.

One method for initializing the values is as follows.
We initialize the max and min to `Integer.MIN_VALUE` and `Integer.MAX_VALUE`.
This works because these are the respective identity elements of the `Math.max` and `Math.min` operations.
We initialize `sum` and count to zero.

Alternatively, we can do something called a "prime read".
In this context prime means something like first.
We can initialize everything but count to the first element.
Count must then be set to 1.

As we loop over the values, we perform the respective updates on each value. 
The average can then be computed as the real-valued quotient of sum and count.
This can be suitably approximated by casting to double and dividing.

# Task 9
We can write a primality test for the integer `n`.
We check if n is 1, which is not prime.
We then check for 2, which is prime;
Then we loop through all the numbers `i` less than `(int)math.sqrt(n)`.
For each `i`, we check `n%i == 0`.
In that case we return `false`.
Once the loop terminates, we return `true`.

# Task 10
**Variable declaration Note**: 
We can declare (and optionally initialize) multiple variables of the same type in a single declaration.
`int nPrimesFound = 0, factor = 2`.
This, of course, works in for loops.

We will loop through all the integers >2 until we find all the primes we want.
We can use our primality test from our `PrimeUtils` class.

