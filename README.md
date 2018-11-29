# My list of useful front end resources and 'ooh I didn't know that' facts to do with the front end.

## Hi! My name is Nikhil and I really like UI and interaction design stuff. This is my public repository of useful front-end related things I've comes across on the internet. I hope some of it is useful for you too.

# <<== LINKS START HERE ==>>

## Useful one-pager on Animations & performance

link: https://developers.google.com/web/fundamentals/design-and-ux/animations/animations-and-performance

>Animating properties is not free, and some properties are cheaper to animate than others. For example, animating the width and height of an element changes its geometry and may cause other elements on the page to move or change size. This process is called layout (or reflow in Gecko-based browsers like Firefox), and can be expensive if your page has a lot of elements. Whenever layout is triggered, the page or part of it will normally need to be painted, which is typically even more expensive than the layout operation itself.

>Where you can, you should avoid animating properties that trigger layout or paint. For most modern browsers, this means limiting animations to opacity or transform, both of which the browser can highly optimize; it doesn’t matter if the animation is handled by JavaScript or CSS.

## Consistently add a gradient to any container making it darker or lighter with a couple of lines of CSS. 

Add a gradient that starts 100% transparent, and ends slightly less transparent (eg: rgba(255,255,255,.25))  in order to give your container/item some more depth. 

Video: https://www.youtube.com/watch?v=5sHUHVU3I4g

CodePen: https://codepen.io/kevinpowell/pen/21f2833aa4a9c6929d5dc6404dcd1e75

**Variable:**
```
:root {
  --gradient-light: linear-gradient(145deg, rgba(255,255,255,0), rgba(255,255,255,.25));
  --gradient-dark: linear-gradient(145deg, rgba(0,0,0,0), rgba(0,0,0,.25));
}
```
**Usage:**
```
.content {
  background-color: #ee6352;
  background-image: var(--gradient-dark);
  width: 70vw;
  padding: 3em;
  box-shadow: 0 0 3em rgba(0,0,0,.15);
  color: white;
}
```
## Use SASS lighten(), darken() and more to programatically lighten or darken colours 

SASS comes with functions you can use without declaring. I'll add examples below. I use these mostly to add hover states on buttons, containers, links etc. 

**Examples**

```
darken( $base-color, 10% )
lighten( $base-color, 10% )
saturate( $base-color, 20% )
desaturate( $base-color, 20% )
adjust-hue( $base-color, 20% )
rgba( $base-color, .7 ) // alpha transparency
tint( $base-color, 10% )
shade( $base-color, 10% )
```

[Further reading →](https://robots.thoughtbot.com/controlling-color-with-sass-color-functions)

## Use system-ui fonts to improve performance

Article: https://css-tricks.com/snippets/css/system-font-stack/

**Usage**

```
/* System Fonts as used by GitHub */
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}

/* System Fonts as used by Medium and WordPress */
body {
  font-family: -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Oxygen-Sans,Ubuntu,Cantarell,"Helvetica Neue",sans-serif;
}
```
*It’s worth noting that system-ui works in place of BlinkMacSystemFont in newer versions of Chrome.*

Related article: https://booking.design/implementing-system-fonts-on-booking-com-a-lesson-learned-bdc984df627f

> don’t use -apple-system at the head of a shorthand font declaration, and test thoroughly, especially when playing around with proprietary stuff like system font declarations. If it looks like a vendor prefix and smells like a vendor prefix, chances are at least one browser is going to treat it like a vendor prefix.

## Doing CSS Breakpoints right

Link: https://medium.freecodecamp.org/the-100-correct-way-to-do-css-breakpoints-88d6a5ba1862

This is a really practical way to use mixins (in SASS) to define your breakpoints, and use it in a readable, declarative way. I haven't really found other ways that are better than this. 


**The Code:**
```

@mixin for-size($size) {
  @if $size == phone-only {
    @media (max-width: 599px) { @content; }
  } @else if $size == tablet-portrait-up {
    @media (min-width: 600px) { @content; }
  } @else if $size == tablet-landscape-up {
    @media (min-width: 900px) { @content; }
  } @else if $size == desktop-up {
    @media (min-width: 1200px) { @content; }
  } @else if $size == big-desktop-up {
    @media (min-width: 1800px) { @content; }
  }
}

// usage
.my-box {
  padding: 10px;
  
  @include for-size(desktop-up) {
    padding: 20px;
  }
}
```

## Using `calc()` for fluid typography

Link: https://css-tricks.com/snippets/css/fluid-typography/

**Code:**
```
body {
  font-size: calc([minimum size] + ([maximum size] - [minimum size]) * ((100vw - [minimum viewport width]) / ([maximum viewport width] - [minimum viewport width])));
}
```
