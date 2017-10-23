# Chapter 1 - Some History

## The CSS Box Model

[From Jeff Kaufman](https://raw.githubusercontent.com/ALMaclaine/box-model-book/master/assets/img/ascii-box.png)

%Quote
In December 1996 the W3C published CSS1, the first version of the CSS spec. It used this
diagram to define a 'box model' of progressively larger boxes surrounding the content.
%

%Insert
Box model ascii image
%

However, the box model was not implemented according to the standard in every browser.
Internet explorer, like usual for it's day, had a "bug" that made the box model render
with it's border and padding inside the total width of the container.  This caused many
headaches for newbie and seasoned designers alike.  Attempting to maintain cross browser
compatability was an exercise in torture.

Internet Explorer Implemented it's box model like this

%Insert
Box model ascii image
%

From Jeff Kaufman

%Quote
When Microsoft released CSS1 support with their new Trident layout engine, it acted as
if the spec had instead had (refers to image).

Specifically, IE was treating width to include the border and the padding while
CCS1 treated width as including only the content. This became known as the IE box model.
%

This internet explorer "bug" is famous enough that it has its own wikipedia entry.

%Quote wiki
According to the CSS1 specification, released by the World Wide Web Consortium (W3C) in 1996 and revised in 1999, when a width or height is explicitly specified for any block-level element, it should determine only the width or height of the visible element, with the padding, borders, and margins applied afterward.[3][12] Internet Explorer in "quirks mode" includes the content, padding and borders within a specified width or height; this results in a narrower or shorter rendering of a box than would result following the standard behavior
%

While fundamentally a flaw, and an aberation against the standard, the IE box model started to
gain a following, and for a good reason. It makes sense.

Let's start with an example adapted from Fred Meyers parable.

Lets say you are a photographer and you have the opportunity to show one of your images
at an art gallery.  The gallery manager tells you that you have a 36 x 24 in spot and anything bigger
will be rejected. You call your printer and ask them to print and frame your best work.  You tell the
manager you want your picture to be as big as possible, but it needs some padding, about 2 inches on each side,
and the frame should be 3 inches. You tell the printer your spot is 36 x 24 inches and ask him to ship your picture to the gallery. Soon later you get a call from the manager, he asks you why you can't follow instructions and hangs up. Confused you call the printer, after considerable back and forth you discover he took you a little too literally.
You said you wanted your photo as big as possible, and you got it, 36 x 24 inches.  Then the padding and framing added
on top of photo, leaving it well outside your alotment.

While clarity and specifity is always important, sometimes it's nice to simply be understood.  Most people would
agree that the printer didn't follow the intent of the photographers instructions.  It's well accepted that maximum
dimensions should by respected, and lacking specificity, slack should come from the least qualified parameter, in this case, the size of the photo.

The w3x box model is a little like this very literal printer.  It takes you exactly at your direction, but
this isn't as intuitive as it could be.

From Peter Paul Koch

%Quote
In my opinion this model is completely illogical.

Logically, a box is measured from border to border. Take a physical box, any box. Put something in it that is distinctly smaller than the box. Ask anyone to measure the width of the box. He'll measure the distance between the sides of the box (the 'borders'). No one will think of measuring the content of the box.

Web designers who create boxes for holding content care about the *visible* width of the box, about the distance from border to border. The borders, and not the content, are the visual cues for the user of the site. Nobody is interested in the width of the content.
I wonder why W3C made its box model so needlessly complicated?
%

Another problem, is that it's usually at odds with a designer's intention.

From Fred Meyer
pressupine.com

%Quote
An obvious question is, “Isn’t working with the default model just a matter of learning a different way of saying the same thing?” If you’ve really got your heart set on a 100-pixel box, can’t you just do a bit of math and call it 50 pixels with 20px padding and 5px borders?

That we’d have to do this in the first place points to probably the simplest argument against the default box model: it approaches layout differently than actual designers do. When I try to lay out a page, I never think, “No matter what happens to the rest of the layout, I need this paragraph of text to take up exactly half of the page width.” I always think: “This column that contains text—and which has padding and borders and whatnot—should fill half the page.”

So the default model puts us through a lot of unnecessary translation work. Do we really want to manually be doing a bunch of math—”element width = declared width – (left padding + right padding) – (left border + right border)”—just to make CSS understand what we should have been able to declare with a simple, emphatic “width”?
%

The traditional box model also really hampers responsive design

From Fred Meyer

%Quote
The default box model also doesn’t work well for responsive design. Consider the following very intuitive, should-be-very-easy style declaration, attempting to divide a responsive-width container into two equal-width columns, each with 15px of padding:

.responsive-container .half-width-column {
   width: 50%;
   padding: 15px;
}
With the default box model, there’s no way to make this work. To get a 50% total width, you’d have to subtract 15px from 50% of the container width; but you don’t know the container width to be able to convert 15px into a percentage. As a result, whatever width value you attempt will always be broken: the columns will break and stack vertically at some widths, and they won’t fill the container at others.
%

And perhaps worst of all, it creates fragile layouts

From Fred Meyer

%Quote
Because the default model allows numerous kinds of style declarations to change an element’s dimensions, element styles are built like a house of cards. This makes the default model a great source of styling “gotchas,” which can break an element’s styling at any time. Here’s an example:

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
The sensible CSS above will break, since what needed to be a 250px-wide image is now 252px.
%