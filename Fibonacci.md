# Fibonacci

# Definition:

A numerical pattern where each number is the sum of the two numbers that precede it.

The sequence [0, 1, 1, 2, 3, 5, 8, 13, 21, 34] represents the first ten numbers in the Fibonacci sequence.

_Why you would want to know this_:
The Fibonacci pattern appears in a variety of contexts: mathematics, science - and even art and nature. For example, the asexual reproduction of amoeba follows the Fibonacci pattern.

![Amoeba asexual reprdodcution image in the Fibonacci patter](https://math.temple.edu/~reich/Fib/amoebae.gif)

Source: [THE FIBONACCI SEQUENCE, SPIRALS AND THE GOLDEN MEAN](https://math.temple.edu/~reich/Fib/fibo.html)

# Implementation:

- Print out the n-th entry in the Fibonacci series.
- Note: We must define the series with the first two numbers of 0 and 1 first, before generating the remainder of the sequence.

### Solution 1: Brute Force

```js
function fib(n) {
  let series = [0, 1];
  for (let i = 2; i <= n; i++) {
    series.push(series[i - 1] + series[i - 2]);
  }
  return series[n];
}
```

### Solution 2: Recursion

```js
//Base Case: The only time we return a number, is when n < 2
	if (n < 2) {
    		return n;
  	}
//Keep calling Fibonacci with smaller and smaller numbers until you call the function with n < 2. Once, n < 2, we return the numbers themselves and add them to each other.
  	return fib(n - 1) + fib(n - 2);
}
```

The image below depicts how the recursive method functions. At each level, n decreases by a value of 1 _and_ 2.

![Diagram of Fibonacci function in action](https://i.imgur.com/vdAkXQ9.jpg)

When we reach n<2, we find the total number of fib(1) and add them together to reach the value at n in the sequence.

- Runtime: The recursive approach takes an exponential run time: for every additional element, we are getting a dramatic (read: exponential) increase in the number of function calls to arrive a the result.

### Solution 3: Memoization

Store the arguments of each function call along with the result. If the function is called again with the _same arguments_, return the already calculated result that we have stored, instead of running the function again and duplicating the result (like in recursion). This optimizes the runtime.

```js
//Define a function called 'memoize' that takes in a function 'fn' that will return a faster function
function memoize(fn) {
	//Store all the arguments used to call the memoize function and their respective results
	let cache = {};
  //We don’t know how many args the fx will be called with, so just take all the args and assign them to an array call args and pass them to the fx
  	return function (…args) {
    //If the function has already been called with this particular set of args
    if (cache[args]) {
		//Then return the result already stored instead of calling the functuion
      return cache[args];
    }
		//Otherwise take n from slowFib and store it in cache obj
		//When we call a function with an array of args, use the .apply() method
    	const result = fn.apply(this, args);
		//Take result from calling slowFib fx and store it in the cache at cache[args]
    	cache[args] = result;
    	return result;
  };
}
//The slow version of the function (the recursive approach)
function slowFib(n) {
  //id base case
  if (n < 2) {
    return n;
  }
//the fib calls below are a reference to the memoized fib fx
  return fib(n - 1) + fib(n - 2);
}
//reassign fib
fib = memoize(slowFib);
```
