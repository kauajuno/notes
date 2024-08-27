Conditional rendering happens when, depending on the context, different things will be rendered from the same component.

Let's use a to-do list as an example. We'll have two main components: `TodoList` and `Item`. The first will be a container for the instances of the second.

```jsx
function TodoList() {
  return (
    <ul>
      <Item name={"Do laundry"} completed={false} />
      <Item name={"Pick bf up at the U"} completed={true} />
      <Item name={"Do the dishes"} completed={false} />
      <Item name={"Check on the neighbor"} completed={false} />
      <Item name={"Water my little plants"} completed={true} />
    </ul>
  );
}
```

The intention here is already clear: I want to render something different in order to show whether an item of the list is completed or not.

A way of doing this would be through a simple conditional like `if`:

```jsx
function Item({ name, completed }) {
  let itemName = name;
  if (completed) {
    return (
      <li>
        {itemName} + " ✔️"
      </li>
    );
  }
  return <li>{itemName}</li>;
}
```

Let's suppose you don't want to display the components at all in case they are already completed. You could just return null:

```jsx
function Item({ name, completed }) {
  let itemName = name;
  if (completed) {
    return null;
  }
  return <li>{itemName}</li>;
}
```

Back to the other case, there's a way to simplify it by using ternary operator:

```jsx
function Item({ name, completed }) {
  let itemName = name;

  return <li>{completed ? itemName + " ✔️" : itemName} </li>;
}
```

In a similar analogy to curly brackets being windows to JavaScript, it's possible to say that parentheses are windows to JSX. This allows you to write more complex JSX inside the conditionals.

```jsx
function Item({ name, completed }) {
  return (
    <li>
      {completed ? (
        <>
          {name} <span style={{ color: "green" }}> [[COMPLETED]]</span>
        </>
      ) : (
        name
      )}
    </li>
  );
}```

It's possible to simplify it EVEN more through the logical operator `&&`:

```jsx
function Item({ name, completed }) {
  return (
    <li>
      {name}
      {completed && <span style={{ color: "green" }}> [[COMPLETED]]</span>}
    </li>
  );
}
```