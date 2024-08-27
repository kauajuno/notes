Event handlers aren't something that belongs specifically to React, in fact when learning JavaScript event handlers are one of the main topics as they deliver interactivity through relatively simple logic. The main point about learning how to deal with event handlers in React is that often need to pass it as props from a component to the other.

Let's make a simple button at first.

```jsx
function Button() {
  function eventHandler() {
    alert("Oh hey what's up");
  }

  return <button onClick={eventHandler}>Click me!</button>;
}
```

This is really simple. Event handlers also have access to the props as they are inside of the component.

```jsx
function App() {
  return (
    <>
      <Button message="Believe in your dreams!" />
    </>
  );
}
```

```jsx
function Button({ message }) {
  function eventHandler() {
    alert(`Message of the day: ${message}`);
  }

  return <button onClick={eventHandler}>Click me!</button>;
}
```

Working the other way around, event handlers can be passed as callback functions through props too. 

```jsx
function App() {
  return (
    <>
      <Button
        eventHandler={() => {
          alert("Nah that's crazy");
        }}
      />
    </>
  );
}
```

```jsx
function Button({ eventHandler }) {
  return <button onClick={eventHandler}>Click me!</button>;
}
```

Event propagation in react works just the same as in JavaScript. If a child element catches an event, the event "bubbles up" through the DOM tree. Let's create a `ToolBar` component that is composed by two `Button` components.

```jsx
function App() {
  return (
    <ToolBar
      onClick={() => {
        alert("clicked the toolbar");
      }}
    >
      <Button
        onClick={() => {
          alert("clicked button 1");
        }}
      />
      <Button
        onClick={() => {
          alert("clicked button 2");
        }}
      />
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
function Button({ onClick }) {
  return <button onClick={onClick}>Click me!</button>;
}
```

When using the components as above, the `Button` component is the first one to catch the event, so its message will be exhibited first. Then the event propagates up, and the `ToolBar` also catches the event and shows its message.

If this is an unwanted behavior, it's simple to stop the propagation.

```jsx
function App() {
  return (
    <ToolBar
      onClick={() => {
        alert("clicked the toolbar");
      }}
    >
      <Button
        onClick={(e) => {
          e.stopPropagation();
          alert("clicked button 1");
        }}
      />
      <Button
        onClick={(e) => {
          e.stopPropagation();
          alert("clicked button 2");
        }}
      />
    </ToolBar>
  );
}
```