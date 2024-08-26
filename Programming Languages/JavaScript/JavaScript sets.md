Sets are structures that store unique values and have no defined sequence. Here's an example of a set in use in JavaScript.

```js
const mySet = new Set([1, 2, 3, 4, 5]); // adding values through Set constructor passing an array
const myOtherSet = new Set(); // let's populate this one use the add method

myOtherSet.add(6);
myOtherSet.add(7, 8);
myOtherSet.add([9, 10]);
myOtherSet.add(6);

for (let i of mySet) {
  console.log(i);
}

console.log("---");

for (let i of myOtherSet) {
  console.log(i);
}

/*
1
2
3
4
5
---
6
7
[ 9, 10 ]
*/
```

>[!info]
>Note that add receives just one parameter, and passing an array will add the entire array object to the set. Also note that adding elements that are already in the set won't do anything.

# Other methods

JavaScript sets share the same methods as [[JavaScript maps]]. This is quite confusing as sets don't have explicit keys, and yet you can invoke the `keys()` method just as you do with maps. In case you're wondering, that method has the same behavior as `values()` when invoked on a set, returning an iterator to the values.




