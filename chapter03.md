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

First is browser support, looking at [caniuse](http://caniuse.com/#feat=css3-boxsizing) will show you using box-sizing
is totally safe today.

[From Paul Irish](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>Due to browser support, this recommendation is only for projects that support IE8 and up. (Full browser compat at MDN) Firefox <= 28 still needs the -moz- prefix, and <= iOS4, Android <= 2.3 need the -webkit-, but everyone else uses the unprefixed. You can find more info about a box-sizing polyfill for IE6 & 7 at html5please.com/#box-sizing (which was developed with `* { box-sizing: border-box !important }`).

#### But is it safe?

[From Paul Irish](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>Totally. jQuery works pretty great with it. As mentioned, browser support is excellent. And a number of projects use this layout model by default, including the WebKit Web Inspector (aka Chrome DevTools). I heard from Dutch front-end developer Yathura Thorn on his experience:
>>We’ve been using `* { box-sizing: border-box; }` in one of my projects (deployed in production, averaging over 1mln visits a month) at work for about a year now, and it seems to be holding up just fine. The project has been tested in IE8 & 9 and the latests Firefox and Chrome versions and we’ve had no problems. All jQuery (+UI) offset calculations and animations run fine, even in any element we’ve displayed as inline-block. As of late we’ve started testing the project on mobile devices (iPhone, iPad and Android) and we’ve had no issues regarding box-sizing with any of them yet, so it seems to work just fine.

#### But it's slow right?

[From Paul Irish](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>You might get up in arms about the universal `*` selector.
><br><br>Apparently you’ve heard its slow. Firstly, it’s not. It is as fast as h1 as a selector. It can be slow when you specifically use it like `.foo > *`, so don’t do that. Aside from that, you are not allowed to care about the performance of `*` unless you concatenate all your javascript, have it at the bottom, minify your css and js, gzip all your assets, and losslessly compress all your images. If you aren’t getting 90+ Page Speed scores, it’s way too early to be thinking about selector optimization. See also: CSS Selector Performance has changed! (For the better) by Nicole Sullivan.
><br><br>So… enjoy and hope you’ll find this a far more natural layout model.

Here's an efficiency comparison via [Paul Irish](https://www.paulirish.com/2012/box-sizing-border-box-ftw/).

<div align="center">
  <a href="https://docs.google.com/spreadsheets/d/1jJUuSBQj6a3imkX_QYZDVW5eDyE5tXULTkqnI7rMLU8/edit#gid=0">
    <img src="https://raw.githubusercontent.com/ALMaclaine/box-model-book/master/assets/img/efficiency.png">
  </a>
</div>

#### Does it play well?

[From Paul Irish](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>Any third party widgets add content directly into the page may need extra attention. Any widgets inside an iframe (like Disqus’s new theme) are naturally insulated from the parent page’s layout styles. If you need to make adjustments to the third party content you can apply box-sizing: content-box; to the widget and its descendants. This may not be trivial as form controls in particular are border-box by default, so you’ll also have to account for that.

### What's it do for me?

So what are some of the benefits of using the border-box model?

[From Chris Coyier](https://css-tricks.com/international-box-sizing-awareness-day/#article-header-id-0)
>Why all the HOO-RAH?!
><br><br>It makes working with boxes so super duper much nicer.
><br><br>When you set the width of an element, that's the width that it is. If you set the width to 25%, it will take up 1/4 of the horizontal space available in its parent element. That's it.

#### But wait, there's more.

There are a number of other benefits as well. It allows the mixture of different units easily, something
rather difficult to manage before `calc()`, and even with `calc()`. It also allows for changes in element
padding/border down the line without recalculating overall widths/heights to preserve layout, and as we've
mentioned it matches our intuition.

#### When and where?

There are a number of use cases, one of [Paul Irish's](https://www.paulirish.com/2012/box-sizing-border-box-ftw/) top use cases is for columns.

[From Paul Irish](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>One of my favorite use-cases that border-box solves well is columns. I might want to divide up my grid with 50% or 20% columns, but want to add padding via px or em. Without CSS’s upcoming `calc()` this is impossible… unless you use border-box. So easy. :) Another good one is applying 100% width and then wanting to add a padding to that element.

### The ways of the master.

To many, the universal box-sizing reset seemed like a perfect solution to their web design woes. However, it's not without it's downfalls.  One such problem occurs when inserting
third party components into the page.

[From Paul Irish](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
>Any third party widgets add content directly into the page may need extra attention. Any widgets inside an iframe (like Disqus’s new theme) are naturally insulated from the parent page’s layout styles. If you need to make adjustments to the third party content you can apply box-sizing: content-box; to the widget and its descendants. This may not be trivial as form controls in particular are border-box by default, so you’ll also have to account for that.

This problem leads us to the last, and most recommended box-sizing reset.

```css
html {
  box-sizing: border-box;
}
*, *:before, *:after {
  box-sizing: inherit;
}
```

Credit goes to [Jon Neal](http://blog.teamtreehouse.com/box-sizing-secret-simple-css-layouts#comment-50223)
>This will give you the same result, and make it easier to change the box-sizing in plugins or other components that leverage other behavior.

By setting box-sizing to border-box on the html root, and setting all elements to inherit
their box-sizing, we are able to cancel out box-sizing on certain sub-components.  By setting box-sizing back to content-box on the sub-component containers, the inner elements of that component will inherit content-box and we've fixed the issue.

### Keep in mind

Some things to keep in mind for the border-box model. (pressupinc)

1. Margins are still outside the element.
2. Borders and padding now reduce content size
3. Be alert if you're transitioning an entire site to the new box model

### There's a price for everything.

A few issues with the border-box model that people list are.

#### Issue with em paddings

[From Roger Johansson](http://www.456bereastreet.com/archive/201104/controlling_width_with_css3_box-sizing/)
 >The box-sizing behavior is neat but has issues with the units you use, for padding, doesn't like ems."

#### Nested border-box

[From Roger Johansson](http://www.456bereastreet.com/archive/201104/controlling_width_with_css3_box-sizing/)
>It has problems when one element with box-sizing:border-box is nested inside another. So in example 3, the box-sizing behavior is only applied to the column elements, not the input fields. To avoid the input fields becoming wider than their parents, I’ve made them a bit narrower for IE 7. Example 4 shows a possible workaround without using box-sizing. I’ve just reduced the widths of the columns and input fields to where they don’t become too wide until the browser window is really narrow.

#### box-sizing table bug

[Chromium Bug](https://bugs.chromium.org/p/chromium/issues/detail?id=124816)
>box-sizing doesn't completly work for tables, can be read about in the [bug](https://bugs.chromium.org/p/chromium/issues/detail?id=124816) report.

#### Citations
1. [https://css-tricks.com/almanac/properties/b/box-sizing](https://css-tricks.com/almanac/properties/b/box-sizing/)
2. [http://caniuse.com/#feat=css3-boxsizing](http://caniuse.com/#feat=css3-boxsizing)
3. [https://www.paulirish.com/2012/box-sizing-border-box-ftw/](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
4. [https://css-tricks.com/international-box-sizing-awareness-day/#article-header-id-0](https://css-tricks.com/international-box-sizing-awareness-day/#article-header-id-0)
5. [http://blog.teamtreehouse.com/box-sizing-secret-simple-css-layouts#comment-50223](http://blog.teamtreehouse.com/box-sizing-secret-simple-css-layouts#comment-50223)
6. [https://bugs.chromium.org/p/chromium/issues/detail?id=124816](https://bugs.chromium.org/p/chromium/issues/detail?id=124816)