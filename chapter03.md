# Chapter 3 - Box-Sizing to the rescue

### New Property: box-sizing

In CSS3 the option to change the way the box model handles it's total width has been introduced
in the box-sizing property.  The box-sizing property allows either content-box or box-sizing to be
set as its value, content-box is the default w3c box model and box-sizing, the IE model.

[From Sara Cope](https://css-tricks.com/almanac/properties/b/box-sizing/)
> The box-sizing property in CSS controls how the box model is handled for the element it applies to.

Changing the box model is simple, for any selector, just use the box-sizing property.

```css
.module {
  box-sizing: border-box;
}
```

The most common way to apply border-box is to all elements and pseudo elements on the page using the universal
selector \*.

```css
*, *:after, *:before {
  box-sizing: border-box;
}
```

This is called universal box-sizing.

### What's the catch?

In the famous Paul Irish blog post that got this craze started, he addresed many of the points of
interest and concern related to using this reset.

First is browser support, looking at http://caniuse.com/#feat=css3-boxsizing will show you using box-sizing
is totally safe today.

[From Paul Irish](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>Due to browser support, this recommendation is only for projects that support IE8 and up. (Full browser compat at MDN) Firefox <= 28 still needs the -moz- prefix, and <= iOS4, Android <= 2.3 need the -webkit-, but everyone else uses the unprefixed. You can find more info about a box-sizing polyfill for IE6 & 7 at html5please.com/#box-sizing (which was developed with `* { box-sizing: border-box !important }`).

### But is it safe?

[From Paul Irish](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>Totally. jQuery works pretty great with it. As mentioned, browser support is excellent. And a number of projects use this layout model by default, including the WebKit Web Inspector (aka Chrome DevTools). I heard from Dutch front-end developer Yathura Thorn on his experience:
>>We’ve been using `* { box-sizing: border-box; }` in one of my projects (deployed in production, averaging over 1mln visits a month) at work for about a year now, and it seems to be holding up just fine. The project has been tested in IE8 & 9 and the latests Firefox and Chrome versions and we’ve had no problems. All jQuery (+UI) offset calculations and animations run fine, even in any element we’ve displayed as inline-block. As of late we’ve started testing the project on mobile devices (iPhone, iPad and Android) and we’ve had no issues regarding box-sizing with any of them yet, so it seems to work just fine.


<div align="center">
  <a href="https://www.jefftk.com/p/the-revenge-of-the-ie-box-model">
    <img src="https://raw.githubusercontent.com/ALMaclaine/box-model-book/master/assets/img/ascii-iebox.png">
  </a>
</div>

[From Jeff Kaufman](https://www.jefftk.com/p/the-revenge-of-the-ie-box-model)
>When Microsoft released CSS1 support with their new Trident layout engine, it acted as
if the spec had instead had (refers to image). Specifically, IE was treating width to include the border and the padding while
CCS1 treated width as including only the content. This became known as the IE box model.

## Internet Explorer Box Model Bug
This internet explorer "bug" is famous enough that it has its own wikipedia entry.

[Wiki](https://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug#Background)
>According to the CSS1 specification, released by the World Wide Web Consortium (W3C) in 1996 and revised in 1999, when a width or height is explicitly specified for any block-level element, it should determine only the width or height of the visible element, with the padding, borders, and margins applied afterward.[3][12] Internet Explorer in "quirks mode" includes the content, padding and borders within a specified width or height; this results in a narrower or shorter rendering of a box than would result following the standard behavior

While fundamentally a flaw, and an aberation against the standard, the IE box model started to
gain a following, and for a good reason. It makes sense.

## That's not a bug, that's a feature.

Let's start with an example adapted from Fred Meyers parable.

Lets say you are a photographer and you have the opportunity to show one of your images
at an art gallery.  The gallery manager tells you that you have a 36 x 24 inches spot and anything bigger
will be rejected. You call your printer and ask them to print and frame your best work.  You tell the
printer you want your picture to be as big as possible, but it needs some padding, about 2 inches on each side,
and the frame should be 3 inches. You tell the printer your spot is 36 x 24 inches and ask him to ship direct to the gallery.

Soon later you get a call from the gallery manager, he asks you why you can't follow simple instructions and hangs up. Confused you call the printer, after considerable back and forth you discover he took you a little too literally.
You said you wanted your photo as big as possible, and you got it, 36 x 24 inches.  Then the padding and framing was added on top of photo, leaving it well outside your allotment.

While clarity and specificity is always important, sometimes it's nice to simply be understood.  Most people would
agree that the printer didn't follow the intent of the photographers instructions.  It's well accepted that maximum
dimensions should by respected, and lacking specificity, slack should come from the least qualified parameter, in this case, the size of the photo.

The w3x box model is a little like this very literal printer.  It takes you exactly at your direction, but
this isn't always intuitive.

## Professional Complaints

### Illogical

[From Peter Paul Koch](https://netdiver.net/interviews/peterpaulkoch.php)
>In my opinion this model is completely illogical.
Logically, a box is measured from border to border. Take a physical box, any box. Put something in it that is distinctly smaller than the box. Ask anyone to measure the width of the box. He'll measure the distance between the sides of the box (the 'borders'). No one will think of measuring the content of the box.
><br><br>Web designers who create boxes for holding content care about the *visible* width of the box, about the distance from border to border. The borders, and not the content, are the visual cues for the user of the site. Nobody is interested in the width of the content.
I wonder why W3C made its box model so needlessly complicated?

### That's Not What I Said

Another problem, is that the standard box model is usually at odds with a designer's intention.

[From Fred Meyer](https://pressupinc.com/blog/2014/01/whats-wrong-css-box-model-fix/)
>An obvious question is, “Isn’t working with the default model just a matter of learning a different way of saying the same thing?” If you’ve really got your heart set on a 100-pixel box, can’t you just do a bit of math and call it 50 pixels with 20px padding and 5px borders?
><br><br> That we’d have to do this in the first place points to probably the simplest argument against the default box model: it approaches layout differently than actual designers do. When I try to lay out a page, I never think, “No matter what happens to the rest of the layout, I need this paragraph of text to take up exactly half of the page width.” I always think: “This column that contains text—and which has padding and borders and whatnot—should fill half the page.”
><br><br> So the default model puts us through a lot of unnecessary translation work. Do we really want to manually be doing a bunch of math—”element width = declared width – (left padding + right padding) – (left border + right border)”—just to make CSS understand what we should have been able to declare with a simple, emphatic “width”?


### Please Respond

The traditional box model also really hampers responsive design

[From Fred Meyer](https://pressupinc.com/blog/2014/01/whats-wrong-css-box-model-fix/)
>The default box model also doesn’t work well for responsive design. Consider the following very intuitive, should-be-very-easy style declaration, attempting to divide a responsive-width container into two equal-width columns, each with 15px of padding:

```css
.responsive-container .half-width-column {
   width: 50%;
   padding: 15px;
}
```
>With the default box model, there’s no way to make this work. To get a 50% total width, you’d have to subtract 15px from 50% of the container width; but you don’t know the container width to be able to convert 15px into a percentage. As a result, whatever width value you attempt will always be broken: the columns will break and stack vertically at some widths, and they won’t fill the container at others.

### Rooms Made of Glass

And perhaps worst of all, it creates fragile layouts

[From Fred Meyer](https://pressupinc.com/blog/2014/01/whats-wrong-css-box-model-fix/)
> Because the default model allows numerous kinds of style declarations to change an element’s dimensions, element styles are built like a house of cards. This makes the default model a great source of styling “gotchas,” which can break an element’s styling at any time. Here’s an example:

```css
/* Image must be exactly 250px wide to fit properly in layout */
.main-container img.fixed-width-img {
   width: 250px;
}

/* 300 lines later...
________________________________ */

/* Today feels like a good day to make some pretty image styles */
.main-container img {
   border: 1px black solid;
}
```

>The sensible CSS above will break, since what needed to be a 250px-wide image is now 252px.

#### Citations
1. [https://www.jefftk.com/p/the-revenge-of-the-ie-box-model](https://www.jefftk.com/p/the-revenge-of-the-ie-box-model)
2. [https://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug#Background](https://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug#Background)
3. [https://netdiver.net/interviews/peterpaulkoch.php](https://netdiver.net/interviews/peterpaulkoch.php)
4. [https://pressupinc.com/blog/2014/01/whats-wrong-css-box-model-fix/](https://pressupinc.com/blog/2014/01/whats-wrong-css-box-model-fix/)
5. [https://pressupinc.com/blog/2014/01/css-default-box-model-utter-madness-parable/](https://pressupinc.com/blog/2014/01/css-default-box-model-utter-madness-parable/)