Maps are structures that store values in key-value pairs. It's possible to access which value a key stores through the key itself, and any data type can function as a key. Here's an example of a map being used in JavaScript:

```js
const studentsGrades = new Map();

studentsGrades.set("George", 9.8);
studentsGrades.set("Elisa", 9.1);
studentsGrades.set("Matthew", 6.7);
studentsGrades.set("Elijah", 8.2);
studentsGrades.set("Mark", 4.5);

for (let item of studentsGrades) {
  console.log(item);
}

/*
[ 'George', 9.8 ]
[ 'Elisa', 9.1 ]
[ 'Matthew', 6.7 ]
[ 'Elijah', 8.2 ]
[ 'Mark', 4.5 ]
*/
```

>[!info]
>Although the outputs are represented with brackets, maps are **not** merely arrays of key-value arrays.

Maps can also be initialized through a given set of key-value pairs:

```js
const carPrices = new Map([
  ["Toyota", 88500],
  ["Subaru", 127000],
  ["Rolls Royce", 530000],
]);

console.log(carPrices[0]); // undefined
console.log(carPrices["Rolls Royce"]); // undefined
console.log(carPrices.get("Rolls Royce")); // 530000
```

>[!info]
>Notice how the use of the methods get and set are the correct way to retrieve and put or update data, respectively.

# Other methods

JavaScript also have other useful and intuitive methods for maps:

- `has()`: checks if the map has a given key passed as a parameter.
- `delete()`: given a key, removes the correspondent associated key-value from the map.
- `clear()`: clears all pairs from the map.
- `entries()`: returns an iterator that yields key-value pairs of the map.
- `keys()`: returns an iterator that yields keys from the map.
- `values()`: returns an iterator that yields values from the map.

