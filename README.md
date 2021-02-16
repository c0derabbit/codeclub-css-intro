# Code Club – Intro to CSS (or, how to style web apps)

CSS (cascading style sheets) are used to style websites: change the font, colour, spacing, sizes of things, add animations etc.

## In context

Use:
- HTML for structure
- **CSS for style and animations**
- JavaScript for interactivity.

Most of the time, you don’t need JS for a website to look dynamic.

## Ways to style HTML

- style attribute:
  ```html
  <h1 style="color: red;">
  ```
- inline stylesheet:
  ```html
  <style type="text/css">
    h1 {
      color: blue;
    }
  </style>
  ```
- external stylesheet:
  ```html
  <link rel="stylesheet" href="style.css" />
  ```

## CSS syntax

```css
p {
  color: darkblue;
  font-weight: bold;
}
```

## Selectors

### Element

Applies style to the HTML elements that have the same tag name — p, button, input etc.

```css
button {
  height: 40px;
  font-size: 20px;
}
```

### Class

Applies style to all elements that have the class.

```css
.large {
  width: 200px;
  height: 40px;
  font-size: 20px;
}
```
```html
<button class="large">Click me</button>

<input class="large" />
```

- element: `p, h2, div, input…`
- class: `.box, .big-button`
- elements with pseudo-classes: `a:active, .card:hover` etc. (`:hover` is the most used)

[Further reading here.](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors)

## Styling

Just a few examples to get started.

### Colors

```css
.something {
  background: blue;
  color: #fff0f0;
}
```
[This](https://www.colorschemer.com/css-color-codes/) is a good reference for colors.

### Text

Text alignment: `text-align: center;` (or `left`, `right`, `justify`)
Font size: `font-size: 2em` (`em`: relative size to document font size. `px`: pixels.)

#### To add custom web fonts:
1. Go to [fonts.google.com](https://fonts.google.com)
2. Find the font you want and click 'Select this style'
3. If the sidebar doesn't open, click the top right icon with squares.
4. Between `<link>` and `@import`, choose `@import`, and copy the code between the `<style>` tags. You don't need to copy the `<style>` tag.
5. Paste the copied line to the top of your CSS file.

Use it as `font-family: 'The Font Name';`

### Layouts
```css
.one {
  width: 600px; /* in pixels */
  height: 300px;
  max-width: 100%; /* of parent (or screen) */
  margin: 20px; /* all sides */
}

.two {
  margin: 0 40px; /* 0 on top and bottom, 40px on the sides */
}

.centered {
  margin: 0 auto; /* "automatically" as big as possible on the sides */
}

.grid {
  /* A simple grid with content arranged in 3 columns. */
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 40px;
}

.card {
  border: 4px solid #404040;
  border-radius: 3px;
  box-shadow: 0 0 8px 0 lightgrey;
}
```

### Transformations
```css
transform: rotate(5deg); /* rotate by 5 degrees */
transform: scale(1.2); /* make 1.2x bigger */
```
There are many more.

### Transitions
Smooth "animations" that change from one style to the other when their properties change. We'll use this with `:hover`.

**Transition should be applied to the original selector (or both if different), not only the :hover state.**

```css
.thing {
  background: white;
  color: blue;
  transition: background .5s ease; /* single-property transition only */
  transition: all .3s ease; /* all properties */
  transition: background .3s ease, color .3s ease; /* only needed properties. 
  If you transition more than one property, this is a better way than "all". */
}

.thing:hover {
  background: blue;
  color: white;
}
```

## Let’s style the Superhero Game!

Note: you'll need to restart the server after changes.

### Task 1: Stylesheet, font, colors

1. Create and use an external stylesheet called `style.css`
2. Change the body background and the title color.
3. Center all the text.
4. Import the web font **Permanent Marker** (from [Google Fonts](https://fonts.google.com)), and apply it to all the text.
5. Using the [MDN text-shadow docs](https://developer.mozilla.org/en-US/docs/Web/CSS/text-shadow), apply some text shadow to the title.
6. Remove the inline style from the hero image, and use CSS to set max width to 100%. (We'll need this later)

### Task 2: Layout
1. Wrap all the content inside `body` in a `<main>` element. Add a maximum width (something between 600 and 1200px) and center it with `margin`.
2. Wrap the heroes in a `<div>`, and add a class to it (e.g. `hero-list`).
3. Display the heroes in a 4-column grid.

### Task 3: Heroes
1. Add a class to the hero links (`card` or `hero` for example)
2. Add a white background.
3. Add a border, border-radius and some box-shadow.
4. With the pseudo-class `:hover`, apply a transformation to the hero when the mouse is over it. (Hint: use `transform: ...`)
5. Apply a transition between the normal and hover state. Hint: use the changed property name for the transition.

## Further reading
- [Learn CSS on MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS)
- Why is it called [cascading?](https://stackoverflow.com/questions/1043001/what-is-the-meaning-of-cascading-in-css)

### Shortcut to success ✨

There are many pre-coded solutions (think of them as dependencies or external stylesheets) that make styling web apps easier. One of the best and easiest to use is [TailwindCSS](https://tailwindcss.com/) – at its core, it's a collection of classes that you can use in HTML pages (including Flask templates).
