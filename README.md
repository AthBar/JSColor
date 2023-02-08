Have you ever wanted to change a color in a canvas in a specific way and couldn't get it done without weird regular expressions? Try this project! JSColor can parse any CSS color format string into a JavaScript object and edit it however you want.

# Documentation
The documentation for this specific project is very simple. It is all in one object:

## Color
This is where the color data is stored and processed. It can be constructed using the standard `new` operator, or by calling `Color` directly.
### constructor(String color):
Decodes the color into separate `r`, `g`, `b` and `a` values that can be accessed using prototype functions or reading the properties.


# Regular Expressions
This project was obviously made possible using regular expressions. From checking color validity to decoding color data, regex was used. Having said that, I decided to share every regular expression used in the project with the world.

## Checking color validity
Here are the regular expressions that tell whether the string provided is CSS-valid, i.e. would be acceptable as a color value in a `CSSStyleDeclaration` or it would change the color of a `CanvasRenderingContext2D` if used as `fillStyle`, `strokeStyle` and any color value of the context.

### RGB / RGBA
- With capturing groups:
  - Supporting both numbers and percentages (groups will be 1, 2, 3 and 4 for percentages and 5, 6, 7 and 8 for numbers if this method is used): `^\s*rgba?\(\s*(?:(?:(-?\d*(?:\.\d*)?%),?\s*(-?\d*(?:\.\d*)?%),?\s*(-?\d*(?:\.\d*)?%)(?:,?\s*(-?\d*(?:\.\d*)?%?)) *\)?\s*)|(?:(-?\d*(?:\.\d*)?),?\s*(-?\d*(?:\.\d*)?),?\s*(-?\d*(?:\.\d*)?)(?:,?\s*(-?\d*(?:\.\d*)?%?))))\s*\)?\s*$`
  
  - Supporting only numbers: `^\s*rgba?\(\s*(-?\d*(?:\.\d*)?),?\s*(-?\d*(?:\.\d*)?),?\s*(-?\d*(?:\.\d*)?)(?:,?\s*(-?\d*(?:\.\d*)?%?))\s*\)?\s*$`
  
  - Supporting only percentages: `^\s*rgba?\(\s*(-?\d*(?:\.\d*)?%),?\s*(-?\d*(?:\.\d*)?%),?\s*(-?\d*(?:\.\d*)?%)(?:,?\s*(-?\d*(?:\.\d*)?%?))\s*\)?\s*$`
  
- Without capturing groups:
  - Supporting both numbers and percentages: ``
