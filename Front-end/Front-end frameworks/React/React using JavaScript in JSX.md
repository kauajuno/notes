It's frequently useful to use some JavaScript inside the markup. In order to use JavaScript inside the JSX markup, it's possible to "open a portal", or, in less fancy words, open curly brackets.

```jsx
function Header() {
  const siteName = "etermentales";
  return (
    <nav>
      <h1>{siteName.toUpperCase()}</h1>
      <ul id="nav-items">
        <li>FAQ</li>
        <li>Contacts</li>
      </ul>
    </nav>
  );
}
```

# Where to use curly brackets

Curly brackets are mainly used in two situations:

- Text: directly inside a JSX tag.
- Attribute: as an attribute passed to a JSX tag such as `src` in the `<img>` tag.
- Objects: when using inline CSS to style a tag, for example, you use two pairs of curly brackets: one to explicit the use of JavaScript and other to reference a JavaScript object.

```jsx
// here you can see all examples above in action
function Header() {
  const siteName = "etermentales";
  const headerImage =
    "https://upload.wikimedia.org/wikipedia/en/3/3b/SpongeBob_SquarePants_character.svg";
  return (
    <nav style={{ backgroundColor: "#000000", color: "#FFFFFF" }}>
      <h1>{siteName.toUpperCase()}, the site</h1>
      <ul id="nav-items">
        <li>
          <img src={headerImage} style={{ width: "40px" }} alt="" />
        </li>
        <li>FAQ</li>
        <li>Contacts</li>
      </ul>
    </nav>
  );
}
```

