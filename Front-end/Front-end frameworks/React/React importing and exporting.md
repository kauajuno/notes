The main idea of react is having reusable components that are much easier to organize as you can reference a component composed of multiple lines of code through a single tag. But how is it done in fact?

Let's suppose you have an `App.js` file, which will export the `App` component. This component is composed by three other ones: `Header`, `Content` and `Footer`.

Let's start with `Header`.

```jsx
// App.js
import "./App.css";

function App() {
  return (
    <Header/>
  );
}

export default App;

```

This will give you an error, because React doesn't know where you are pulling this Header component from. In order for it to work, you need to import the Header component from its own file. Let's suppose you store your components inside a folder called "components", where each component is in a folder with its own name. The import would look like this:

```jsx
// App.js
import "./App.css";
import Header from "./components/Header/Header";

function App() {
  return <Header />;
}

export default App;
```

This import is only being possible because, on the `Header.js` file, a Header component is also being exported through `export default`.

Now it's just following the same pattern with the other components, remembering to wrap them inside some tag as [[JSX return statements allow only a single tag to be returned at a time]].

```jsx
import "./App.css";
import Header from "./components/Header/Header";
import Content from "./components/Content/Content";
import Footer from "./components/Footer/Footer";

function App() {
  return (
    <>
      <Header />
      <Content />
      <Footer />
    </>
  );
}

export default App;
```

>[!info]
>Notice how `App` is also being exported, as it will be imported somewhere else in order for it to be rendered.

