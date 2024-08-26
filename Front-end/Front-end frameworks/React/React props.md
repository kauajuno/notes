Props are basically properties that components use to exchange information. Props are passed by the parent component and read by the child component.

Let's suppose I have two `Card` components, and I want to provide different information to each of them, such as the name and the image that will be displayed.

First I need to pass these information to the `Card` components.

```jsx
// App.js

import Card from "./components/Card/Card";

function App() {
  return (
    <>
      <Card
        imgUrl={
          "https://fearandhunger.wiki.gg/images/d/d9/Marina_Fear_and_Hunger_portrait.png"
        }
        name={"Marina"}
      />
      <Card
        imgUrl={
          "https://fearandhunger.wiki.gg/images/c/c0/Abella_Gro-goroth_portrait.png"
        }
        name={"Abella"}
      />
    </>
  );
}
```

Then I'm receiving them in the child components and using them as necessary.

```jsx
// Card.jsx

function Card({ name, imgUrl }) {
  return (
    <div className="container-card">
      <div className="container-description">
        <img src={imgUrl} alt="" />
        <h1>{name}</h1>
      </div>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Inventore
        reprehenderit ea provident similique facilis odio autem repellendus
        dignissimos quod quia deleniti vitae natus officia magni possimus,
        explicabo exercitationem eos nostrum?
      </p>
    </div>
  );
}

export default Card;
```

Alternatively, a single props object could be received and manipulated accordingly inside the child component:

```jsx
// Card.jsx

function Card(props) {
  return (
    <div className="container-card">
      <div className="container-description">
        <img src={props.imgUrl} alt="" />
        <h1>{props.name}</h1>
      </div>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Inventore
        reprehenderit ea provident similique facilis odio autem repellendus
        dignissimos quod quia deleniti vitae natus officia magni possimus,
        explicabo exercitationem eos nostrum?
      </p>
    </div>
  );
}

export default Card;
```

However, it is considered good practice to de-structure your props inside the child component given the following reasons:

- Improved readability: code is way easier to read.
- Cleaner code: reduces code repetition.
- Allows [[JavaScript functions#Parameters|default values]]: default values can be provided to be assigned just in case none are passed through the props.
- Easier identification: sometimes not all props are used by the component, making it easier to understand which are used and why.

# Children props

In the same way HTML tags are frequently nested, **react components can also be nested**. Let's take the example from above: what if I though it would be better to separate a component specifically for the photo and name in the card and call it `Avatar`? Then `Avatar` would be inside of `Card`.

```jsx
// App.js

function App() {
  return (
    <>
      <Card>
        <Avatar
          imgUrl={
            "https://fearandhunger.wiki.gg/images/d/d9/Marina_Fear_and_Hunger_portrait.png"
          }
          name={"Marina"}
        />
      </Card>
      <Card>
        <Avatar
          imgUrl={
            "https://fearandhunger.wiki.gg/images/c/c0/Abella_Gro-goroth_portrait.png"
          }
          name={"Abella"}
        />
      </Card>
    </>
  );
}
```

Technically, what's happening here is: `Avatar` is being passed as a prop to `Card`. To access it inside of the `Card` component, we must refer to the `children` prop.

```jsx
function Card({ children }) {
  return (
    <div className="container-card">
      {children}
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Inventore
        reprehenderit ea provident similique facilis odio autem repellendus
        dignissimos quod quia deleniti vitae natus officia magni possimus,
        explicabo exercitationem eos nostrum?
      </p>
    </div>
  );
}
```
