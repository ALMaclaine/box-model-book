# Chapter 4 - Examples

## Example 1 - Default Width Behavior

The w3c box model behaves differently depending on whether width is explicitly set.
If width is explicitly set, say at 100%, then the padding and border are added outside
the element. If however, no width is set, then the border and padding are inset.

Load this <a href="../examples/ex01-default-behavior.html">example</a> file.

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
<a href="../examples/ex02-box-model.html">this</a> file in a browser.

## Example 3 - w3c box-model

As a beginniner is can difficult to visualize the different gutter when actually looking
at a website.

In this example we have a demo box set up with all it's parts clearly visible.  Additionally
a ruler has been set against the box model so you can really understand the big picture.

Click <a href="../examples/ex03-w3c-model.html">here</a> for the file.

## Example 4 - ie box-model

Just like example 3, except using the ie box-model instead.

Click <a href="../examples/ex04-ie-model.html">here</a> for the file..

## Example 5 - dimensions

In this example we use the javascript functions client/offset dimensions to see
how box-sizing impacts the dom.

Click <a href="../examples/ex05-js-dimensions.html">here</a> for the file.

You can see that box-sizing is reflected in the dom and thus the javascript calls
return the numbers you'd expect.

## Exampele 6 - columns

This example builds a three column layout using flex-box and box-sizing.

Click  <a href="../examples/ex06-columns.html">here</a> for the file..

Using border box makes it easy to make columns of text and then add padding
because the content automatically adjust to fit and we keep our layout.

## Example 7 - fragile layouts

In this example we're building rows of yellow boxes for some reason.  The three
columns represent three attempts.

Click  <a href="../examples/ex07-broken-layouts.html">here</a> for the file..

You can see in the first column all of our yellow boxes.  Why they are useful is a
mystery, but they exist.  Suddenly we realize we need borders, so we add a thin
border around our boxes.

Woops! In column two we can see changing our border destroyed our layout.  We
really wanted the boxes to organize themselves like in column one.  In years
past we'd have to hand calculate how much to subtract to meet the correct dimensions.
But thanks to box-sizing, we just add the border-box property and suddenly our layout
is fixed, as shown in column 3.

