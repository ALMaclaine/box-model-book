# Chapter 4 - Examples

## Every Reset

### Original Reset

```css
   * {
      box-sizing: border-box;
   }
```

Every normal element has border-box applied to it.

### Full Reset

```css
   *, *:after, *:before {
      box-sizing: border-box;
   }
```

Resets all normal elements as well as pseudo-elements

### Inheriting Reset

```css
   html {
      box-sizing: border-box;
   }

   *, *:after, *:before {
      box-sizing: inherit;
   }
```

This reset applies box-sizing at the root element and the has all other elements inherit from it.
This allows you to reset box-sizing for components by changing the containing element to content-box.

### Root Reset

```css
   :root {
      box-sizing: border-box;
   }

   *, *:after, *:before {
      box-sizing: inherit;
   }
```

The root reset is the same as the inheriting reset, except we use the psuedo class
matching the root element of the tree, `:root`.

### Preserving Replaced Content

If you wish to maintain the original scaling or aspect ratio of replaced content
(img, video, svg) then you should avoid setting them to border-box with one of
the following methods.

```css
   :root {
      box-sizing: border-box;
   }

   *, *:after, *:before {
      box-sizing: inherit;
   }

   img, video, svg, .content-box {
      box-sizing: content-box;
   }
```

or

```css
   :root {
      box-sizing: border-box;
   }

   *:not(img):not(video):not(svg), *:after, *:before {
      box-sizing: inherit;
   }
```

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

## Example 4 - IE box-model

Just like example 3, except using the ie box-model instead.

Click <a href="../examples/ex04-ie-model.html">here</a> for the file.

## Example 5 - Dimensions

In this example we use the javascript functions client/offset dimensions to see
how box-sizing impacts the dom.

Click <a href="../examples/ex05-js-dimensions.html">here</a> for the file.

You can see that box-sizing is reflected in the dom and thus the javascript calls
return the numbers you'd expect.

## Exampele 6 - Columns

This example builds a three column layout using flex-box and box-sizing.

Click  <a href="../examples/ex06-columns.html">here</a> for the file.

Using border box makes it easy to make columns of text and then add padding
because the content automatically adjust to fit and we keep our layout.

## Example 7 - fragile layouts

In this example we're building rows of yellow boxes for some reason.  The three
columns represent three attempts.

Click  <a href="../examples/ex07-broken-layouts.html">here</a> for the file.

You can see in the first column all of our yellow boxes.  Why they are useful is a
mystery, but they exist.  Suddenly we realize we need borders, so we add a thin
border around our boxes.

Woops! In column two we can see changing our border destroyed our layout.  We
really wanted the boxes to organize themselves like in column one.  In years
past we'd have to hand calculate how much to subtract to meet the correct dimensions.
But thanks to box-sizing, we just add the border-box property and suddenly our layout
is fixed, as shown in column 3.

## Example 8 - Scaled Images

There's an argument to be made that replaced content such as img, video and svg,
should not have it's box-sizing changed as it can cause unwanted scaling.

Click  <a href="../examples/ex08-image-scaling.html">here</a> for the file.

You can see that our padding is causing the image to scale down uniformly.  To me
this is a minor issue, but some people have concerns about the image scaling capabilities
of browsers.

## Example 9 - Muh Aspect Ratio

Similar to above, except we force a break in our aspect ratio, an obvious issue.

Click  <a href="../examples/ex09-muh-aspect.html">here</a> for the file.

You can see that our padding is causing the image to scale inwards more than down.  This
issue is not a minor issue and serious consideration should be made on how these situations
will be handled.  It's for this reason some people avoid applying the box-sizing reset
to replaced content.
