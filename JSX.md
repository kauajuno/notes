JavaScript XML is a syntax extension for JavaScript that looks a lot like HTML, but it has some key differences.

# Returning a single element

In JSX, functions are used to return markup. In the return statement, only a single tag shall be returned at a time. It doesn't mean that a tag can wrap other tags and be returned.

```jsx
function App() {
  return (
    <>
      <Header />
      <Content />
      <Footer />
    </>
  );
}
```

The wrapper tag above is called a fragment. By giving no name to a tag, it becomes a fragment, which does not leave a trace in the browser HTML tree, so it's effectively like returning all their children at once.

# Attributes with camelCase

There are attributes that are common in HTML that can't be directly transferred to JavaScript. The greatest example of this is `class`. The equivalent of a HTML/CSS class in JavaScript can't be called class because of the keyword that represents [[JavaScript classes]], so there's `className` to represent it instead.

This pattern in camelCase also applies to some HTML attributes that come with two or more words, such as `stroke-width` becoming `strokeWidth`. 

The only cases in which the pattern of using dashes is maintained is with `data-*` and `aria-*`.

# Closing all the tags

All tags in a markup block that is being return must be closed in that same markup block. This affects even classes that don't need to be closed in HTML, such as `<img>`, implying the need of **self-closing tags** such as `<img/>`.