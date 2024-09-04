In order to display elements in the screen, React needs to render it. This rendering action needs to be triggered by something, then the component will be rendered and committed to the DOM. Let's understand in detail what in fact happens in the rendering process.

# Trigger

The first thing is: renders need to be triggered somehow. The first render is triggered by the root element itself, which contains basically everything.

```jsx
createRoot(document.getElementById("root")).render(
  <StrictMode>
    <App />
  </StrictMode>
);
```

Further renders are queued whenever a [[React state|state]] of a component is changed. 

# Render

Rendering is a hierarchical functionality. When a component is rendered, if it returns any other component, they will also be rendered. This means that the only time that the entire application will necessarily be rendered is in the first render, where React renders the root itself. Any other render will be applied only to the component whose state triggered the render and its children.

# Commit

In the first render, React basically uses the [[DOM]] API method `appendChild` to set all the elements where they need to be. Further renders use the minimal necessary operations.