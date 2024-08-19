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
- [[JavaScript IIFEs|Immediatly invoked function expressions]]: allows you to create a function that will be executed right after, creating a private scope for variables and functions within them. 
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
