Classes are the core concept of [[Object-Oriented Programming]]. To create a class in JavaScript, it's as simple as that:

```js
class Car{
  
}
```

Let's put some things inside this class, shall we?

# Methods

A method is a block of code that works almost the same as a function, but it needs a class or an instance of a class to be invoked.

```js
class Car {
  constructor(model, color, year) {
    this.model = model;
    this.color = color;
    this.year = year;
  }

  start() {
    console.log(`${this.model} is now running.`);
  }
}

const myCar = new Car("Creta", "Grey", 2021);
myCar.start();
```

Right above there's a class Car with two methods, `constructor` and `start`.

The first one is a special method, note that `constructor` is a reserved keyword, because it constitutes a block of code that will be executed every time an object instance of that class is initialized. When `new Car` is invoked, a new object of that class is being created through the use of the constructor method. This method, although very important, is not necessarily required. If you don't provide a constructor method, JavaScript will use the default one, which is an empty constructor like `constructor(){}`. However, this won't happen if the class has a [[superclass]]. Don't worry about the content of the constructor defined above as we will cover [[#Properties|properties]] next.

The second one, on the other hand, is just a generic method. It could have any other name, such as `startEngine` or `drive`, these methods just execute the code inside of them without some gimmick happening behind the curtains.

# Properties

Properties are data that define the instance of a class. Let's use the same example:

```js
class Car {
  constructor(model, color, year) {
    this.model = model;
    this.color = color;
    this.year = year;
  }

  start() {
    console.log(`${this.model} is now running.`);
  }
}

const myCar = new Car("Creta", "Grey", 2021);
myCar.start();
```

In this example, there are three properties: model, color and year. Each instance can have its own model, color and year. It's also possible to have multiple objects that share the exact same properties without making them the same object.

Properties can have a default value, it can be defined either in the constructor via default parameters or directly in the class.

```js
class Car {
  constructor(model = "Subaru", color = "Sky blue", year = 2001) {
    this.model = model;
    this.color = color;
    this.year = year;
  }

  start() {
    console.log(`${this.model} is now running.`);
  }
}

class ToyotaCar {
  // property defined directly in the class
  model = "Toyota";

  constructor(color, year){
    this.color = color;
    this.year = year;
  }

  start() {
    console.log(`${this.model} is now running.`);
  }
}

const myCar = new Car("Creta", "Grey", 2021);
const defaultCar = new Car();
const toyotaCar = new ToyotaCar("Light purple", 1996);
myCar.start(); // Creta is now running.
defaultCar.start(); // Subaru is now running.
toyotaCar.start(); // Toyota is now running.
```

# Static

The keyword static allows you to write special properties and methods.

## Static properties

As explained before, common properties, also known as instance properties, are properties that belong to an instance of some class. Static properties, on the other hand, do not belong to instances, but to the class itself.

```js
class Car {
  static totalCars = 0;

  constructor(model, color, year) {
    this.model = model;
    this.color = color;
    this.year = year;
    Car.totalCars++;
  }

  start() {
    console.log(`${this.model} is now running.`);
  }
}

const myFirstCar = new Car("Creta", "Grey", 2021);
const mySecondCar = new Car("Palio", "Dark Green", 2009);
const myThirdCar = new Car("Celta", "Black", 2006);

console.log(Car.totalCars);
```

## Static methods

Static methods work the same way: they belong to the class instead of belonging to the instance. This is extremely useful in cases where you shouldn't depend of a instance to invoke the method. Let's see an example:

```js
class Calculator {
  static sum(a, b) {
    return a + b;
  }

  static subtract(a, b) {
    return a - b;
  }

  static multiply(a, b) {
    return a * b;
  }

  static divide(a, b) {
    if (b === 0) throw new Error("Division by zero");
    return a / b;
  }
}

console.log(Calculator.subtract(8, 5)); // 3
```

# Other related topics

- [[JavaScript inheritance]]: inheritance is a principle of [[Object-Oriented Programming|OOP]] that allow classes to inherit properties and methods from other classes.