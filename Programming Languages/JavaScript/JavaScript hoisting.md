Hoisting is a phenomenon in which the JavaScript interpreter appears to move specific lines of code to the top of the file before executing it.

# Imports and functions

Starting with imports is a nice way to go.

```js
// function.js file
function greet(name) {
  console.log(`Hello ${name}!`);
}

export default greet;
```

```js
// index.js file

greet("John Doe"); // Hello John Doe!

import greet from './function.js';
```

Why does this work? the function greet is being used before it is even imported into the file. It seems like it, but the interpreter does something else called **hoisting** behind the curtains.

When the JavaScript interpreter detects an import, it allows you to use it even before the line it is wrote in, just like if it was moved to the top of the file.

The same behavior happens to [[JavaScript functions|functions]], as the interpreter would hoist the declaration of the function to the top of its scope.

```js
greet("John Doe"); // Hello again, John Doe

function greet(name) {
  console.log(`Hello again, ${name}`);
}
```

# var, let and const

Hoisting with variables have a different behavior than with imports and functions. Actually, hoisting with variables differ between themselves depending on how they are declared.

## [[JavaScript variables#Declaring with `var`|var]]

```js
function greet() {
  console.log(greetUsed);
  var greetUsed = "Hello!";
}

greet(); // undefined
```

Note that, despite not working as intended, the code doesn't throw any error. When declaring with var, you're allowed to reference it without any error, but the value will always be `undefined` before initializing.

>[!info]
>Remember that the use of `var` is currently discouraged.

## [[JavaScript variables#Declaring with `let`|let]] and [[JavaScript variables#Declaring with `const`|const]]

Some consider this hoisting, some does not. There's not exactly an agreement on what is hoisting and what is not, so this one can divide opinions as it is ambiguous. The fact is that it implies in altered behavior.

```js
const x = 1;
{
  console.log(x);
}
```

The code above works just fine, as the log statement can access the x variable from the outer scope.

However, this one throws an error:

```js
const x = 1;
{
  console.log(x);
  const x = 2;
}
```

As the variable taken into consideration is the one in then same scope as the log statement.

>[!info]
>When considered hoisting, this type of hoisting is called hoisting with time dead zone restriction.

# Classes

Class hoisting has the exact same behavior as [[#JavaScript variables Declaring with `let` let and JavaScript variables Declaring with `const` const|let and const hoisting]].