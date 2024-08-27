Components are the core element of react, it is through components that you build the parts of an application. And how do we create a component? Let's find out.

```jsx
import "./header.css";

function Header() {
  return (
    <nav>
      <h1>Website</h1>
      <ul id="nav-items">
        <li>FAQ</li>
        <li>Contacts</li>
      </ul>
    </nav>
  );
}

export default Header;
```

Alright, this is a component, cool. But this is very, very strange if this is your first time dealing with React code. "Why is there HTML tags being returned in a JavaScript function?", you might ask. It's a syntax called [[JSX]], which is very similar to HTML. Don't worry about it now as you can get to this topic later on, just assume that now it is possible to return markup with JavaScript.

To create components, there are three essential things that shall be done:

- Function: there's gotta be a function representing the component, it's mandatory for the name of the function to be pascal cased.
- Return: the function gotta return some markup representing the content of the component. If the return statement returns multiple lines, they have to be wrapped in parentheses, otherwise only the first line will be returned.
- Export: the component gotta be exported so it can be used as part of other component or directly rendered.

