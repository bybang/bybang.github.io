---
layout: single
title: "[Frontend] TIL Frontend project - CSS Properties part 3"

categories: Frontend
tag: [Frontend, HTML, CSS, JavaScript, TIL]

permalink: /frontend/TIL-FASTCAMPUS-009

toc: true
published: true
---

![](https://velog.velcdn.com/images/devbang/post/af7f72ea-d3e6-4cb3-b98d-a9fb68176eea/image.png)

# FASTCAMPUS Frontend Project

## CSS Properties part 3

> 패스트캠퍼스 - [프론트엔드 웹 개발의 모든 것 초격차 패키지 Online](https://fastcampus.co.kr/dev_online_fesignature) 과정

# 🧩 What I Should Learn?

- CSS Layout - part 2
- CSS Layout - part 3
- Flex Container - part 1
- Flex Container - part 2
- Flex items

# 🎯 What I learned today

## CSS Layout - part 2

### `position` value (continue)

#### `fixed`

The position value `fixed` is used when the element is removed from the normal document flow, and no space is created for the element in the page layout.

The element will position relative to its initial _containing block_, which is the viewport in the case of visual media.

We previously saw the example of the `absolute` where if it can't find the _positioned ancestor_, the element positions relative to the viewport.

That is not the best use case of `absolute`, whereas the `fixed` is built to position relative to the viewport.

![](https://velog.velcdn.com/images/devbang/post/9d33729e-7869-4520-a603-a8287dfb17d2/image.png)

Suppose we bring the previous example and set two container CSS identical. Then, by changing the `position` value from `absolute` to `fixed`, we can see that the box `2` pops out from its ancestors.

The most use case of the `fixed` value would be like this:

![](https://velog.velcdn.com/images/devbang/post/9b8921f1-ebb3-49e6-9cd7-cf51c661e399/image.gif)

Notice the element is fixed to the viewport, and when we scroll down, the element follows the viewport.

If we think about the website experience, the banner or ads are normally followed when we scroll down.

### Stacking Context

**Stacking context** is a three-dimensional conceptualization of HTML elements along an imaginary `z-axis` relative to the user, who is assumed to be facing the viewport or the webpage.

HTML elements occupy this space in priority order based on element attributes.

When the `z-index` property is not specified on any element, elements are stacked in the following order (from bottom to top):

1. The background and borders of the **root** element.
2. Descendant _non-positioned_ elements, in order of appearance in the HTML.
3. Descendant positioned elements in order of appearance in the HTML.

![](https://velog.velcdn.com/images/devbang/post/2b0fb6d6-d4bd-4c9d-a9f5-5f305b4a3e1e/image.png)

Notice the above picture has three boxes, the first one being the original state and the second having the stacked elements. The box `1` has the position value, but the position is not changed since there is no direction value like the `top`, `right`, or ``bottom`.

We placed the box `2`, 50px from the top and 50px from the left. It has the position value `absolute`.

Now, if we look back at the stack order conditions, the first box and the second boxes are the _positioned_ elements. The third box has no CSS properties in the picture.

Compared to the third box, the second box indeed should be the top of it because the third box is a _non-positioned_ element.

Then, if we compare the first and second boxes, the second box is still on the top of every element.

That's because of the first condition in stacking order. If we open and see the HTML structure, it looks like this:

```html
<div class="container1">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>
```

Notice the box `2` div element placed below the box `1` div element, or the box `2` element appears later in the HTML structure.

Hence, box `2` is on top of box `1`; technically speaking, box `3` will be the bottommost of the stacked elements because box `3` is the _non-positioned_ element.

### Using `z-index`

If we want to create a custom stacking order, we can use the `z-index` property on a _positioned_ element.

Imagine the page as a stack of layers, each with a number. Layers are rendered numerically, with large numbers above smaller ones.

![](https://velog.velcdn.com/images/devbang/post/77dfc962-706d-44ae-9d5d-ad4a6471d7ed/image.png)

When no `z-index` value is specified, elements are rendered on the default rendering layer (Layer 0).

If several elements share the same `z-index` value, stacking rules follow the above rules (Stacking without the `z-index` property).

![](https://velog.velcdn.com/images/devbang/post/fb91ef95-6055-4a57-b900-8f33f66d2b22/image.png)

Now, we make the CSS the same as the above and change the original box to have the same value as the second one.

Notice now that box `1` is on the top of the stacked elements because box `2` doesn't have the `z-index` value or the omitted `z-index` value is 0.

Another interesting point is the box `3`, which has the highest `z-index` value, but the value is not applied to the element.

That's because the box `3` is not a positioned element. In other words, the box `3` has a `position: static` property value, and we learned that if the `static` value is set, the position properties have **_no effect_**.

![](https://velog.velcdn.com/images/devbang/post/bc3023de-a71a-4a13-ae37-9f70ce47ca8e/image.png)

If we want to bring the box `3` on the top of the stacked elements, we can add the position value to the element as in the picture above.

Notice we change the `z-index` value to be the same as the box `1` to compare the order of the stacked elements.

We can't see it visually that the box `3` is on the top, but we know that the box `3` element appears below the box `1` element. Therefore, the box `3` is on the top, box `2` is in the middle, and so forth.

## CSS Layout - part 3

### `z-index`

The `z-index` CSS property sets the z-order of a positioned element and its descendants or _flex and grid_ items. Overlapping elements with a larger `z-index` value cover those with a smaller one.

The `z-index` property can be specified with an integer value (positive, zero, or negative), representing the element's position along an imaginary z-axis.

The initial value of `z-index` is `auto`, meaning the box does not establish a new local stacking context. The stack level of the generated box in the current stacking order is `0`, and this zero is the default value of `z-index`.

![](https://velog.velcdn.com/images/devbang/post/847cef56-db29-4910-b318-ff87fa8dd001/image.png)

Let's see the above example to review the `z-index`. The yellow box has the largest `z-index` value, but it is the last element in the stacking order because it is a `non-positioned` element.

The yellow box is on the top compared to the brown box because the yellow box has the `z-index` value.

Technically speaking, the brown box has the `z-index` value of `auto` or `0`, which means it has the same stacking order as the current stacking context.

![](https://velog.velcdn.com/images/devbang/post/8f339b95-40de-4930-ac27-f81fd8b7c9c1/image.png)

The above boxes are positioned elements, so we must compare the `z-index` value.

Indeed, we can see the yellow box is on top of the stacked elements because it has the largest value.

An important reminder is that we should avoid using the largest value like the one above without thinking of it because it is easy to stack on top of everything.

The largest value is easy to modify initially, but when the HTML and CSS get complicated, it takes time to manage the stacking context.

### Block formatting context

A block formatting context is a part of a visual CSS rendering of a webpage. It's the region in which the layout of block boxes occurs, and floats interact with other elements.

It is a large amount to cover this definition, and we will scratch the surface of the `absolutely` positioned element part. More details are available on the [MDN](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Block_formatting_context) website.

![](https://velog.velcdn.com/images/devbang/post/71d67f7d-9716-4c50-b6e8-f4da4883d671/image.png)

Notice there are two inline elements in the webpage. By default, the inline element is not a block-level element, which can't use the width and height properties.

However, the second span element uses the width and height property because it is an _**`absolutely` positioned element**_.

> An _**`absolutely` positioned element**_ is an element whose computed `position` value is `absolute` or `fixed`. The `top`, `right`, `bottom`, and `left` properties specify offsets from the edges of the element's containing block.

The containing block is the ancestor relative to which the element is positioned. If the element has margins, they are added to the offset. The element establishes a new block formatting context for its contents.

The definition shows that the first element is not absolutely positioned, although it is a _positioned element_.

![](https://velog.velcdn.com/images/devbang/post/85b415d7-120d-4249-876b-53a183cfa9e9/image.png)

Therefore, if we see an element like the above - an inline element uses a block formatting context or is absolutely positioned as an inline element - we assume that there is a `display: block;` property value is omitted.

## CSS Flex Container - part 1

### `flex`

The `flex` is a new value added to the CSS `display` property. For a long time, the only reliable cross-browser compatible tools available for creating CSS layouts were features like `positioning` and `floats`. In some ways, they are frustrating and also limiting.

![](https://velog.velcdn.com/images/devbang/post/96ce9c84-c23f-4dea-8f89-efeaf6334b48/image.png)

Notice we have familiar box layers in the above picture. In the second box, we add the `display: flex` property value and see that the container's items are horizontally aligned.

### Basic concept of Flexbox

The flexible box layout module, usually referred to as flexbox, was designed as a one-dimensional layout model and as a method that could offer space distribution between the items in an interface and powerful alignment capabilities.

When we describe flexbox as being one-dimensional, we are describing the fact that flexbox deals with layout in one dimension at a time - either as a row or a column.

### The two axes of flexbox

When working with flexbox, we must consider two axes - the **main axis** and the **cross axis**.

The main axis is defined by the `flex-direction` property, and the cross axis runs perpendicular to it.

#### The main axis

The main axis has four possible values: `row`, `row-reverse`, `column`, and `column-reverse`.

![](https://velog.velcdn.com/images/devbang/post/47d2ae23-faac-47db-a79b-440724f39333/image.png)

If we choose `row` or `row-reverse`, our main axis will run along the row in the _inline direction_.

Choose `column` or `column-reverse`, and our main axis will run from the top of the page to the bottom in the **_block direction_**.

![](https://velog.velcdn.com/images/devbang/post/d4fed3ee-ca2c-45aa-bcbd-3be2817546b0/image.png)

#### The cross-axis

The cross axis runs perpendicular to the main axis; therefore, if our `flex-direction` (main axis) is set to `row` or `row-reverse`, the cross axis runs down the columns.

![](https://velog.velcdn.com/images/devbang/post/1fabf8cd-6e0e-4c25-adf0-93db3438bd92/image.png)

The cross axis runs along the rows if the main axis is `column` or `column-reverse`.

![](https://velog.velcdn.com/images/devbang/post/90ebd055-7df4-4def-b472-4613f60779df/image.png)

### Start and end lines

Another vital area that we should know is how flexbox makes no assumptions about the writing mode of the document. In the past, CSS was heavily weighted towards horizontal and left-to-right writing modes.

With modern layout methods, we no longer assume that a line of text will start at the top left of a document.

![](https://velog.velcdn.com/images/devbang/post/d6dbfcbf-5737-40ba-9dc5-9668f76a48d9/image.png)

If the `flex-direction` is `row`, then the start edge of the main axis will be on the left, and the end edge will be on the right. Some exceptions depend on the languages, but we will not cover that here.

### The flex container

An area of a document that is laid out using a flexbox is called a **flex container**. To create a flex container, we set the area's `display` property to `flex`.

When we set the `display` property to `flex`, the direct children of that container become **flex items**.

A value of `flex` causes the element to become a block-level flex container, and `inline-flex` causes the element to become an inline-level flex container.

![](https://velog.velcdn.com/images/devbang/post/921b69ba-8fc5-492b-b3eb-ee086a1e4606/image.png)

The flex container uses the above values, and we will cover that in the following chapters.

### The flex item

The children of a flex container become flex items. The following picture shows the flex item values.

![](https://velog.velcdn.com/images/devbang/post/2a109d7d-dd0e-49d8-bd66-3b536ae93857/image.png)

### `display: flex`

Along with the `display: flex` property, we deal with the elements as block-level elements.

![](https://velog.velcdn.com/images/devbang/post/f8f7c5ed-62d7-4962-92f4-b5b0ba012f41/image.png)

Notice two containers don't have the width property, but their width is set to the viewport. Here, the containers are the flex container, and the orange boxes are the flex items.

We learned that if we make an element to the block level element, the width is auto, and it calculates to the viewport width as the block element tends to expand to its parent container size.

![](https://velog.velcdn.com/images/devbang/post/df5de05f-7572-4720-8ff9-ded6ce757083/image.png)

Notice we changed the orange box height accordingly to see the container. Also, we changed the `display` value to `inline-flex`.

Now, the containers are treated as the inline-level element. Therefore, the containers are stacked in one line from left to right.

We should distinguish the container and boxes in which the container indicates _flex container_ and the boxes indicate _flex item_.

### `flex-direction`

The `flex-direction` CSS property sets how flex items are placed in the flex container, defining the main axis and the direction.

The initial value of `flex-direction` is `row`, as we see the above main axis section.

If the `flex-direction` is `row`, the flex container's main axis is defined to be the same as the text direction. The **main-start** and **main-end** points are the same as the content direction.

![](https://velog.velcdn.com/images/devbang/post/7a0b9a09-3c5f-46e7-9b6a-660def9f8ba2/image.png)

Notice the two flex containers have different `flex-direction` values. The first container has the `row`, the initial value we regularly see on the elements.

The second container has the `flex-direction: row-reverse` property value, which means the main axis and cross axis are the same, but the **start** and **end** points are changed.

![](https://velog.velcdn.com/images/devbang/post/d6dbfcbf-5737-40ba-9dc5-9668f76a48d9/image.png)

If we bring back the image from above, the picture shows the typical start and endpoints. Now, if we go back to check the orange boxes, the second container's **main-start** and **main-end** points are flipped compared to the first container.

![](https://velog.velcdn.com/images/devbang/post/9af061fd-2067-480f-a7b5-00c724cd5357/image.png)

On the other hand, if we set the `flex-direction` value to `column` or `column-reverse`, we can see that the main axis changes to the column and is stacked from top to bottom. The cross-axis also changes accordingly.

![](https://velog.velcdn.com/images/devbang/post/d4fed3ee-ca2c-45aa-bcbd-3be2817546b0/image.png)

The **main-start** and **main-end** points are the same as the block direction, top to bottom. If the value is `column-reverse`, it flips the other way around.

## CSS Flex Container - part 2

### `flex-wrap`

The `flex-wrap` CSS property sets whether flex items are forced onto one line or can wrap onto multiple lines. If wrapping is allowed, it sets the direction in which the lines are stacked.

![](https://velog.velcdn.com/images/devbang/post/1d1f81c4-a1a2-4235-b9e6-bc6ab0502c18/image.png)

Notice that the first container boxes are shrunk to fit the boxes in one line. Meanwhile, the second container has a `flex-wrap: wrap` property value, and the boxes inside the second container maintain the original size.

That's because the `flex-wrap` property allows to wrap the content in multiple lines. We removed the `height` property and automatically set the height to be auto to expand the container height to fit the wrapped item size.

The initial value of `flex-wrap` is `nowrap`; if we don't set the `flex-wrap` property to `wrap`, the items in the container always try to shrink from displaying every element in one line.

### `justify-content`

The CSS `justify-content` property defines how the browser distributes space between and around content items along the **main-axis** of a flex container and the line axis of a grid container.

![](https://velog.velcdn.com/images/devbang/post/11089201-08c7-4d22-baaf-3170d66b1b26/image.png)

Notice the three most used values are aligned in order. Three containers are the flex container, and the items are aligned accordingly.

The `flex-start` aligns the items toward the edge of the alignment container depending on the flex container's main-start side.

The `center` aligns the items toward the center of the alignment container along the main axis.

The `flex-end` aligns the items toward the edge of the alignment container depending on the flex container's main-end side. Notice that the flex items order is unchanged because the main axis direction is unchanged.

### `align-content`

The CSS `align-content` property sets the space distribution between and around content items along a fclexbox's cross-axis or grid's block axis.

![](https://velog.velcdn.com/images/devbang/post/da669779-bea5-43b6-a382-982f8447cc24/image.png)

Notice the flex items align vertically or along the cross-axis. The biggest difference between the `align-items` is that the `align-content` has **no effect** on **single line** flex containers (i.e. ones with `flex-wrap: nowrap`).

Due to its limitations, the `align-content` property is not commonly used.

### `align-items`

The CSS `align-items` property sets the `align-self` value on all direct children as a group. In flexbox, it controls the alignment of items on the _**cross axis**_. In grid layout, it controls the alignment of items on the _**block axis**_ within their grid area.

![](https://velog.velcdn.com/images/devbang/post/b4238196-ba18-49c1-acd9-e7177e365213/image.png)

Notice that the flex items are multiple lines because of the `flex-wrap` property, which is distributed into two lines and aligns flex items with each line start and line end.

The blue lines indicate each line's **main-start** and **main-end**. The first box has the initial value of `align-items`, the `stretch` by default.

The `stretch` auto-sizes items equally enlarges to fill the container, respecting the items' width and height limits.

However, the above case differs from a typical use case for aligning multiple-line contents. We learned that to align multiple-line content simultaneously, we use the `align-content` property.

![](https://velog.velcdn.com/images/devbang/post/02ef72d4-ac61-4bbb-94c7-4ec8907ccaf3/image.png)

The above picture shows a more general usage of the `align-items` property. When the flex items are the single line without the `flex-wrap` property, it aligns flex items vertically.

The first container shows normal behavior when we don't set the `align-items` property. Meanwhile, the fourth container shows that the flex items are stretched.

That's because we explicitly set the flex items' height to `auto` or removed the height property. Therefore, the flex items are stretched, albeit we do not set the `align-items: stretch` property value.

The most common case is the third container, which we will be using when we want to align flex items in flex containers in the center of the element.

Remember that if we want to centralize the flex items, we need to set the `align-items: center` and the `justify-content: center` property values.

## CSS Flex items

### `order`

The `order` CSS property sets the order to lay out an item in a flex or grid container. Items in a container are stored by ascending `order` value and then by their source code order. Items not given an explicit `order` value are assigned the default value of `0`.

![](https://velog.velcdn.com/images/devbang/post/e8a3bdfd-8bf2-483d-96b7-9880d0608ec8/image.png)

Notice that the above is the demo model from the MDN website, indicating the initial value of `order`, which is `0`.

![](https://velog.velcdn.com/images/devbang/post/c648aaf9-208f-414e-9d2b-e30422d53b83/image.png)

Suppose we have a model like the above picture. The box `A` and `D` have the initial `order` value `0`. If we want to place beyond every box, we can set the `order` value to `-1`. If we want to stack the box at the end of the line, we can set the largest `order` value.

The benefit of the `order` property is that it allows the modification of the elements' order without modifying or editing the HTML structure.

### `flex-grow`

The `flex-grow` CSS property sets the flex grow factor, which specifies how much of the flex container's remaining space should be assigned to the flex item's main size.

Let's see the example below to understand flex-grow. We are setting the `flex-grow` property to the flex items.

![](https://velog.velcdn.com/images/devbang/post/4a4e2f59-0fdf-47cc-a0de-e9efd6c92068/image.png)

Notice if we set `flex-grow: 1` on each item, the box grows proportionally to fill the parent container.

The initial value of `flex-grow` is `0`, the default state in the first container indicating it.

When the value is set to `0`, it behaves like the normal box that has the width and height.

But, if we see the third and fourth containers, they don't seem proportional to their parent containers.

![](https://velog.velcdn.com/images/devbang/post/a5b7cd48-eba7-4bdc-a4bd-482e046ffc5a/image.png)

That's because the `flex-grow` uses the flex container's _**remaining space**_ to calculate how much the items can grow.

The third container has the space with the blue arrow in two pieces, and the `flex-grow` property divides the remaining space proportionally.

The fourth container has the space with the blue arrow, and only one box has the `flex-grow` property. Hence, the box with the `flex-grow` property occupies the whole remaining space.

### `flex-shrink`

The `flex-shrink` CSS property sets the flex shrink factor of a flex item. If all flex items are larger than the flex container, items shrink to fit according to `flex-shrink`.

![](https://velog.velcdn.com/images/devbang/post/bcffa277-c25b-47fd-84a2-d29893e06bec/image.png)

We have seen that if we reduce the flex container width, the flex items shrink proportionally to display all flex items in one line.

That was the default behavior or because of the initial value of the `flex-shirnk`. The initial value is `1`, which means it shrinks each item proportional to its value `(1:1:1)`.

If we don't want to shrink the flex items in the container, we can set the `flex-shrink` value to `0`.

### `flex-basis`

The `flex-basis` CSS property sets the initial main size of flex items. It sets the size of the content box unless otherwise set with the `box-sizing` property.

![](https://velog.velcdn.com/images/devbang/post/904c2cf6-45bb-4acd-9781-d966714dd918/image.png)

Notice that the initial value of `flex-basis` is `auto`, and it calculates the content area. Then it divides the remaining space proportionally `(1:1:2)` because of the `flex-grow` property.

![](https://velog.velcdn.com/images/devbang/post/a9c5ffb4-4493-42ca-9160-4632c026fe73/image.png)

The most common use case will be the `flex-basis: 0` to set the content area to `0` or make the flex items not consider the content area.

The first container in the above picture is not perfectly proportional, but the second container's flex items are exactly proportional `(1:1:2)`.

We can also set the `flex-basis` area with the `<length>` value to have an absolute area value.

![](https://velog.velcdn.com/images/devbang/post/0c3a449d-d104-4177-a030-b40c72528532/image.png)

Notice the content area is now `100px` because of the `flex-basis` property. Then, the remaining area is calculated and divided by the `flex-grow` property.

# 📌 Takeaway

- The `absolute` value positions relative to the viewport when it can't find the `positioned` ancestor, albeit it is not the best use case.
- Whereas the `fixed` value is designed for positioning the element relative to the viewport.
- When the `position: fixed` property value is set, the element will fix to the viewport and will follow the viewport when we scroll down the website.
- Stacking context is a three-dimensional concept of HTML elements along an imaginary `z-axis` relative to the user.
- There are multiple factors to calculate stacking order when `z-index` is not specified. They stack in the following orders:
  1. The background and borders of the root element.
  2. Descendant `non-positioned` elements in order of appearance in the HTML document.
  3. Descendant `positioned` elements in order of appearance in the HTML.
- The `z-index` property sets the z-order of a positioned element and its descendants or flex and grid items.
- The largest value like `9999` should be avoided as a `z-index` value because when the code gets complex, the stacking order will not work as expected if the rough value is used.
- The `absolutely` positioned element is an element that has the `position` value `absolute` or `fixed`.
- An inline element uses a block formatting context, or an `absolutely` positioned element has the default `display: block` property.
- The flexbox is a new value added to the CSS `display` property to solve the frustration and limit features with `positioning` and `floats`.
- The flexible box layout module is usually referred to as a flexbox.
- The flexbox is designed as a one-dimensional layout model with powerful alignment capabilities.
- The main axis has four possible `row`, `row-reverse`, `column`, and `column-reverse` values.
- The `row` will make the main axis run along the row in the inline direction, and the `column` will make the main axis run from the top to bottom in the block direction.
- A flex container is an area of a document laid out using a flexbox.
- When the `display: flex` property value is set to an element, the direct children of that flex container become flex items.
- A `flex` value makes a block-level flex container, and an `inline-flex` value makes an inline-level flex container.
- The `flex-direction` property defines the main axis and sets how the flex items are placed in the flex container.
- The `flex-direction` property defines the main-start and main-end points and changes if the `flex-direction` changes.
- The `flex-wrap` property determines how the flex items are displayed, either forced onto a single line or wrapped onto multiple lines.
- If the `flex-wrap: wrap` property is not set, the flex container's flex items always shrink and try to display all elements in one line. That is the default behavior in regular websites.
- The `align-content` property sets the space distribution between and around content items along a flexbox's cross-axis.
- The `align-content` property does not affect single-line flex containers. This property usually works with the `flex-wrap: wrap`.
- The `align-items` property controls the alignment of flex items on the cross-axis.
- The `order` property sets the order to lay out an item in a flex or grid container. It allows the elements' order to be changed without modifying or editing the HTML structure.
- The `flex-grow` property specifies how much of the flex container's remaining space should be assigned to the flex item's main size.
- The `flex-grow` property uses the flex container's remaining space to calculate how much items can grow.
- The initial value of the `flex-shrink` property is `1`, which explains why the elements shrink proportionally when the flex container shrinks.
- The `flex-basis` property sets the initial main size of the flex items.
- By setting the `flex-basis: 0` property value, the content area becomes zero, and the `flex-grow` property can perfectly divide the container with its value.

# 💻 Solution

- None

# 🔖 Review

- We use the `z-index` to create a custom stacking order.
- The initial value of `z-index` is `auto`, but this is considered as a `0` because it doesn't create a new stacking context and shares the same level with the parent by default.
- In simple terms, if the element is a `positioned element` with an `absolute` or `fixed` value, then we assume that `display: block` is omitted.
- The cross-axis runs perpendicular to the main axis.
- If the `flex-direction` is `row`, then the start edge of the main axis will be on the left, and the end edge will be on the right.
- The `justify-content` property defines how the browser distributes space between and around content items along the main axis of a flex container.
- By reducing a flex container that contains flex items, we can see that the items shrink proportionally to display all items in one line.
- If we don't want to shrink the flex items, we use the `flex-shrink: 0` property value.
