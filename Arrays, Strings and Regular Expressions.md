# Javadoc
We use a special form of comment starting with `/**`. 
Javadoc is then extracted from the source code.
We usually just look at the comments in the source code, but it's the same stuff.
You have Seen Javadoc on Oracle's website.
# Arrays
Arrays allow us to have multiple things in one variable.
For a type `T`, we can declare an array of `T`s named `var` like `T[] var`.
The characters `[ ]` and `[]` have identical meaning.
An example of an array of `int`s `new int[]{42, 66, 99}`.
The `new int[]` bit can be left out in a compound declaration-initialization statement.
We can also make an array like `new int[10]`.
Everything is initialized to its default value.
Numerics are initialized to `0`, `boolean`s are initialized to `false`, characters are initialized to `\0`, and all other types (i.e. objects) are initialized to `null`. 

Each element of an array has an index.
We start at `0` and go up to one less than the length.
We can get the element corresponding to an `i` of the array `m` using `m[i]` pronounced (by me) `m` sub `i`.
We can use this on the left side of an assignment.
The statement `m[0] = 7;` sets the first element to 7.

You can iterate over the indices of the array of `T`s `m` as follows:
```java
for(int i=0; i<m.length; i++){
	// use i and/or m[i]
}
```
It is critically important that we start at `0`, and that we use `<` and not `<=`.
Note that, unlike with strings, getting the length of an array does not require parentheses.

If we don't need the indices, but only the values (in order), we can write:
```java
for(T e:m){ // the `:` is pronounced "in".
	//use e which corresponds to m[i] in the above example.
}
```
Style point, it is common to name arrays with the plural, and the element with the singular.
We can write:
```java
for(String month:months);
for(int index:indices;
```
## Array Equality
To check arrays for equality, we check if their lengths are the same, and then check for equality at each index.
This is not what `==` does; `==` checks to see if the arrays actually refer to the same place in memory.
This difference is important because arrays are passed by reference.
Remember that primitives are not passed by reference.
To copy an array, we can use allocate a new array with the length of the old one, and then copy values index by index in a for loop.
Ryan's code has demonstrations of all of this.
We can also use `java.util.Arrays(array_1, array_1.length)`.
## `StringBuilder`
When we concatenate two `Strings` together with `+`, this requires allocating memory and copying both `Strings`.
This is inefficient if done in a loop to build a string.
For this reason, we use the `StringBuilder`.
The `StringBuilder` keeps track of all of the strings we `.append()` to it.
When we call `.toString()`, the StringBuilder will allocate a single `String`.
This improves performance. 
Ryan provides the following code to demonstrate how to use StringBuilder.
```java
Scanner scan = new Scanner(System.in);

System.out.println("Enter 10 words");
StringBuilder words = new StringBuilder();

for (int i = 0; i < 10; i++)
{
    words.append(scan.next());
    words.append(" ");
}

System.out.println("You entered: " + words.toString());
```
## Reduce-Like Methods
You are not expected to know what Reduce-like is supposed to mean. Consider the code below.
```java
public static int sum(int[] m){
	int rv=0; //THIS LINE
	for(int e:m){
		rv+=m; //THIS LINE
	}
	return rv;
}
```
Note that `rv` stands for "**r**eturn **v**alue". 
Changing the indicated lines above can make the code compute the
minimum, or the maximum, or the average, but we normally compute the
average by first calculating the sum and then dividing.
# Misc
## Swap
To swap two things of type `T` (for example variables or places in arrays), we do the following.
```java
T tmp = thing1;
thing1 = thing2;
thing2 = temp
```
And **NOT**
```java
thing1 = thing2;
thing2 = thing1;// This line does nothing.
```
## Method Overloading
We can have multiple methods of the same name if they have different argument lists.
Ryan implemented `max(int[] inputArray, int startIndex, int endIndex)`.
We can implement `max(int[] inputArray)` as:
```java
public static int max(int inputArray){
	return max(inputArray, 0, inputArray.length);
}
```
