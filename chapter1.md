#Chapter 1 - The Box Model

## Intro

Opening a webpage as an amateur web developer and trying to understand it's design structure can
be a daunting task.  To the untrained eye, web pages may appear to lack clear organizational structure.
"How are there buttons next to this article?", "How does this text seem to fit around this image?",
"Why isn't my new row of data aligned underneath my first?" are all questions likely to strike a novice
designer.  The key to understanding all of these questions, and many more, is the CSS box model.

[According to MDN.](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing)
>The CSS box model is the foundation of layout on the Web — each element is represented as a rectangular box, with the box's content, padding, border, and margin built up around one another like the layers of an onion. As a browser renders a web page layout, it works out what styles are applied to the content of each box, how big the surrounding onion layers are, and where the boxes sit in relation to one another. Before understanding how to create CSS layouts, you need to understand the box model.

Here is an image of the box model.

<div align="center">
  <a href="https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model">
    <img src="https://raw.githubusercontent.com/ALMaclaine/box-model-book/master/assets/img/wlarrows.png">
  </a>
</div>

As you can see, the entire space of an element is composed of its content dimensions,
its padding, its border and its margin.

The formulas for caclulating the actual widths and lengths are

Width

- width  + padding-left + padding-right + border-left + border-right

Height

- height + padding-top + padding-bottom + border-top + border-bottom

<div align="center">
  <a href="http://blog.teamtreehouse.com/box-sizing-secret-simple-css-layouts#comment-50223">
    <img src="https://raw.githubusercontent.com/ALMaclaine/box-model-book/master/assets/img/box-model.png">
  </a>
</div>

If any of the values are left undeclared then they default to the browser and unlikely to be 0,
using a css reset will set all of these properties to a default values of 0.

The box model has a number of finer details that can be hard to pin down if you
aren't looking for them.  One of the more interesting details of the box model
is that it behaves differently depending on whether the width is explicitly set.

[From Chris Coyier](https://css-tricks.com/the-css-box-model/#article-header-id-1)
>If you don't declare a width, and the box has static or relative positioning, the width will remain 100% in width and the padding and border will push inwards instead of outward. But if you explicitly set the width of the box to be 100%, the padding will push the box outward as normal... But if you explicitly set the width of the box to be 100%, the padding will push the box outward as normal.

<div align="center">
  <a href="https://quirksmode.org/css/user-interface/boxsizing.html">
    <img src="https://raw.githubusercontent.com/ALMaclaine/box-model-book/master/assets/img/widths.gif">
  </a>
</div>

Absolute Elements

While block level elements take up the entire width of the screen by default, absolute boxes do not. By default they only expand to fit their content.

[From Chris Coyier](https://css-tricks.com/the-css-box-model/#article-header-id-2)
>Absolutely positioned boxes that have no width set on them behave a bit strangely. Their width is only as wide as it needs to be to hold the content. So if the box contains a single word, the box is only as wide as that word renders. If it grows to two words, it'll grow that wide. This should continue until the box is 100% of the parent's width (the nearest parent with relative positioning, or browser window) and then begin to wrap. It feels natural and normal for boxes to expand vertically to accommodate content, but it just feels strange when it happens horizontally. That strange feeling is warranted, as there are plenty of quirks in how different browsers handle this, not to mention just the fact that text renders differently across platforms.

Keep in mind that floated boxes behave in the same manner.

Inline Elements

It's important to note that inline elements are boxes too. They create boxes of their own
and sit next to other inline elements until their widths expand past the break point.

[From Chris Coyier](https://css-tricks.com/the-css-box-model/#article-header-id-4)
>We've been kind of focusing on boxes as block-level elements here. It's easy to think of block-level elements as boxes, but inline elements are boxes too. Think of them as really really long and skinny rectangles, that just so happen to wrap at every line. They are able to have margin, padding, borders just like any other box.


If you want to visualize all the boxes in your design, a cool trick to see every box on the screen is as follows

```css
* { 1px solid red !important; }
```
