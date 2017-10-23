# Chapter 4 - Examples

## Example 1 - Default Width Behavior

The w3c box model behaves differently depending on whether width is explicitly set.
If width is explicitly set, say at 100%, then the padding and border are added outside
the element. If however, no width is set, then the border and padding are inset.

Load this <a href="./examples/ex01-default-behavior.html">example</a> file.

Looking at the code, you can see that there is no width on `.box1` but a width
of 100% on `.box2`.  Examining the html file in the browser, you can see the
padding and margin is inset for the first box, but outside the element for the second.

```css
   .box1 {
      background-color: lightblue;
      height: 25%;
      border: 20px solid orange;
   }

   .box2 {
      background-color: lightblue;
      width: 100%;
      margin-top: 5%;
      height: 25%;
      border: 20px solid orange;
      margin-left: -20px;
   }
```

Make sure to keep this quirk in mind when choosing to set width.

## Example 2 - box-model

Understanding the box-model and how it's part sit together is extremely important.

To see a visual representation of the css box model, load
<a href="./examples/ex02-box-model.html">this</a> file in a browser.
