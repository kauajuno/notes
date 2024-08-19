Method chaining is what happens when multiple methods are called sequentially on the same object. Here's an example:

```js
const numbers = [1, 2, 3, 4, 5];

const result = numbers
  .filter(num => num > 2) // Filter numbers greater than 2
  .map(num => num * 2)     // Double each number
  .reduce((acc, num) => acc + num, 0); // Sum the numbers

console.log(result); // Output: 1
```

This is probably nothing new to someone who's already familiarized with programming concepts. However, how is it implemented in JavaScript? How can I implement this by myself?

# Implementing on classes

The easier way of implementing method chaining is with classes. Let's suppose we'd like to build a calculator class where we pass a number as a parameter and then we can invoke operations on it until we finally want to get the result.

```js
class Calculator {
  constructor(val = 0) {
    this.val = val;
  }
}
```

Now there's the magic: when we use method chaining, we call a method directly on the result of the last method. For that to be possible, the output of a method shall be able to call the next one. So if we create the methods in such way that all of them return an instance of the calculator, it will be possible to use method chaining, as a calculator instance will keep being able to call its own methods.

```js
class Calculator {
  constructor(val = 0) {
    this.val = val;
  }

  add(val) {
    this.val += val;
    return this;
  }

  subtract(val) {
    this.val -= val;
    return this;
  }

  multiply(val) {
    this.val *= val;
    return this;
  }

  divide(val) {
    if (val == 0) throw new Error("Division by zero");
    this.val /= val;
    return this;
  }
}
```

```js
const res = new Calculator(15)
  .add(5)
  .subtract(2)
  .multiply(2)
  .divide(3)
  .getResult();

console.log(res); // 12
```

# Implementing on functions

It is also possible to implement this on function, although it might seem a little bit gimmicky.

```js
function calculatorFunction(val = 0) {
  return {
    add: function (n) {
      val += n;
      return this;
    },
    subtract: function (n) {
      val -= n;
      return this;
    },
    multiply: function (n) {
      val *= n;
      return this;
    },
    divide: function (n) {
      if (n == 0) throw new Error("Division by zero");
      val /= n;
      return this;
    },
    getResult: function () {
      return val;
    },
  };
}
```

```js
const alsoRes = calculatorFunction(15)
  .add(5)
  .subtract(2)
  .multiply(2)
  .divide(3)
  .getResult();

console.log(alsoRes); // 12
```