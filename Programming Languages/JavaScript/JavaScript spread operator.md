The spread operator in JavaScript (`...`) does exactly what its name say: it spreads an iterable into individual elements. 

It serves multiple purposes, and seeing it in action is the best way to understand it.

# Copying an array

```js
const arr = [1, 2, 3, 4, 5];
const secondArr = [...arr]; // shallow copy of the first array
const thirdArr = arr; // reference to the first array
const fourthArr = [arr]; // array inside of an array

arr[0] = 9;

arr.forEach((e) => console.log(e)); // 9 2 3 4 5
secondArr.forEach((e) => console.log(e)); // 1 2 3 4 5
thirdArr.forEach((e) => console.log(e)); // 9 2 3 4 5
fourthArr.forEach((e) => console.log(e)); // [9, 2, 3, 4, 5]
```

In the example above, the spread operator works by spreading each of the elements inside a new array. You can also see wrong ways of trying to make an array copy, as the third array just turns into a reference to the first and the fourth array turns into an array with a single element inside: a reference to the first array.

# Joining arrays

Combining arrays using the spread operator is a concise way to create a new array containing all elements from the original arrays

```js
const arr1 = [1, 2, 3, 4];
const arr2 = [4, 5, 6, 7];
const arr3 = [...arr1, ...arr2];
arr3.forEach((e) => console.log(e)); // 1 2 3 4 4 5 6 7
```

