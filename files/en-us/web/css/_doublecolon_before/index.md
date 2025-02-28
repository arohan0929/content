---
title: "::before (:before)"
slug: Web/CSS/::before
tags:
  - CSS
  - Layout
  - Pseudo-element
  - Reference
  - Selector
  - Web
browser-compat: css.selectors.before
---

{{CSSRef}}

In CSS, **`::before`** creates a [pseudo-element](/en-US/docs/Web/CSS/Pseudo-elements) that is the first child of the selected element. It is often used to add cosmetic content to an element with the {{cssxref("content")}} property. It is inline by default.

{{EmbedInteractiveExample("pages/tabbed/pseudo-element-before.html", "tabbed-standard")}}

> **Note:** The pseudo-elements generated by `::before` and `::after` are [contained by the element's formatting box](https://www.w3.org/TR/CSS2/generate.html#before-after-content), and thus don't apply to _[replaced elements](/en-US/docs/Web/CSS/Replaced_element)_ such as {{htmlelement("img")}}, or to {{htmlelement("br")}} elements.

## Syntax

```
::before
```

> **Note:** [Selectors Level 3](https://drafts.csswg.org/selectors-3/#gen-content) introduced the double-colon notation `::before` to distinguish [pseudo-classes](/en-US/docs/Web/CSS/Pseudo-classes) from [pseudo-elements](/en-US/docs/Web/CSS/Pseudo-elements). Browsers also accept single-colon notation`:before`, introduced in CSS2.

## Examples

### Adding quotation marks

One simple example of using `::before` pseudo-elements is to provide quotation marks. Here we use both `::before` and `{{Cssxref("::after")}}` to insert quotation characters.

#### HTML

```html
<q>Some quotes</q>, he said, <q>are better than none.</q>
```

#### CSS

```css
q::before {
  content: "«";
  color: blue;
}

q::after {
  content: "»";
  color: red;
}
```

#### Result

{{EmbedLiveSample('Adding_quotation_marks', '500', '50', '')}}

### Decorative example

We can style text or images in the {{cssxref("content")}} property almost any way we want.

#### HTML

```html
<span class="ribbon">Notice where the orange box is.</span>
```

#### CSS

```css
.ribbon {
  background-color: #5bc8f7;
}

.ribbon::before {
  content: "Look at this orange box.";
  background-color: #ffba10;
  border-color: black;
  border-style: dotted;
}
```

#### Result

{{EmbedLiveSample('Decorative_example', 450, 60)}}

### To-do list

In this example we will create a simple to-do list using pseudo-elements. This method can often be used to add small touches to the UI and improve user experience.

#### HTML

```html
<ul>
  <li>Buy milk</li>
  <li>Take the dog for a walk</li>
  <li>Exercise</li>
  <li>Write code</li>
  <li>Play music</li>
  <li>Relax</li>
</ul>
```

#### CSS

```css
li {
  list-style-type: none;
  position: relative;
  margin: 2px;
  padding: 0.5em 0.5em 0.5em 2em;
  background: lightgrey;
  font-family: sans-serif;
}

li.done {
  background: #ccff99;
}

li.done::before {
  content: "";
  position: absolute;
  border-color: #009933;
  border-style: solid;
  border-width: 0 0.3em 0.25em 0;
  height: 1em;
  top: 1.3em;
  left: 0.6em;
  margin-top: -1em;
  transform: rotate(45deg);
  width: 0.5em;
}
```

#### JavaScript

```js
const list = document.querySelector('ul');
list.addEventListener('click', (ev) => {
  if (ev.target.tagName === 'LI') {
     ev.target.classList.toggle('done');
  }
}, false);
```

Here is the above code example running live. Note that there are no icons used, and the check-mark is actually the `::before` that has been styled in CSS. Go ahead and get some stuff done.

#### Result

{{EmbedLiveSample('To-do_list', 400, 300)}}

### Special characters

As this is CSS; not HTML, you can **not** use markup entities in content values. If you need to use a special character, and can not enter it literally into your CSS content string, use a unicode escape sequence, consisting of a backslash followed by the hexadecimal unicode value.

#### HTML

```html
<ol>
  <li>Crack Eggs into bowl</li>
  <li>Add Milk</li>
  <li>Add Flour</li>
  <li aria-current='step'>Mix thoroughly into a smooth batter</li>
  <li>Pour a ladleful of batter onto a hot, greased, flat frying pan</li>
  <li>Fry until the top of the pancake loses its gloss</li>
  <li>Flip it over and fry for a couple more minutes</li>
  <li>serve with your favorite topping</li>
</ol>
```

#### CSS

```css
li {
  padding: 0.5em;
}

li[aria-current="step"] {
  font-weight: bold;
}

li[aria-current="step"]::after {
  content: " \21E6"; /* Hexadecimal for Unicode Leftwards white arrow*/
  display: inline;
}
```

#### Result

{{EmbedLiveSample('Special_characters', 400, 200)}}

## Accessibility concerns

Using a `::before` pseudo-element to add content is discouraged, as it is not reliably accessible to screen readers.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{Cssxref("::after")}}
- {{Cssxref("content")}}
