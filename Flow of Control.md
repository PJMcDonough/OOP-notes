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
