The `this` keyword in JavaScript is used to refer to an object, and the object it will refer to depends completely on the context in which the keyword is being used.

# In a method

When used in [[JavaScript classes#Methods|methods]], the keyword will refer to the calling object.

```js
class Counter {
  val = 0;

  count() {
    this.val++;
  }

  check() {
    console.log("Current value is " + this.val);
  }
}

const counter = new Counter();

counter.count();
counter.count();
counter.count();
counter.check(); // Current value is 3
```

In the example above, every time count is called, the property `val` of the calling object `counter` is increased by one, as the `this` keyword refers to `counter`.

>[!info]
>This is essential for the understanding of how [[JavaScript method chaining]] works.

# In a function

When used in a function, the `this` keyword will refer to the global object.

```js
function showGlobalObject() {
  console.log(this);
}

showGlobalObject(); // In a browser, this will log the `window` object
```

# In an arrow function

When used in an arrow function, the `this` keyword will refer to the parent object.

# In an event handler

When used in an event handler, the `this` keyword will refer to the element that received the event.