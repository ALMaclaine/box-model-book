# Chapter 4 - The Talk Around Town

During my research I found lots of people sharing interesting thoughts about their
use of the box-sizing property and the css box-model.

Here are some of the top quotes, note some of the names and companies.

## Quotes

### Douglas Bowman, Famous Designer
>What drives you crazy when using CSS?
>>The Box Model, with regards to width and height. If I want a box to be x-wide by y-high, that’s what I want the final box to be. None of this subtractive nonsense needed to calculate something called “content width/height”. It’s dumbfounding that padding and border aren’t included in width and height measurements, or that I’m at least not given the option to force them to be included. An obvious sign that the CSS specification was written by technical people who understood modular construction differently than any designer ever would.
>><br><br>It’s like a furniture salesman providing you the length and height of a couch you like; you confirm the couch will fit perfectly along one wall in your home. Then when you get the couch home, it’s more than a foot too long and about six inches too tall. When you phone back to the furniture salesman to complain about the incorrect length he provided, he responds by stating that the length didn’t include the armrests and the height didn’t include the metal legs, and aren’t you stupid for not taking those into account in your measurements! What!?
In that regard, and in my opinion, Microsoft’s IE5/Windows team actually did something right when they originally implemented the box model against specification. They implemented it the way they thought the masses would expect the box model to work. Even though I’d like all browsers to build to specification so we all gain consistency and predictability, it’s a shame – in this instance – that Microsoft ended up bending to the specification, instead of rallying other browser makers and pressuring the W3C to change the specification to match logical behavior, and by extension, IE5/Win’s existing implementation.
>><br><br>CSS2.1 bended and evolved to meet and compromise with popular rendering implementations that have become de facto standards. It’s too bad that didn’t include correcting the backwards box model.

### Original Reset