Arrays are probably the most important structures in JavaScript. They are basically indexed structures that can store data. They can be created both by using the brackets or the array constructor:

```js
const arr = [1, 2, 3, 4, 5];
const otherArr = new Array(1, 2, 3, 4, 5);
```

As they're indexed structures, you can access any element of the array given its index.

```js
const arr = [1, 2, 3, 4, 5];

let first = arr[0];
let last = arr[arr.length - 1]
```

>[!info]
>The property `length` of the array keeps track of how many elements are in it.

# Adding elements

There are three ways of adding elements to an array.

```js
const myArr = [1, 2, 3, 4, 5];

myArr[0] = 99; // updates the element at index 0, now it's 99 instead of 1
myArr.push(6); // adds the element at the end of the array
myArr.unshift(0); // adds the element at the beginning of the array.

for (let i of myArr) { // 0 99 2 3 4 5 6
  console.log(i);
}
```

# Removing elements

There are also three ways of removing elements from an array.

```js
const myArr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

myArr.pop(); // removes the last element of the array
myArr.shift(); // removes the first element of the array
myArr.splice(1, 2); // given .splice(m, n), removes n elements starting from element at index m

console.log(myArr); // [2, 5, 6, 7, 8, 9]
```

>[!info]
>After the second parameter on splice, every parameter passed will be added as a element of the array in the position of the excluded elements. `myArr.splice(1, 2, 3, 4)` in the example above would revert the array to its initial state, as after removing elements 3 and 4 they would be added again at the same position.

# Finding elements

There are two built-in methods created in order to find elements in an array.

- `indexOf()`: given a parameter n, returns the index of the first occurrence of `n` in the array.
```js
const myArr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

console.log(myArr.indexOf(1)); // 0
```

- `includes()`: given a parameter n, returns `true` if the array includes the element in it and `false` otherwise.
```js
const myArr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

console.log(myArr.includes(11)); // false
console.log(myArr.includes(10)); // true
```

# Other methods

- `.flat()`: this method works by "flattening" elements inside of the array by "solving" them into the array. It's easier to understand by seeing it in action:
```js

```




