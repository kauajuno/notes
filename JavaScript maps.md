Maps are structures that store values in key-value pairs. Here's an example of a map being used in JavaScript:

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
```