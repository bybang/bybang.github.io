---
layout: single
title: "[Frontend] TIL Frontend project - Overview of CSS part 1"

categories: Frontend
tag: [Frontend, HTML, CSS, JavaScript, TIL]

permalink: /frontend/TIL-FASTCAMPUS-005

toc: true
published: true
---

![](https://velog.velcdn.com/images/devbang/post/af7f72ea-d3e6-4cb3-b98d-a9fb68176eea/image.png)

# FASTCAMPUS Frontend Project

## Overview of CSS - part 1

> 패스트캠퍼스 - [프론트엔드 웹 개발의 모든 것 초격차 패키지 Online](https://fastcampus.co.kr/dev_online_fesignature) 과정

# 🧩 What I Should Learn?

- Basic Syntax, comments
- Types of CSS
- Basic CSS selectors
- CSS combinators
- CSS Pseudo-class 1

# 🎯 What I learned today

## Basic Syntax, comments

### CSS

CSS stands for Cascading Style Sheets and is used to style and layout webpages. For instance, we can use CSS to alter the font, color, size, and spacing of our content.

![](https://velog.velcdn.com/images/devbang/post/318e3587-433b-4a73-8549-9f6d67ed420e/image.png)

As we did previously, the picture above shows that we added some `CSS` styles to the `div` tag, and it applied to the `div` tag on the screen.

The CSS styles won't be applied to the screen if we change the `div` element to a `span` element.

![](https://velog.velcdn.com/images/devbang/post/0c5200ee-1795-420d-82b5-bddb4d93828a/image.png)

Hence, we call the `div` part in the CSS file a `selector` because we are selecting elements to apply CSS styles from an HTML document.

In a nutshell, the CSS file code means we want to `select` the `div` element from an HTML document and apply the code inside the curly braces after the `div`.

More information on the CSS syntax can be found [here](https://developer.mozilla.org/en-US/docs/Web/CSS/Syntax).

![](https://velog.velcdn.com/images/devbang/post/85c4746b-2270-4e29-8d9e-64ea7048ed54/image.png)

### CSS Selector

A selector is the first part of a CSS rule. It is a pattern of elements, and other terms that tell the browser which HTML elements should be selected to have the CSS property values inside the rule applied to them. - [MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors#what_is_a_selector)

```css
h1 {
  color: blue;
}
```

### CSS Syntax

In the case above, the `h1` is the selector, the `color` is a property, and the `blue` is a value of the CSS property.

<!-- prettier-ignore -->
```css
h1 { color: blue; background-color: yellow; }
```

The curly braces indicate where the style starts and ends, and we distinguish each style by colon and semicolon at the end of it.

Reading the long line of code and identifying the specific property can be a tedious job, and this process might increase the chance of making mistakes.

To streamline the workflow and reduce errors, we use indentations.

```css
h1 {
  color: blue;
  background-color: yellow;
  margin: 20px;
}
```

CSS has its own comment style, and we can leave a memo or comment out the styles to check output without it like this:

```css
/* Sample comment */
h1 {
  color: blue;
  /* background-color: yellow; */
  margin: 20px;
}
```

## Types of CSS

### Internal CSS

Internal CSS has the `style` tag inside the `head` section of the HTML document.

![](https://velog.velcdn.com/images/devbang/post/8be39266-1604-4e32-b21b-b0ec85b6eaa6/image.png)

The `style` element contains style information for a document. It contains CSS, which is applied to the contents of the document containing the `style` element. In general, it is better to put the styles in external stylesheets and apply them using `link` elements. - [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/style)

### Inline CSS

Inline CSS is used to style a specific HTML element by adding a `style` attribute to each HTML tag without using selectors.

```html
<a href="https://www.google.com">Google</a>
<a href="/about">About</a>
<a href="/login/" style="color: red; margin: 20px;">Login</a>
```

It styles multiple elements at the same time, which can affect the page size and download time of the page. This attribute and `style` element have mainly the purpose of allowing for quick styling, like for testing purposes.

### External CSS

The use of inline CSS and internal CSS is not recommended due to the difficulty in maintenance. The recommended styling is using external stylesheets, which is the external CSS.

In external CSS, we link the webpages to the external `.css` file. By editing the `.css` file, we can change the whole site at once.

![](https://velog.velcdn.com/images/devbang/post/cf92cca4-e20d-4555-b5f4-e16946b6eecc/image.png)

As we learned before, the external CSS type requires the `link` element. The external resource link element has the `rel` attribute that specifies the relationship between the current document and an external resource, and the `href` attribute, which indicates the external resource's location.

```html
<link rel="stylesheet" href="./css/main.css" />
```

### Import CSS

The `@import` CSS at-rule is used to import rules from other valid stylesheets. An `@import` rule _must_ be defined at the top of the stylesheets before any other at-rule and style declarations, or it will be ignored.

![](https://velog.velcdn.com/images/devbang/post/1e8e0e58-e352-4a23-a78c-db16d385732a/image.png)

The `@import` rule has a serial processing structure, which means the `box.css` style will not applied before interpreting the `main.css`. We can use this delay on purpose, but it could also be a disadvantage.

Meanwhile, the `link` tag has a parallel processing structure, which means the external resources will be called simultaneously. Hence, using the `link` element will be much faster when interpreting and applying CSS styles to HTML documents.

## Basic CSS selectors

### Universal Selector

There are a few different selectors in CSS, and we are going to learn from the basic selectors that are commonly used.

The CSS universal selector `*` matches elements of any type. The universal selector is a special type selector and is useful when we want to select all of the elements.

![](https://velog.velcdn.com/images/devbang/post/bb9f0209-ce75-4a2a-b624-9f17bf21d1bc/image.png)

### Type Selector

The CSS type selector matches elements by node name, which means it selects all elements of the given type within a document.

![](https://velog.velcdn.com/images/devbang/post/32e78f71-0433-4f45-8baa-d94ba3125727/image.png)

### Class Selector

The CSS class selector matches elements based on the contents of their `class` attribute.

Notice the above type selector can't distinguish individual elements. Hence, we use the `class` attribute to select the specific element.

![](https://velog.velcdn.com/images/devbang/post/82aea7e3-6619-439b-9ea1-969ab788a84e/image.png)

The important syntax is `.`, which indicates that the following word is the class name.

### ID Selector

The CSS ID selector matches an element based on the value of the element's `id` attribute. In order for the element to be selected, its `id` attribute must match exactly the value given in the selector.

![](https://velog.velcdn.com/images/devbang/post/37f36205-9ec5-4b02-90e4-a8979e669c35/image.png)

The id uses `#` to select the element, and notice from the picture that the id selector and class selector can be used together.

## CSS Combinators

### Class Selector

The class selector can be used as a combinator like the following case:

![](https://velog.velcdn.com/images/devbang/post/3c57451c-99b1-4289-ab03-d4c411ecbd56/image.png)

Notice that the `span.orange` selector has to satisfy both the `span` tag and the `orange` class. Even though we have the elements with the same class name, only the style of the last element has changed.

![](https://velog.velcdn.com/images/devbang/post/242e5dd6-9ef1-416a-b41b-db061fa56ac2/image.png)

The order of the elements is important since the selector has no space between the elements.

### Child Combinator

The child combinator (`>`) is placed between two CSS selectors. It matches only those elements matched by the second selector that are the direct children of elements matched by the first.

![](https://velog.velcdn.com/images/devbang/post/ac093775-5c48-4ff0-bb4c-85c71ee982b4/image.png)

We can see that in `main.css`, the style applied to the last element, which is the `li` tag and the class name `.orange`. Also, the `ul` element is the parent element for both `li` and `.orange`.

The last content also has the same class name, `.orange`, but the parent element is `span`. Hence, the style only applied to the first content with the class name `.orange`.

### Descendant Combinator

The descendant combinator is typically represented by a single space (`" "`) character. It combines two selectors such that elements matched by the second selector are selected if they have an ancestor element matching the first selector.

![](https://velog.velcdn.com/images/devbang/post/e5f1c0bf-63bb-49ab-a452-d46d6977949f/image.png)

Notice that the outermost `div` element has many descendant elements, and the descendant combinator finds the class with the name `orange`. The `span` outside of the `div` element is not selected because it is not a descendant of the `div` element.

In most cases, we use a descendant combinator for detail styling. If we really want to style a specific element, we use the child combinator, but generally, the descendant combinator is more convenient.

Additionally, because whitespace is considered a special character, we have to be careful when using space in CSS.

### Next-sibling combinator

The next-sibling combinator (`+`) is placed between two CSS selectors. It matches only those elements matched by the second selector, which is the next sibling element of the first selector.

![](https://velog.velcdn.com/images/devbang/post/e0433485-1798-42b8-ae36-a3a59f7d5adb/image.png)

If we look at the `li` element with the class name `.orange`, it has two adjacent siblings: the mango and kiwi.

Only the mango has the color in the live server because the content mango or the `li` element is next to the `li` element that has the class name `.orange`.

### Subsequent-sibling combinator

If you want to select siblings of an element even if they are not adjacent, then you can use the subsequent-sibling combinator (`~`).

![](https://velog.velcdn.com/images/devbang/post/33f97502-4bb2-4ce8-8018-35a29fd16df0/image.png)

Normally, we often use a next-sibling combinator when selecting the next content, but we should know there is a selector for every element next to the current content.

More detailed information about the combinator is available on [MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Combinators).

## CSS Pseudo-class part 1

### Pseudo-class

A CSS pseudo-class is a keyword added to a selector that specifies a special state of the selected element. It consists of a colon followed by the pseudo-class name.

Pseudo-classes let you apply a style to an element not only in relation to the content of the document tree but also in relation to external factors like the position of the mouse, the status of its content or the history of the navigator - [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes).

### `:hover`

The `:hover` CSS pseudo-class matches when the user interacts with an element with a pointing device but does not necessarily activate it.

![](https://velog.velcdn.com/images/devbang/post/51b42dd0-3a94-45aa-ad62-fd89258cd2be/image.gif)

It is generally triggered when the user hovers over an element with the mouse pointer.

### `:active`

The `:active` CSS pseudo-class represents an element that is being activated by the user. When using a mouse, `activation` typically starts when the user presses the primary mouse button.

![](https://velog.velcdn.com/images/devbang/post/3ff12673-9ad3-455b-9b37-2c2f2193a72b/image.gif)

Note that the box only changes the style when the cursor clicks the content. The `:active` pseudo-class is commonly used on `a` and `button` elements.

### `:focus`

Tcus` CSS pseudo-class represents an element that has received focus. It is generally triggered when the user clicks or taps on an element or selects it with the keyboard's tab key.

![](https://velog.velcdn.com/images/devbang/post/85d1294f-ac69-4806-a274-a3125df5562c/image.png)

Notice that when we click the input, the background color changes to orange. The `:focus` pseudo-class only works if the content is focusable. Usually, those contents are called phrasing content. (`input`, `a`, `button`, `textarea`, `label`, `select`, etc.)

Regular content like `.box` cannot be focused, but when we add the `tabindex` global attribute, we can change the content to be focusable.

# 📌 Takeaway

- We need a `selector` to apply the CSS styling in a specific element in the HTML document.
- A selector is the first part of a CSS rule. It is a pattern of elements and other terms that tell the browser which HTML element should be selected to have CSS property values.
- Keeping the CSS syntax(indentation) is helpful to streamline the workflow and reduce errors.
- Generally, it is better to put the styles in an external stylesheet and apply them with `link` elements.
- The `@import` CSS at-rule imports rules from other valid stylesheets.
- The `@import` rule has a serial processing structure, and the `link` element has a parallel processing structure. Both have pros and cons, depending on how we use it.
- The child combinator (`>`) is placed between two selectors, and it matches only those elements matched by the second selector that are the direct children of the first element.
- The descendant combinator is typically represented by a single space (` `) character.
- The next-sibling combinator (`+`) matches only those elements matched by the second selector, the next sibling element of the first selector.
- We can use the subsequent-sibling combinator (`~`) to select siblings of an element that are not adjacent.
- A CSS pseudo-class is a keyword added to a selector that specifies a special state of the selected element.
- Only the phrasing content like `a`, `button`, `input`, `textarea` and `select` can be focused.
- If we want to make non-focusable elements focusable, we have to add the `tabindex` global attribute to the element.

# 💻 Solution

- None

# 🔖 Review

- Cascading Style Sheets or CSS is used to style and layout webpages.
- Internal CSS has a `style` tag inside the `head` section of the HTML document.
- Inline CSS is used to style a specific HTML element by adding a `style` attribute to each HTML tag without using selectors.
- We link the webpages to the external `.css` file. By editing this file, we can change the whole webpage at once.
- The universal selector (`*`) matches elements of any type.
- The type selector matches elements by node name.
- The class selector matches elements based on the contents of their `class` attribute.
- The ID selector matches an element based on the value of the element's `id` attribute.
- The `:hover` pseudo-class matches when the user interacts with an element with a pointing device.
- The `:active` pseudo-class represents an element that is activated by the user.
- The `:focus` pseudo-class represents an element that has received focus.
