Inheritance enables the creation of hierarchy between classes in which some classes are parents and some classes are children. Child-classes inherit properties and methods from their parent-classes. Parent-classes are often called **superclasses**, and children-classes are often called **subclasses**.

```js
class Vehicle {
  constructor(engine) {
    this.engine = engine;
  }

  start() {
    console.log(`${this.engine} roars and you start moving.`);
  }
}

class Car extends Vehicle {
  turnRadioOn() {
    console.log("You're now listening to Joy Division...");
  }
}

class Motorcycle extends Vehicle {
  doWheelie() {
    console.log("Hey! That's dangerous!");
  }
}

const car = new Car("V8");
const motorcycle = new Motorcycle("Honda Pcx 150");

car.start(); // V8 roars and you start moving.
car.turnRadioOn(); // You're now listening to Joy Division...

motorcycle.start(); // Honda Pcx 150 roars and you start moving.
motorcycle.doWheelie(); // Hey! That's dangerous!
```

Notice how both `Car` and `Motorcycle` classes inherit the `start` method from `Vehicle` but still have their own methods too.

# Super keyword

The super keyword is used in JavaScript in order to refer to the constructor method of the superclass, which can spare a lot of bulky code.

```js
class Vehicle {
  constructor(engine) {
    this.engine = engine;
  }

  start() {
    console.log(`${this.engine} roars and you start moving.`);
  }
}

class Car extends Vehicle {
  constructor(engine, radioModel) {
    super(engine);
    this.radioModel = radioModel;
  }

  turnRadioOn() {
    console.log(
      `You're now listening to Joy Division... This ${this.radioModel} sounds really good!`
    );
  }
}

class Motorcycle extends Vehicle {
  constructor(engine, helmetModel) {
    super(engine);
    this.helmetModel = helmetModel;
  }

  doWheelie() {
    console.log(
      `Hey! That's dangerous! This ${this.helmetModel} better save your head!`
    );
  }
}

const car = new Car("V8", "JBL CX2");
const motorcycle = new Motorcycle("Honda Pcx 150", "Falcon 3");

car.start(); // V8 roars and you start moving.
car.turnRadioOn(); // You're now listening to Joy Division... This JBL CX2 sounds really good!

motorcycle.start(); // Honda Pcx 150 roars and you start moving.
motorcycle.doWheelie(); // Hey! That's dangerous! This Falcon 3 better save your head!
```
