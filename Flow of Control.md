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
