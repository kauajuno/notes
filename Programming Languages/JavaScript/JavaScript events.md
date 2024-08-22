Events are things that happen when something happens to a [[HTML]] element. These things can be actions triggered either by the user or by the browser automatically.

# User interaction events

The most known event is the click event, which is commonly added to buttons to perform some task.

```js
const colors = ["green", "red", "blue"];

const button = document.getElementById("button");
let cont = 0;

button.addEventListener("click", () => {
  button.style.backgroundColor = colors[++cont % 3];
});

```

In the example above, every time the even **click** happens, the provided function is executed. In this case, the function changes the button background color with every click.