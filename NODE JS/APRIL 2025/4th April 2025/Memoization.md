**Memoization means storing the result so you can use it next time instead of calculating the same thing again and again.**

In simpler words, it consists of storing in **cache** the output of a function, and making the function check if each required computation is in the cache before computing it.

A **cache** is simply a temporary data store that holds data so that future requests for that data can be served faster.

# Example

```js
function fibo(n) {
	if (n <= 1) return 1;
	return fibo(n - 1) + fibo(n - 2);
} // Output in approx 8 seconds

function fibo(n, memo = {}) {
	if (n <= 1) return 1;
	if (memo[n]) return memo[n]; // If we already have that computed result return that
	// Otherwise store computated result and return 
	return (memo[n] = fibo(n - 1, memo) + fibo(n - 2, memo));
} // Output in 0.09 seconds

console.log(fibo(45));
```

```js
var cache = {};

async function memoized_ajax(url, callback) {
	if (cache[url]) {
		callback(cache[url]); // we already know the result for this url
	} else {
		const data = await fetch("SomeUrl");
		cache[url] = data; // we will store the result for future usecase
		callback(cache(url));
	}
}

```


Memoization is only safe to do when the function is “pure” — that is, **if it only reads its parameters and doesn’t interact with the “outside world”.** With a pure function, it doesn’t matter whether you call it once or if you reuse its previous result.

