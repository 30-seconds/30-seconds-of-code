### factors

Returns the array of factors of the given `num`.
If the second argument is set to `true` returns only the prime factors of `num`.
If `num` is `1` or `0` returns an empty array.
If `num` is less than `0` returns all the factors of `-int` together with their additive inverses.

Use `Array.from()`, `Array.map()` and `Array.filter()` to find all the factors of `num`.
If given `num` is negative, use `Array.reduce()` to add the additive inverses to the array.
Return all results if `primes` is `0`, only prime factors if `primes` is `1` & only the non-prime factors if `primes` is `-1`
Omit the second argument, `primes`, to return prime and non-prime factors by default.

**Note**:- _Negative numbers are not considered prime._

```js
const factors = (num, primes = 0) => {
  const isPrime = num => {
    const boundary = Math.floor(Math.sqrt(num));
    for (var i = 2; i <= boundary; i++) if (num % i === 0) return false;
    return num >= 2;
  };
  const isNeg = num < 0;
  num = isNeg ? -num : num;
  let array = Array.from({ length: num - 1 })
    .map((val, i) => (num % (i + 2) === 0 ? i + 2 : false))
    .filter(val => val);
  if (isNeg)
    array = array.reduce((acc, val) => {
      acc.push(val);
      acc.push(-val);
      return acc;
    }, []);
    if(primes === 0) return array
    else if(primes === 1) return array.filter(el => isPrime(el))
    else if(primes === -1) return array.filter(el => !isPrime(el))
     else throw `${primes} is not a valid value of primes`
};
```

```js
factors(12); // [2,3,4,6,12]
factors(12, 1); // [2,3]
factors(12, -1); //[4,6,12]
factors(-12); // [2, -2, 3, -3, 4, -4, 6, -6, 12, -12]
factors(-12, 1); // [2,3]
```
