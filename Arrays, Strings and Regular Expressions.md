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
## Varargs
Consider a method with the signature
```java
static int sum(int... numbers)
```
Inside the method, `numbers` is simply a `int[]`. See comments below
```java
x = sum(someArray);  //OK
y = sum(1,2,3,4);    //OK
z = sum(someArray,4) //ERROR
z = sum(4,someArray) //ERROR
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
## Selection Sort
Selection sort works as follows.
Start `i` at `0`.
Swap the element at `i` with the smallest element at or before `i`.
Continue with this, incriminating `i` until we get to the end of the array.
This winds up being a nested loop.
As an optimization we don't need to go all the way to the last element, because all 1-element sequences are sorted.
Ryan's Psudo-code is provided here:
```
IN: Array A has n numbers 0 to n-1
for i from 0 to n-2
	min = i
	for j from j+1 to n-1
		if A[j]<A[min]
			min = j
	swap A[i] and A[min]
```
Note that psudo-code is meant for people to read exclusively.
A computer cannot read it.
The indentation has the same meaning as in Python i.e., an increase in indentation corresponds to a Java `{` and a decrease corresponds to a Java `}`.
## Multi-Dimensional Arrays
Arrays can nest, i.e., we can have arrays of arrays.
We call these Multi-Dimensional arrays.
Indexing follows the same rules, but the consequences are non-obvious.
In a two dimensional array `m`, the expression `m[i][j]` gives us element `j` sub-array (row) `i`.
In general, we go from less to more specific.
The reason that the preceding expression works is that `m[i]` gives us row `i`, which is simply a 1 dimensional array.
We can initialize multi-dimensional arrays of `T` as follows `new T[ROWS][COLS]`. 
In the case of a multiplication table, consider the following code.
```java
int[][] timesTable = new int[10][11];
for(int row=0; row < timesTable.length; row++)
	for(int col = 0; col < timesTable[0].length; col++)
		timesTable[row][col] = row*col;
```
Multi-dimensional arrays can be non-rectangular.
The following is valid.
```java
int[][] numbers = {
	{1,2,3},
	{4},
	{},
	{5 0}
};
```
To iterate over the numbers, we would need to either use an enhanced for loop (`for(int [] row : numbers)`) or manually check the length of each array.
# Misc
## Javadoc
We use a special form of comment starting with `/**`. 
Javadoc is then extracted from the source code.
We usually just look at the comments in the source code, but it's the same stuff.
You have Seen Javadoc on Oracle's website.
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
# More Strings
Consider the following code which only works for first/middle/last, and not for 2 or 4 names.
```java
String eptName = "Patrick James McDonough";
int firstSpaceIndex = eptName.indexOf(' ');
int lastSpaceIndex  = eptName.lastIndexOf(' ');
String firstName = eptName.substring(0, firstSpaceIndex);
String middleName = eptName.substring(firstSpaceIndex+1, lastSpaceIndex);
String lastName = ept.substring(lastSpaceIndex+1)

```
We can use a loop to get the space separated components of a name. See [Exercise 14](https://github.com/arewhyaeenn/OOP_ARRAYS_STRINGS_REGEX#q14).
The general idea here is that pass a start index as a second parameter to `indexOf`.
When `indexOf` does not find the requested character, it returns `-1`.
## Escape Sequences
We have already talked about the newline character `'\n'`, the tab character `'\t'`, and the carriage return character `'\r'` which will overwrite the line.
If we want to include a `"` character in a string we need to write `\"` instead.
Take for example `"She said \"Hello\"".`. 
This represents the text `She said "Hello".`
Similarly if we want to include a backslash in our string we actually need to write two of them.
Take for example `"C:\\Users\\Patrick"`.
## Regular Expressions
This will read a file into a string, but will eat the newline at the end of the file.
```java
String content = new Scanner(new File("filename")).useDelimiter("\\Z").next();
```
The regular expression `"\\Z"` will look for the end of the file.
Instead of `"\\Z"`, we might be able to use the magic string `"\u001A"`.

# `ArrayList`
For any type `T`, we can make a `ArrayList<T>` which is like a `T[]`, but where *the size is not fixed*.
We can add elements to the end of the `ArrayList` `m` using `m.add(whatever)`.
To get the number of elements in an `ArrayList`, we can use `.size()`.
Instead of using `[index]` we use `.get(index)`.
Enhanced for loops also work for `ArrayList`.
