# Chapter 4 - The Talk Around Town

During my research I found lots of people sharing interesting thoughts about their
use of the box-sizing property and the css box-model.

Here are some of the top quotes, note some of the names and companies.

## Quotes

### [Douglas Bowman, Famous Designer](http://www.vorsprungdurchwebstandards.de/interviews/fallinginlovewithcss/douglas-bowman/)
>What drives you crazy when using CSS?
>>The Box Model, with regards to width and height. If I want a box to be x-wide by y-high, that’s what I want the final box to be. None of this subtractive nonsense needed to calculate something called “content width/height”. It’s dumbfounding that padding and border aren’t included in width and height measurements, or that I’m at least not given the option to force them to be included. An obvious sign that the CSS specification was written by technical people who understood modular construction differently than any designer ever would.
>><br><br>It’s like a furniture salesman providing you the length and height of a couch you like; you confirm the couch will fit perfectly along one wall in your home. Then when you get the couch home, it’s more than a foot too long and about six inches too tall. When you phone back to the furniture salesman to complain about the incorrect length he provided, he responds by stating that the length didn’t include the armrests and the height didn’t include the metal legs, and aren’t you stupid for not taking those into account in your measurements! What!?
In that regard, and in my opinion, Microsoft’s IE5/Windows team actually did something right when they originally implemented the box model against specification. They implemented it the way they thought the masses would expect the box model to work. Even though I’d like all browsers to build to specification so we all gain consistency and predictability, it’s a shame – in this instance – that Microsoft ended up bending to the specification, instead of rallying other browser makers and pressuring the W3C to change the specification to match logical behavior, and by extension, IE5/Win’s existing implementation.
>><br><br>CSS2.1 bended and evolved to meet and compromise with popular rendering implementations that have become de facto standards. It’s too bad that didn’t include correcting the backwards box model.

### [Paul Irish, Google Chrome Team](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>One of my least favorite parts about layout with CSS is the relationship of width and padding. You’re busy defining widths to match your grid or general column proportions, then down the line you start to add in text, which necessitates defining padding for those boxes. And ‘lo and behold, you now are subtracting pixels from your original width so the box doesn’t expand.

### [Mike Sherov, Adobe & jQuery](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>Im looking to fix all known bugs with border-box in jquery in version 1.8. I've been saying for a while that all signs point to wide adoption of border-box, especially on mobile. If anyone here is using border-box and jquery and finds a bug please file it at: http://bugs.jquery.com Thanks!

### [Mark Otto, Github & bootstrap](https://github.com/twbs/bootstrap/issues/12351)
>`border-box` is better for sizing components and folks all over are switching to it. Perhaps these other libraries should upgrade to support it. It's as easy/difficult for us to do it as it is for others. It's intrusive, but it's smarter and more durable development

### [Jon Hicks, famous designer](https://css-tricks.com/css-wishlist/)
>I would love a different box model! I find it bizarre that padding and border add the width of an object, and would love to be able to give something like a textarea 100% width and 3px padding without worrying what it's going to do the layout. Perhaps something like padding-inside as a new selector?
><br><br>In that vain I also wish I could specify a 100% width for an element, minus a set fixed width. Again, very useful when creating fluid designs with form elements!

### [Peter Paul Koch, famouse designer](https://netdiver.net/interviews/peterpaulkoch.php)
>My favorite example is W3C's box model. In this model, the width property defines the width of the content of the box, excluding paddings and borders. In my opinion this model is completely illogical.
><br><br>Logically, a box is measured from border to border. Take a physical box, any box. Put something in it that is distinctly smaller than the box. Ask anyone to measure the width of the box. He'll measure the distance between the sides of the box (the 'borders'). No one will think of measuring the content of the box.
><br><br>Web designers who create boxes for holding content care about the *visible* width of the box, about the distance from border to border. The borders, and not the content, are the visual cues for the user of the site. Nobody is interested in the width of the content.
><br><br>I wonder why W3C made its box model so needlessly complicated?

### [Elliot Sprehn, Adobe & Chromium](https://www.paulirish.com/wp-content/uploads/2011/gplus-boxsizing.html)
>Yeah, I definitely think IE's model is superior.

### [Nicolas Gallagher, normalize.css]
>Yeah, ever since IE8 came out with support for `box-sizing` we've been waiting until IE6/7 have negligible market share. I'm not sure how useful a global reset of the box model is going to be, but it's definitely useful for fluid components at the moment.

### [Tommy Maintz, Sencha](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>In both ExtJS 4+ and Sencha Touch 2+ we have been using box-sizing: border-box. It greatly simplifies your CSS, layouts and many of the calculations we had to do in JavaScript before. Glad to see others are starting to see the benefits of this.

### [Yathura Thorn](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>We’ve been using `* {box-sizing: border-box;}` in one of my projects (deployed in production, averaging over 1mln visits a month) at work for about a year now, and it seems to be holding up just fine. The project has been tested in IE8 & 9 and the latests Firefox and Chrome versions and we’ve had no problems. All jQuery (+UI) offset calculations and animations run fine, even in any element we’ve displayed as inline-block. As of late we’ve started testing the project on mobile devices (iPhone, iPad and Android) and we’ve had no issues regarding box-sizing with any of them yet, so it seems to work just fine.

### [nirmal](https://stackoverflow.com/questions/2429819/why-is-the-w3c-box-model-considered-better)
>Once I got into accidentally coding for IE's box model and became a fan of it. That's the perfect logic for a box. Ask W3C to run a container shipping firm, and it's dead in a week.

### [Joe Lambert](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>I'm a big fan of this technique and have been using it in a number of mobile web apps (and increasingly) website projects. Its a really welcome way to create a sensible baseline to work from for cross platform development.

### [Christopher Buecheler](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>So happy to hear this being advocated by a premiere developer. I've been complaining about CSS's box model since making the switch from table-based design back in the late 90s. Ending up having to set your 600px-wide column to 587px or whatnot to account for borders and padding is highly annoying and can make going back through the CSS time-consuming. I'm definitely looking forward to using the new box-sizing options on my future projects that don't need to be backward compatible with legacy browsers.

### [fredsbend](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>I don't think I've ever coded a box without knowing I was going to put text in it later. I don't see the problem. I'm pretty obsessive about planning the page first, though, sometimes even sketching it on paper first. If my plan is good, there is very little to tweak.

### [Matt Kruse](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>Also useful:
>
```css
img, .content-box {
   box-sizing: content-box !important;
}
```
>

### [digitalseraph](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>I constantly come back to this page. This has saved me frustration, headaches, and untold hours wasted from screwing with margins and padding and trying to calculate widths and heights unnecessarily for the past 2+ years. I apply this fix to almost every web application and website that I build. Are you aware of any solutions for this in HTML5 (or future CSS4 standards)? Thank you Paul!

### [Anon](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>...or you could do what I always do: use two boxes, one to define the column, one to define the look.
><br><br>Wireframe the page with boxes (no padding, no border, desired width). Nice and semantic, those 'these are my column boxes'-boxes (position: relative; of course).
><br><br>Then, put another box in each of these boxes, with the desired padding and border (a.k.a. non-semantic stuff); width and height 100%.
><br><br>Problem solved! (Oh, rubbish: of course the content-box is all wrong!)

## Not Everyones Ecstastic

### [Dan Eden, Facebook & Dropbox](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>Having used this on a project recently, I'm not 100% sold on the idea. It makes perfect sense for things like grid systems, and kills a lot of the usual layout headaches - particularly when it comes to mixing percentage and fixed unit width/height values, but it can become annoying to have to declare box-sizing: content-box; every time you want to override the universal selector.
><br><br>For me, it's best left on a per-use basis. But I can see it's use. Chris Coyier has some other great universal selector suggestions.

### [Justin](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>We had to remove this from `*` in our CSS framework. In Webkit browsers, this can create a bug with columns, where a column can float to the next row, to never float back up to its original position. We've seen this in several different instances. We're now targeting specific elements that actually need the border-box. It is a little scary using the * selector anyway. It's a great property, but I'm not sure `*` is a good idea.

### [Derek Watson](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>This seems like a buggy and highly unconventional solution to a simple problem. Instead, put your width on a container elements and padding on child elements. You'll find it works perfectly in all cases and you won't have to explain yourself at length to other developers on the project.
>> [Kevin Nelson](https://www.paulirish.com/2012/box-sizing-border-box-ftw/) Reply
>> <br> I would say to have to have two tags for every container is the unconventional solution that developers were forced to get used to because of the stupid box-model. To get a grid system to work this way you would need a container for the row, then a container for the column, and then a third tag inside each single column that does the padding...24 tags for 12 columns...or do it this way and have 12 tags one for each column...I don't see how in the world using the border-box CSS could possibly be more confusing than padding extending the width of a tag.
>><br><br>As far as developers needing an explanation...Bootstrap 3 converts all tags to border-box, but I didn't have to have bootstrap 3 explained to me...I right-clicked on a span in firebug, saw that they were using pixel-padding for their columns but percentage widths and said, "WTF, how did they do that?" Then, I saw the box-sizing on the tag and looked it up with a quick google search. When I saw the definition for box-sizing, what it does, and what browsers support it, I could have thrown a party. It took all of 2 minutes to figure out what Bootstrap3 had done, and now that I know about it, I'll never go back...it is ridiculous to have 24 tags for 12 columns.
>><br><br>Sorry for the long rant...I just don't see how anyone can not LOVE to type less tags (AND less CSS required for the grid system itself) so that their HTML is clearer and more concise and doesn't have extra tags thrown in as work-arounds for a box-model that never should have existed, IMHO.
>
>>[Gavin Smith](https://www.paulirish.com/2012/box-sizing-border-box-ftw/) Reply
>><br>Sometimes there's no way to add a child element to apply padding to that isn't otherwise completely unnecessary. What's the bigger evil, playing the CSS gods with new but fairly well supported box model adjustments or unnecessary markup?
>><br><br>I say the latter. By a long shot.
>
>>[Matthew](https://www.paulirish.com/2012/box-sizing-border-box-ftw/) Reply
>><br>I disagree that it's buggy or highly unconventional. Box-sizing as a property has been around for a long time, and is stable enough that it's now (mostly) non-prefixed. And look, a LOT of us have hated the W3C box model from day 1 and found it completely unintuitive. I've been waiting for IE7 numbers to drop enough to start using it. So it's a completely conventional and legit solution. It makes CSS easier to work with. And with the behavior polyfill, maybe now's the time.

### [Mr C](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>great tip, but non-square images with border / padding / margin appear to lose aspect ratio. presumably the same will happen to video too.
><br><br>would this be a sensible tweak?
><br><br> `*:not(img,video) { }`

### [Adam Schnaare](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>What about adding a container element? Set the 'width' there, and then add padding and border?

### [Thierry Koblentz](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>I ran into an issue yesterday on iPad1 related to box-sizing, hence why I knew about the prefix issue. I learned the hard way... as usual ;)
><br><br>Regarding what we used to call the "broken box model", I think the issue is that you do not own the content box and any change in border or padding impacts that content area. I understand that it can be easier for people to style boxes that way, but it's not a magic wand, you end up dealing with different issues.
><br><br>For example, if you style a nested container using something like "width:50%" does it makes sense to you that what you get is *not* 50% of the width of the parent box?

### [Niels Matthijs](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>Or just use margins on the inner elements instead of using padding on the container. Allows for more flexibility too. I rarely use padding, only if I need to reserve space for icons and such.

### [Justin](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>I'm also a fan of changing box-sizing—to an extent. I think it's only appropriate with fluid applications since percentage widths generate unpredictable sizes.
><br><br>Changing all elements would only be repeating your objection to the box model in reverse. Now you have to account for the math on the _inside_ of the element. This is in many ways harder to keep track of because there's no longer a value in your stylesheet that displays the width. Want an image that's the same size as the content width of the wrapper? Now you have to subtract the padding/margins/borders from the width—instead of just using the width.