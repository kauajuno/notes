Understanding how to tag exactly what you want to style is essential when working with CSS, and it has a lot of possibilities on it.

# Universal selector

The universal selector targets all the elements, is mostly used in order to set a default style or "reset" the default styling provided by the web browser that applies to most of the elements, such as `padding` and `margin`.

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

# Basic selectors

We'll be classifying basic selectors as the ones that do not have any nuance to them and are pretty much self-explanatory.

## Type selector

Selects elements of a given type:

```css
p {
  color: blue;
}
```

## Id selector

Selects the element with a given ID:

```css
#unique {
  background-color: yellow;
}
```

## Class selector

Selects the elements with a given class:

```css
.example {
  font-size: 14px;
}
```

# Combining selectors

Combining selectors is the way used to target elements using two or more identifiers that the element must have at the same time. To use it, you just need to specify the identifiers without separating them with a space:

```css
.box.link#unique{
  text-decoration: none;
}
```

You can also combine selectors in order to target all the elements that have a set of different identifiers to apply style common to all of them. To do this, you need to separate the identifiers with a comma:

```css
.box, .link, #unique{
  text-decoration: none;
}
```

Basically, the first way targets all elements which correspond to all of the identifier at the same time, and the second targets all elements which correspond to at least one of them.

# Combinators

Combinators are used when you want to target elements based on more than one property of it (type, id or class). As these ones aren't exactly as self-explanatory as the basics, we'll be using examples to ensure the understanding.

In order to visualize the effects, use the following setup:

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      body {
        height: 100vh;
      }

      .box {
        display: flex;
        height: 50%;
        width: 50%;
        border: 2px solid white;
        padding: 8px;
      }

      .one {
        background-color: red;
      }

      .two {
        background-color: blue;
      }

      .three {
        background-color: green;
      }
    </style>
  </head>
  <body>
    <div class="box one">
      <div class="box two">
        <div class="box three"></div>
        <div class="box three"></div>
        <div class="box three"></div>
      </div>
    </div>
    <div class="box one">
      <div class="box three">
        <div class="box three"></div>
        <div class="box two"></div>
        <div class="box three"></div>
      </div>
    </div>
    <div class="box two"></div>
    <div class="box three"></div>
  </body>
</html>
```

## Descendant selector

The descendant selector selects all elements that are descendant of specified elements. Apply the following style to the bottom of the style tag provided at the [[#Combinators|start of this section]].

```css
.one .two {
  background-color: yellow;
}
```

Notice how it affects classes with the `.two` element no matter what as long as it's a descendant of a `.one` element in some degree.

This effect can be applied using more identifiers:

```css
.one .two .three {
  background-color: yellow;
}
```

Notice how order matters: it will affect a `.three` element as long as it is a descendant of a `.two` element that is a descendant of a `.one` element.

## Child selector

The child selector works similarly to the descendant selector, but it only applies if the targeted element is a direct children of the previous given element. For example:

```css
.one > .two {
  background-color: yellow;
}
```

When applying this to the [[#Combinators|provided code]], you can notice that it only applies if the `.two` element is a direct children of the `.one` element.

This can also be chained to do more complex targeting:

```css
.one > .two > .three {
  background-color: yellow;
}
```

## Adjacent sibling selector

Targets elements that are immediately preceded by other type of specified element:

```css
.two + .three{
  background-color: yellow;
}
```

By using the [[#Combinators|code provided]], is easier to notice that whenever a `.three` element is preceded by a `.two` element it is affected by this targeting.

This effect cannot be chained.

## General sibling selector

Targets all elements that are siblings of a specified element:

```css
.two ~ .three{
  background-color: yellow;
}
```

This effect also cannot be chained.

## Quick note

>[!info] Addressing the meaning of sibling
>As you might've noticed if following the [[#Combinators|code sample given]], CSS siblings are only the elements that come right **after** some other element in the [[DOM]]. If an element is preceded by `x` elements and followed by `y` elements, the `x` elements are not considered siblings in relation to the mentioned element, while the `y` elements are all considered siblings.

>[!info] Chaining
>Some of the effects which are said to be impossible to chain can in fact be chained, but sometimes it might lead to unexpected behaviors, so it must be avoided.

# Pseudo-classes and pseudo-elements

Selecting through pseudo-classes basically means selecting an element based on the current state of it. The most known pseudo-class is `hover`, so we'll use it as an example:

```css
.button:hover{
  background-color: yellow;
  color: black;
}
```

Selecting pseudo-elements is kind of self-explanatory if you're familiar with pseudo-elements, it... selects a pseudo-element (wow!):

```css
.button::after{
  content: "Hey";
}
```

>[!info]
>You always use `:` for pseudo-classes and `::` for pseudo-elements.

As this concept is quite complex, you can understand it fully [[CSS pseudo-classes and pseudo-elements|here]].

# Attribute selectors

Last but not least, we have attribute selectors, which can select elements based on its attributes.

Let's start simple, to target every element on a document that has a class, you could use:

```css
[class]{
  border: 1px solid red;
}
```

And that works for basically any attribute that an HTML tag can carry, such as `type`, `value`, etc.

But when it comes to targeting only elements that have an attribute set to a certain value, such as form input elements that have its `type` set to `text`, is it possible? Yes, easily:

```css
[type="text"]{
  border: 1px solid red;
}
```

But what if I only want that behavior to be applied to a certain form on the screen and keep the others free from it, can I specify an identifier too? Of course! Look:

```css
.special-input[type="text"]{
  border: 1px solid red;
}
```

