A closure is a function that remembers the environment in which it was created. Let's take the following example:

```js
var createCounter = function (n) {
  let count = n;
  return function () {
    return count++;
  };
};
```

Let's understand what is happening here:

- A variable create counter is being created.
- It has an anonymous function being assigned to it
- That function receives a parameter n, initialize a variable count with the value of n, and returns another anonymous function.
- This last function returns the variable count and then increases its value by one every time it is called.

Let's see how it will perform in practice:

```js
let counter = createCounter(10);

console.log(counter()); // 10
console.log(counter()); // 11
console.log(counter()); // 12
console.log(counter()); // 13
```

It works, but somehow it seems strange at first. Why does it work? The answer is: **JavaScript functions are first-class objects and can carry around with them the context (variables) from the scope in which they were created. This "memory" is what we call a closure.**

The last anonymous function that is being returned and being called through `counter()` in the example remembers the value of the `count` variable as it was in the outer-scope of the function, right above it.

Then a question might emerge: if it remembers the `count` variable, shouldn't it remember the `n` parameter? It not only should, but it does, so the following function works just as well as the first implementation:


```js
var createCounter = function (n) {
  return function () {
    return n++;
  };
};
```

