Let's get directly to the point. State refers to an variable that might change over the lifetime of a component. When the state changes, React triggers a re-render of the component to update the UI, reflecting the new state visually to the user. But in order for all this to work, a [[React hooks|react hook]] called [[React useState|useState]].

```jsx
const [count, setCount] = useState(0);
```

By using this, React is going to "remember" count and whenever `useState` is called it triggers a re-render.

```jsx
function App() {
  return (
    <ToolBar>
      <Button />
      <Button />
    </ToolBar>
  );
}
```

```jsx
function ToolBar({ onClick, children }) {
  return (
    <div onClick={onClick} id="tool-bar">
      {children}
    </div>
  );
}
```

```jsx
function Button() {
  const [count, setCount] = useState(0);

  return (
    <button
      onClick={() => {
        setCount(count + 1);
      }}
    >
      Counting at {count}
    </button>
  );
}
```

The example above demonstrate how state works in practice with the most classical example possible. If you try to simply define count as a simple variable and try to update its value directly through `count++` or `count = count + 1` on the event listener, it won't trigger a re-render and the component won't have any visible changes to it.

# Render queues and state snapshot

There's something that looks like flaws in the examples above that you might have notice if you're very attentive. How is `count` changing its value if we declared it with `const`? This is a very important question to have, because its answer is also much valuable.

First of all: `count` is not the value itself. It is the reference to a value. It works in the same way that you can modify the content of objects declared with const such as arrays, as long as you don't attribute another reference to it.

Second thing is: whenever `count` changes, it triggers a render, but that rendering action doesn't happen instantly: instead, it goes to a queue to be executed. Now there's an amazing insight: state works like a snapshot of your JSX. Nothing better than an example to explain it.

```jsx
function Button() {
  const [count, setCount] = useState(0);

  return (
    <button
      onClick={() => {
        setCount(count + 1);
        setCount(count + 1);
        setCount(count + 1);
      }}
    >
      Counting at {count}
    </button>
  );
}
```

Seeing this without understand how state actually works might lead you into thinking that this is the same as writing `setCount(count + 3)`, but it isn't. Changes to the state are made based on a snapshot of that same state after its last render. Now put that together with the fact that renders are queued and you got that **the exact same update to the state is being made three times**. If a render happened between each `setCount` call it would be the same as writing `setCount(count + 3)` as the snapshot would also be updated, but as it happens otherwise, it only increases count by one.

# Multiple consecutive state updates

The solution of the last topic raises another question: what if it is my intention to make multiple changes to the state between two renders? The answer to that is quite simple. When `setCount(count + 1)` is called, React queues a "replace count with count + 1" operation. But if you pass a function that does something to the state, React queues the execution of these functions and just them performs the render.

```jsx
function Button() {
  const [count, setCount] = useState(0);

  return (
    <button
      onClick={() => {
        setCount((count) => count + 1);
        setCount((count) => count + 1);
        setCount((count) => count + 1);
      }}
    >
      Counting at {count}
    </button>
  );
}
```

A better way to understand it can be experimenting with both of these operations in sequence. Assume that:

- A: `setCount(count + 1);`
- B: `setCount(count => count + 1)`

Now assume that count initial state value is `0`. The sequences of calling ahead will get the following results:

- `A -> B -> B`: `0 + 1 = 1 -> (1) => {1 + 1} = 2 -> (2) => {2 + 1} = 3`
- `A -> B -> A`: `0 + 1 = 1 -> (1) => {1 + 1} = 2 -> 0 + 1 = 1`

Notice that, in the second example, the second calling of A brings the value of count from the last snapshot and simply assign it to count, making the B calling "worthless".



