## Linking Stylesheets

To separate your HTML and CSS code, you can create a new file, like `css/styles.css` and link it to
your HTML file by placing a `<link>` tag in the `<head>` of your HTML document.

```html
<head>
  …
  <link rel="stylesheet" href="css/styles.css" />
</head>
```

## CSS syntax

Any stylesheet consists of a collection of **ruleset**s. A ruleset consists of four parts:

![CSS syntax](assets/css-syntax.png)

|                | Description                                                                                                              |
| -------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Selector       | Selects to which elements the style declarations are applied, followed by curly braces (`{}`) enclosing the declarations |
| Declaration    | A combination of a property and a property value, separated by a colon (`:`) and ending with a semicolon (`;`)           |
| Property       | The property you want to style, e.g. `color`, `font-size`, `text-align`                                                  |
| Property Value | The value assigned to the property, e.g `blue` for the `color` property, `3rem` for the `font-size` property             |

A ruleset can have multiple declarations:

```css
h1 {
  color: blue;
  font-size: 3rem;
  text-align: center;
}
```

## Selectors

There are different CSS selectors you can use to select elements to which you want to apply styles.

### Type selector

The type selector selects all elements of a specific element type.

**Syntax**: `article`, `h1`, `p`, `div`, `a`, `input`, `button`, …

**Example**:

Select all `article` elements.

```css
article {
  color: red;
}
```

```html
<article>…</article>
```

### Class selector

The class selector selects all elements that have the specified class.

**Syntax**: `.superpink` (the user defined class name from the HTML but starting with a dot `.`)

**Example**:

Select all elements with the class `superpink`.

```css
.superpink {
  color: hotpink;
}
```

```html
<aside class="superpink">…</aside>
```

HTML elements can have multiple classes separated by a space. The selector `.superpink` would
also select the following element:

```html
<aside class="broccoli superpink some-other-class">…</aside>
```

The order of the classes in the HTML attribute doesn't matter.

### Pseudo-classes

The pseudo-class selector selects all elements that are in a specific state. It is used in combination with other selectors.

**Syntax**: `:hover`, `:focus`, … (the pseudo-class name starting with a colon `:`)

#### `:hover`

Selects an element when you hover over it with the mouse.

**Example**:

Select all hovered links.

```css
a:hover {
  color: hotpink;
}
```

```html
<a href="https://www.neuefische.de">neuefische</a>
