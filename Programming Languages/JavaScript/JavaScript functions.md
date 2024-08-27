A function is some block of code designed to perform a particular task, and is executed when called. A basic JavaScript function can be declared with the following syntax:

```js
function example() {
  return "Hello world";
}

console.log(example()); // Hello world
```

# Function expressions

A function expression allows you to define a function inside an expression. It is usually assigned to a variable.

```js
const greet = function() {
    console.log("Hello world");
};

console.log(greet()); // Hello world
```

# Anonymous function

You might have noticed something strange in the code above: that function does not have a name. And that's right, that's a regular implementation of an anonymous function.

Anonymous functions might seem kind of pointless for beginners, but soon it shows its enormous value, as it helps a lot with:

- Conciseness: spares you from writing a lot of code on callback and inline functions.
- [[JavaScript closures|Closures]]: enables the creation of functions that remember their context.
- [[#Immediately invoked function expression|Immediately invoked function expressions]]: allows you to create a function that will be executed right after, creating a private scope for variables and functions within them. 
- [[#Function expressions]]: seen right above!

Don't worry about acing all of these topics for now, you will read more about them later and so they will sink in.

# Inline function

An inline function is a function whose code is directly inserted into the point where it is needed, often being passed as a parameter. Inline functions are often [[#Anonymous function|anonymous]] for practical reasons, even though it doesn't prevent them from being named.

```js
let numbers = [1, 2, 3, 4, 5];

let doubled = numbers.map(function (num) { // inline function
  return num * 2;
}); 

console.log(doubled); // [2, 4, 6, 8, 10]

```

# Callback function

A callback function is a function that is passed as a parameter to another function and executed inside of it at a certain point. They can be either regular functions or [[#Inline function|inline functions]].

```js
function greeting(name) {
    console.log('Hello, ' + name);
}

function processUserInput(callback) {
    let name = prompt('Please enter your name.');
    callback(name);
}

processUserInput(function(name) {
    console.log('Hello, ' + name);
});

processUserInput(greeting);
```

# Immediately invoked function expression

IIFEs are function that, as the name suggests, are invoked immediately up on its definition. These functions have their own private scope, protecting possibly data from the outer scope and avoiding namespace pollution.

```js
(function iife() {
  console.log("I'm being invoked right after being defined? That's crazy.");
})(); // I'm being invoked right after being defined? That's crazy.
```

# Parameters

Passing a parameter in JavaScript is very simple. As saw above, you define the parameters of a function between the parentheses.

```js
function greet(name){
  console.log(`Hello there, ${name}`);
}
```

It's possible to have many of them.

```js
function introduction(name, age, occupation, city){
  console.log(`Hello I'm ${name}, I'm a ${age} year-old ${occupation} from ${city}`);
}
```

It's also possible to define default values for parameters in case some of them are not passed when the function is called.

```js
function introduction(
  name = "John",
  age = 28,
  occupation = "engineer",
  city = "Oklahoma City"
) {
  console.log(
    `Hello I'm ${name}, I'm a ${age} year-old ${occupation} from ${city}`
  );
}

introduction(); // Hello I'm John, I'm a 28 year-old engineer from Oklahoma City
```

If no parameters are passed and there is no default value, they are going to be undefined.

```js
function introduction(name = "John", age, occupation, city) {
  console.log(
    `Hello I'm ${name}, I'm a ${age} year-old ${occupation} from ${city}`
  );
}

introduction(); // Hello I'm John, I'm a undefined year-old undefined from undefined
```

```js
function introduction(name = "John", age, occupation, city) {
  console.log(
    `Hello I'm ${name}, I'm a ${age} year-old ${occupation} from ${city}`
  );
}

introduction("Karl"); // Hello I'm Karl, I'm a undefined year-old undefined from undefined
```

>[!info]
>Notice how default parameters do not change the order in which parameters can be passed. In fact, there is no native approach in JavaScript that allows you to pass parameters in a different order from the one in which they were defined, although there are some workarounds for this with [[JavaScript Objects]].

Lastly, the [[JavaScript spread operator]] allows you to spread an iterable into multiple parameters.

```js
function customLogger(...messages) {
  const prefix = "[LOG]";

  // Loop through each message
  for (let message of messages) {
    console.log(`${prefix} ${message}`);
  }
}

customLogger("Server started", "Listening on port 8080", "Another one!");

// [LOG] Server started
// [LOG] Listening on port 8080
// [LOG] Another one!
```

