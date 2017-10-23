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

### [nirmal](https://stackoverflow.com/questions/2429819/why-is-the-w3c-box-model-considered-better)
>Once I got into accidentally coding for IE's box model and became a fan of it. That's the perfect logic for a box. Ask W3C to run a container shipping firm, and it's dead in a week.

### [Paul Irish, Google Chrome Team](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>One of my least favorite parts about layout with CSS is the relationship of width and padding. You’re busy defining widths to match your grid or general column proportions, then down the line you start to add in text, which necessitates defining padding for those boxes. And ‘lo and behold, you now are subtracting pixels from your original width so the box doesn’t expand.

### [Yathura Thorn](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>We’ve been using `\* {box-sizing: border-box;}` in one of my projects (deployed in production, averaging over 1mln visits a month) at work for about a year now, and it seems to be holding up just fine. The project has been tested in IE8 & 9 and the latests Firefox and Chrome versions and we’ve had no problems. All jQuery (+UI) offset calculations and animations run fine, even in any element we’ve displayed as inline-block. As of late we’ve started testing the project on mobile devices (iPhone, iPad and Android) and we’ve had no issues regarding box-sizing with any of them yet, so it seems to work just fine.