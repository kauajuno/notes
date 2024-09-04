The main thing about CSS grid is complex layouts. While [[CSS flexbox]] excel at adjusting simple layouts, grid just give you way more room for creativity and creation than flexbox does. It comes at the cost of some code complexity, so it's important to evaluate which one is the ideal for the layout being constructed. It is recommended to take a peek at [[CSS flexbox]] before jumping into grid as flexbox is way simpler to use and its "flaws" explain the necessity of using grid at times.

# Grid template areas

This is definitely the easiest way of setting up a layout in CSS grid, as you quite literally "draw" the layout you want to use in a matrix. The `grid-template-areas` is a CSS property that takes the format in which you want to display some layout. You can use arbitrary names to represent everything, it doesn't necessarily need to match CSS class names or something else.

Assuming body is the container for our case:

```css
body {
  display: grid;

  grid-template-areas:
  "sidebar header"
  "sidebar main-content"
  "footer footer"
}
```

Let's apply this idea to the following page:

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <div class="sidebar">
      <h1 class="sidebar-logo">My site</h1>
      <a href="">Some link</a>
      <a href="">Some other link</a>
      <a href="">Another link</a>
    </div>
    <div class="header">
      <button>Previous page</button>
      <button>Next page</button>
    </div>
    <div class="main-content">
      <div class="card">
        <h1>Course one</h1>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit.
        </p>
        <div class="desc">Provident,
          magni assumenda, eligendi ea aperiam vero cumque, sapiente quis
          distinctio corrupti id perferendis. Vero numquam voluptate porro
          perferendis corrupti tempora culpa.</div>
        <button>Get now</button>
        <alert>Details</alert>
      </div>
    </div>
    <div class="footer">
      Copyrights and other stuff
    </div>
  </body>
</html>
```

>[!info]
>If you're experimenting with this, make sure to add other instances of the `card` element to populate the main content section.

Trying to implement this layout using flexbox will be a little bit annoying as you'll need to think about `div` tags that will be used merely to wrap other tags and apply a very simple flexbox styling to it. In grid, by using the property `grid-area` to an item in the grid, you can assign which position it should assume on the layout based on the template provided earlier.

```CSS
body {
  display: grid;

  grid-template-areas:
    "sidebar header"
    "sidebar main-content"
    "footer footer";

  grid-template-columns: auto 1fr;
}

.sidebar {
  grid-area: sidebar;
}

.header {
  grid-area: header;
}

.main-content {
  grid-area: main-content;
}

.footer {
  grid-area: footer;
}
```

And just like that the main layout of your application is set. Of course, there's lots of styling that need to be done for each item (and you'll likely need flexbox for all of them), but the main layout is already set.

"Wait! You didn't explain why you used that `grid-template-columns` property!". Sorry, my bad. This property purpose is defining the width of the columns. In this case, as we have two columns in our layout, we set the first to `auto`, so it will hug its contents; and the second to `1fr` so it will take one fraction of the rest of the space. We'll dive deeper into the meaning of this unit ahead.

What was shown above is the easiest and most common way to setup a layout with CSS grid, but you'll often come across some ideas that will require you to understand CSS grid with more depth and use the not-so-easy ways. If you're ready for that, proceed to the next topic.

>[!info] CSS flexbox vs. CSS grid
>This is a dilemma for most people that are starting with CSS, even more for those that didn't catch the main idea of each yet or didn't even try to learn both before asking this question (I'm talking to you, me from the past). There's a very simple guideline that I use when I need to know which one to use: if I'm dealing with a component whose layout only has clear columns and/or rows that go all the way from one boundary the the other, flexbox is the way to go; but if it has multiple columns and/or rows that are "cut" along its way to the other side (or maybe they don't even touch any of the sides), the grid can be a better approach.

# Fraction

The `fr` unit is frequently used in CSS grid, but what does it actually mean?

This unit takes into account how much space it has left to take over. That's basically it, and it is VERY powerful. Some might think at first that it would be no different than using percentages, and 4 columns of `1fr` width each is no different than 4 columns of `25%` width each.

Even broken clocks are right twice a day. In this case, if you're trying to layout elements with no space between them, these two would in fact be equivalent. However, try doing this directly on your body element, add 4 columns using both of these methods. Now apply a `gap` between them. Have you noticed the difference? **While percentages take a part of the total space of the container, fractions take a part of the space that has left**. This explains why, in this example, using percentages cause an overflow.

When using multiple columns and/or rows that use fraction at the same time, the name fraction starts to really make sense. Let's suppose you have the following setup for your columns: `grid-template-columns: 250px 1fr 3fr` inside a container of `width: 2250px`. The first column will take the defined `250px`. The second column will take one fraction from the total of fractions that are being used, which are four in this case, so it will take one fourth of the space left, `500px`. The third column will follow the same pattern, occupying `1500px`.