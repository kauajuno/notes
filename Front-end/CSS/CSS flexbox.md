The main thing about flexbox is layout. It's the easiest way to setup layouts in your application as it allow to control the spacing of elements through properties that can be applied either to the container or to the items in that container. It is ideal to organize the layout of components and medium or small scale layouts. For bigger scale layouts, [[CSS grid]] is more recommended as it allows more complex layouts.

# Container properties

In order to start using flexbox, you need to have a container with items, which is basically any major component of a web application. A navigation bar is a container with items, a footer is a container with items, a card is a container with items, the possibilities are quite a lot.

Let's start by learning the properties we apply to containers, as they allow to manipulate every item of the container at once.

## Applying flexbox

Use `display: flex` on a container to start applying flexbox styling to it.

In flexbox, items are organized according to an axis, which is defined through the `flex-direction` property. By default, the value of this property is set to `row`, meaning that the items will be organized in a row-like layout, horizontally. That value can also be set to `column`.

Let's see some flexbox in action with what we've learned so far. I want to style the following boxes horizontally.

<div style="background-color: #303030">
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 300px;
          width: 100px;
          border: 2px solid yellowgreen;
          border-radius: 25px;
        "
      ></div>
</div>

By just applying `display: flex` this layout can be achieved.

<div style="display: flex; background-color: #303030">
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 300px;
          width: 100px;
          border: 2px solid yellowgreen;
          border-radius: 25px;
        "
      ></div>
    </div>

## Wrapping the content

Sometimes, when there is a lot of items in a horizontal container, it might break the layout if nothing is done about it. By default, items shrink to fit the screen.

<div style="display: flex; background-color: #303030">
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 300px;
          width: 100px;
          border: 2px solid yellowgreen;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 300px;
          width: 100px;
          border: 2px solid yellowgreen;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 300px;
          width: 100px;
          border: 2px solid yellowgreen;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 300px;
          width: 100px;
          border: 2px solid yellowgreen;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
</div>

There's ways around it. An alternative provided by flexbox is the `flex-wrap` property, which when set to `wrap` works like breaking a line in text: when maximum width is achieved, items try to fit right below the current axis

<div style="display: flex; background-color: #303030; flex-wrap: wrap">
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 300px;
          width: 100px;
          border: 2px solid yellowgreen;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 300px;
          width: 100px;
          border: 2px solid yellowgreen;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 300px;
          width: 100px;
          border: 2px solid yellowgreen;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 300px;
          width: 100px;
          border: 2px solid yellowgreen;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
</div>

>[!info]
>The `flex-flow` property combine both `flex-direction` and `flex-wrap` properties. Thus it's possible to use something like `flex-flow: column wrap` without any problem.

## Aligning items

To control the aligning of all the items of a container, there are two main properties, which are `justify-content` and `align-items`.

The `justify-content` property aligns the items according to the main axis, and `align-items` according to the cross-axis. It's okay if you can't visualize it happening yet, we'll get through the examples.

- Using `flex-direction: row`, `justify-content: space-between` and `align-items: flex-end`.

<div style="display: flex; justify-content: space-between; align-items: flex-end; background-color: #303030">
      <div
        style="
          height: 100px;
          width: 100px;
          border: 2px solid chocolate;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 200px;
          width: 100px;
          border: 2px solid aquamarine;
          border-radius: 25px;
        "
      ></div>
      <div
        style="
          height: 300px;
          width: 100px;
          border: 2px solid yellowgreen;
          border-radius: 25px;
        "
      ></div>
</div>

As the `flex-direction` is set to row, the main axis is horizontal, so `justify-content` works here putting the most space possible between each of the elements, while `align-items` applies on the cross-axis, which is vertical, to align the items to the end of the cross-axis, which is the bottom of the container.

Both of the presented properties can have lots of different values assigned to them, but the main ones are:

- `justify-content`
	- `flex-start` (default)
	- `flex-end`
	- `center`
	- `space-between`
	- `space-around`
- `align-items`
	- `stretch` (default)
	- `flex-start`
	- `flex-end`
	- `center`

## Spacing between the items

After using `space-between` putting space between items in a flexbox container doesn't sound like a problem at all. However, the spacing provided by it changes according to the size of the container. It's frequently a necessity to give the items a fixed amount of space in between them.

And there's the `gap` property. It is very simple: the value attributed to `gap` will be the value of spacing applied between each of the items. The gap is applied both between the elements in the same axis and between the elements in the cross axis. To specify different gaps for rows and columns, the properties `row-gap` and `column-gap` can be used, or two values can be attributed to `gap`, the first being the `row-gap` and the second being the `column-gap`.

# Item properties

Sometimes it's desired to have an item to follow a different pattern than the one applied to all the items in a container. That's where item properties shine.

## 