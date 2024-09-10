React Router is a library for [[React]] that lets you handle navigation in React. In order to use React Router, first it's needed to install the dependency through:

```
npm install react-router-dom
```

A basic setup using React Router would look like this:

```jsx
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Home from './Home';
import About from './About';
import Contact from './Contact';

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </Router>
  );
}

export default App;
```

Let's see what's happening here:

- We're importing three components from the React DOM library: BrowserRouter, Route and Routes, while setting Router as an alias to BrowserRouter, a common practice to keep the code clean.
- We're wrapping our Routes inside two components: Router and Routes. Router works in order to sync the UI with the current link of the page. You can write other JSX components inside the Router component along with the Routes component, inside which you can define the routes for your application.
- We're defining the routes for the application through the Route component. Each defined route assigns an URL to a specific element. When on some specific URL, the associated element defined for it will be rendered.

All of this allows you to create a multi-page application that behaves just like a single page application.

>[!info]
>By defining a route with `*` as its path as the last route, you implement a behavior in which whenever going to a random page that element is rendered. This is useful to create friendly error pages inside your domain.

