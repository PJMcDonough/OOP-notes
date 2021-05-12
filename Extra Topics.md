# Recursion
Recursion is when something is defined in terms of itself.
A recursive method is one that calls itself.
A method must not always call itself. 
Doing so would result something called a stack overflow.

We wrote a simple recursive method to compute Fibonacci numbers.
Please do not actually write it this way; it will take ages because it does tons of repeat work.
We can make this slightly less terrible by keeping track of the Fibonacci numbers we have already computed i.e., memoizing them.
This is faster, but it is aesthetically hideous; we should use a loop.
When we can easily use a loop we should use it rather than recursion.
# Lambdas
Lambdas in java can look like `(input1, input2) -> {statment1; statment2}`.
It can take any amount of input, and give either some, or no output.
There is a particular type of lambda, called a `Runnable` which takes no input and gives no output.
The `Runnable` written `() -> {System.out.println()}` can has a `.run()` method which allows us to give the output.
We can also write it as `() -> System.out.println()`.
There are also suppliers, which take no input, but return a value, consumers which take an input, but return no value, and functions which take one input and give an output.
Consider `Supplier<String> helloWorld = ()->{return "Hello World"}`, which we can shorten to `Supplier helloWorld = ()-> "Hello World"`. 
Suppliers give us the `.get` method which allows us to get a value out of the `Supplier`.
We can, of course, have side effects in these.
Consider `Consumer<String> helloworld = (s)-> System.out.println(s)`. 
Instead of writing this as a lambda, we can write it as a method expression `Consumer<String> helloworld = System.out::println`.
We can then use `.accept(s)`.
Similarly, there is such a thing as a `Biconsumer`, but there is no `Triconsumer`.
Consider 
```java
Biconsumer<String, String> =` (s1, s2) ->{
	Stringbuilder zipped = new StringBuilder();
	int len = Math.max
	for(int i=0;i<len;i++){
		if(i<s1.len){
			zipped.append(s1.charAt(i));
		}
		if(i<s2.len){
			zipped.append(s2.charAt(i));
		}
	}
	System.out.println(zipped.toString);
}
```
We can also have lambda be `Function`, such as the identity function `(x)->x`.
We can use the `apply` method of `Function`.
## `.foreach`
Given a collection `m`, and a consumer `c` we can write `m.forEach(c)`.
This is equivalent to ` for(e:m) c(e);`.
While this is beyond the scope of this class, we can parallelize with this.
## `.reduce`
This method takes a `BinaryOperator`, which we can get from a lambda.
We can write the sum of a collection m as `m.reduce(0, (partialSum,nextElem) -> partialSum+nextElem)`.
We use `0` because it's the additive identity.

Because of the parallel use-case, if the partialSum is not the same type as the nextElem, we also need to provide another argument to reduce to allow combining multiple sums.

Let's take a look at the greatest of many numbers using gcd.
```java
static int gcd(int m, int n){
	if(n<m)
		return gcd(n,m);
	if(n==0)
		return 0;
	int r = m %n;
	while(r>0){
		m = n;
		n = r;
		r = m%n;
	}
}
```
We can then say `m.reduce(0,MyClass::gcd). This will give us gcf of a set of numbers.
