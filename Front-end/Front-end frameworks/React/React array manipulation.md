It's frequently useful to manipulate an array of data and somehow display it in a component. This manipulation is done through array methods such as `filter` and `map`.

Let's make use of the following example: you have a collection of data such as this:

```jsx
export const terminaCharacters = [
  {
    name: "Marina",
    alignment: "Good",
    imgUrl: "https://fearandhunger.wiki.gg/images/c/cb/Marina_overworld.png",
  },
  {
    name: "Daan",
    alignment: "Good",
    imgUrl: "https://fearandhunger.wiki.gg/images/6/62/Daan_overworld.png",
  },
  {
    name: "Ghoul",
    alignment: "Evil",
    imgUrl:
      "https://fearandhunger.wiki.gg/images/c/c6/Villager_%28Sickle%29_overworld.png",
  },
  {
    name: "Tanaka",
    alignment: "Good",
    imgUrl: "https://fearandhunger.wiki.gg/images/f/f1/Tanaka_overworld.png",
  },
  {
    name: "Caligula",
    alignment: "Evil",
    imgUrl: "https://fearandhunger.wiki.gg/images/9/94/Caligura_overworld.png",
  },
  {
    name: "Pavel",
    alignment: "Evil",
    imgUrl: "https://fearandhunger.wiki.gg/images/2/24/Pav_overworld.png",
  },
  {
    name: "Abella",
    alignment: "Good",
    imgUrl: "https://fearandhunger.wiki.gg/images/8/8a/Abella_overworld.png",
  },
];
```

This is an array of objects containing information about characters from the game [Fear and Hunger 2: Termina](https://indiehellzone.com/2024/01/02/fear-hunger-2-termina/). I want to make a simple unordered list from this collection, but good lord would it be time-consuming to create an `Item` component and pass each of these as props to it, you're probably wishing right now that there was a faster way. And in fact, there is.

```jsx
function List() {
  const mappedCharacters = terminaCharacters.map((element) => {
    return (
      <li key={crypto.randomUUID()}>
        <h1>{element.name}</h1>
        <img src={element.imgUrl} alt="" />
      </li>
    );
  });

  return <ul style={{ listStyleType: "none" }}>{mappedCharacters}</ul>;
}
```

This will work beautifully. However there is one thing here that may be intriguing, what is that `key` attribute in the `<li>` tag? Well, if you take it out the application will still be working, but you'll see an error either on the CLI or in the web developer tool's console indicating that each list item should have an unique key prop. But why is that? The application seems to work just fine. This is specially necessary when you're dealing with interactions that can change the position of the items in the array, enabling React to understand what is happening in fact and render them correctly. Ideally, this identifier data should come along with the data itself, experiment inserting an id field with an unique value for each of the objects in your collection.

Now let's suppose we want to show only the evil characters. To do that, the `filter` method can be used before mapping the list elements to JSX:

```jsx
function List() {
  const evilCharacters = terminaCharacters.filter(
    (character) => character.alignment === "Evil"
  );
  const mappedCharacters = evilCharacters.map((element) => {
    return (
      <li key={crypto.randomUUID()}>
        <h1>{element.name}</h1>
        <img src={element.imgUrl} alt="" />
      </li>
    );
  });

  return <ul style={{ listStyleType: "none" }}>{mappedCharacters}</ul>;
}
```

