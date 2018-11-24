# Resources

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
