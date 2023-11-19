---
layout: single
title: "[Frontend] TIL Frontend project - Dive into Web"
categories: Frontend
tag: [Frontend, HTML, CSS, JavaScript, TIL]
permalink: /categories/frontend/
toc: true
published: false
---

![](https://velog.velcdn.com/images/devbang/post/af7f72ea-d3e6-4cb3-b98d-a9fb68176eea/image.png)

# FASTCAMPUS Frontend Project

## Dive into Web

> 패스트캠퍼스 - [프론트엔드 웹 개발의 모든 것 초격차 패키지 Online](https://fastcampus.co.kr/dev_online_fesignature) 과정

# 🧩 What I Should Learn?

- Document Type Definition
- HTML, HEAD, BODY
- Connecting CSS and JS files with HTML
- Exploring Tags
- Displaying images on the website
- Relative Paths vs Absolute Paths
- Divide and Link Pages
- Developer Tools

# 🎯 What I learned today

## Document Type Definition

### Structure of Document

When we creating a HTML document, it can be divided into three main parts, and the top of the document, we can see the `DOCTYPE` tag.

![](https://velog.velcdn.com/images/devbang/post/db341a4e-e776-411c-91f2-97d061f8491d/image.png)

### DTD

A DTD or document type definition in simple term, is a set of rules that describes the structure and the legal elements of a specific type of document.

The DTD specification file can be used to validate documents.

Nowadays the HTML5 is the standard, but sometimes if we work with the legacy codes, we can encounter the `XHTML` version, and following pattern is the typical for XHTML.

```html
from wikipeida...

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

## HTML, HEAD, BODY

### HTML tag

Recall this html structure again from this picture.

![](https://velog.velcdn.com/images/devbang/post/db341a4e-e776-411c-91f2-97d061f8491d/image.png)

Notice that `<html></html>` tags are wrap the entire docuemnt. The html tag represents the root(top-level element) of an HTML document, and called as the root element. - [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#main_root)

The html tag let browser know where the documents start and end, or the _**area**_ of the document. All elements must be descendants of this element.

### HEAD tag

The head tag contains machine-readable _**information**_, or metadata in technical term. The head tag has the metadata about the document, such as title, scripts, and stylesheets(CSS).

These informations or the content within `<head>` tag doesn't appear as part of the main content, but provides important information for browsers.

### BODY tag

The body tag represents the content of an HTML document. There can be only one body tag in a document. Also, it is where the _**structure**_ and presentation of the webpage are defined, and the part of the document that users interact with.

The content within the `<body>` tag includes text, images, links, forms and other HTML elements that make up the actual webpage.

## Connecting CSS and JS files with HTML

### Create a CSS file

We have seen a html structure and capability of each three main parts through out the course. Let's write some actual content in the body tag.

![](https://velog.velcdn.com/images/devbang/post/e8cf39a0-f8f4-4fa8-9534-0add84d9b40c/image.png)

Notice that our content `Hello, world!` goes inside of the body tag. To style this html document, we need a CSS file.

After create the CSS file, indeed the html file doesn't know what CSS file is, so we need to connect html file with the CSS file.

![](https://velog.velcdn.com/images/devbang/post/6171e7ec-31bb-40c8-ab2f-838aa3923a53/image.png)

### CSS file setting

CSS file has `div` attribute, and has `color: red;` and `font-size: 100px`.

To connect the CSS file, we need a certain form of syntax, and we'll go over the details of the syntax later.

```html
<link rel="stylesheet" href="./main.css" />
```

This is the required syntax to connect or communicate with CSS file and if the color changes, html file now applies that color.

In the `href=""`, reference the CSS file path, and `./` means the current directory. Which means we are in the same directory, and we want to call a file called `main.css`.

### JS file setting

Similar to CSS file, create a `main.js` file and type `console.log("your message here")`.

To connect the JS file, of course we need to add the syntax, and the follow code is the syntax for JS file.

```js
<script src="./main.js"></script>
```

The `src=""` asks where is the `main.js` file path is, and by using the same pattern with CSS, we can connect JS file with html file.

![](https://velog.velcdn.com/images/devbang/post/ed4f1bbf-c387-4031-ae36-4cfc6b887b36/image.png)

When we go to the browser and open the developer tool with `f12 key`, we can see that our message printed out in the `console` tab.

## Exploring Tags

### Title tag

The `<title>` HTML element defines the document's title that is shown in a browser's title bar or a page's tab.

![](https://velog.velcdn.com/images/devbang/post/d9e6e863-3ecd-4a27-8dc4-f3fe179c0235/image.png)

### Link tag

The `<link>` HTML element specifies relationship between the current document and an external resource. This element is most commonly used to link to stylesheets, but it also used to establish site icons.

```html
<link rel="stylesheet" href="./main.css" />
<link rel="icon" href="./favicon.png" />
```

The `rel` stands for the relationship, and the `href` attribute specifies the path to the external resource. The favicon in this case, stands for favorite icon, and often say logo, that displayed on the page's tab.

### Style tag

The `<style>` HTML element contains style information for a document, or part of a document. It contains CSS, which is applied to the contents of the document containing the `<style>` element.

In general, it is better to put styles in external stylesheets and apply them using `<link>` element - [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/style#try_it)

![](https://velog.velcdn.com/images/devbang/post/d6ebe392-d1d2-44d9-8a6d-324c1c213501/image.png)

### Script tag

The `<script>` HTML element is used to embed executable code or data. This is typically used to embed or refer to JavaScript code.

![](https://velog.velcdn.com/images/devbang/post/91121dde-aec6-479f-a3fe-105a5e4ec786/image.png)

Like the `<style>` tag, the `<script>` tag also can link the external resource with the `src` attribute, and the internal JavaScript code inside of the tag.

The `src` stands for the source, and we can use the path to the external resource here as well.

### Meta tag

The `<meta>` HTML element represents metadata(machine-readable information) that cannot be represented by other HTML meta-related elements, such as the above four tags.

```html
<meta charset="UTF-8" />
<meta name="author" content="my content" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

There are so many information we need to go through to explain what `UTF-8` or the `viewport` means, so if interested, please check out [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta).

In a simple term, `charset` attributes declares the document's character encoding. The `UTF-8` is a character encoding standard related to unicode.

The `name` and `content` attributes are used to provide document metadata, in terms of name-value pair. The `name` attribute giving the metadata name, and the `content` attribute giving the value.

The `viewport` is the area of the window in which web content can be seen. The tag above is a typical mobile-optimized site' tag, which the `device` means our mobile device, and the `initial-scale` controls the zoom level when the page is first loaded. More information on [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Viewport_meta_tag).

## Displaying images on the website

### Basic folder structure

Before we dive in to diplaying images, download your logo from the internet. we can use the developer tools to download, or simply download it from the internet.

To manage our logo and the other files, we follow the basic HTML folder structure like following:

```
test(project)
│   index.html
│
└───css
│     main.css
│
└───images
│     logo.png
│
└───js
│     main.js
│
└───────────
```

To whom may not understand the structure above, this is the folder structure from VS Code. Important note that `index.html` file should be always in the root folder, because the browser finds the html file called `index` foremost.

![](https://velog.velcdn.com/images/devbang/post/ae097074-1873-4b0f-945f-5b0391237c1b/image.png)

### Displaying image and correct the file path

To display our image on the website, we need to add a `<img>` HTML element with the `src` attribute. Keep in mind that this element goes right below the `div`.

```html
<div>Hello world!</div>
<img src="./images/logo.png" alt="github-logo" />
```

Notice that now the local server displaying the image. If it is not displayed, check the typo or maybe the picture size is to big to display, so we will give it a size shortly.

There is one more weird thing going on, which is our text was red before, but now it is not. That's because we have the wrong path.

![](https://velog.velcdn.com/images/devbang/post/28bf3b7b-687d-4e6d-8bfa-7e07d51fbd8d/image.png)

Fix the file path same with the picture above. The bottom `img` tag indicates we can display image file from various path. Additionally, the HTMLImageElement property `alt` provides fallback(alternate) text to display when the image is not loaded.

## Relative path vs Absolute path

### Relative path

Relative path or Relative path name specify a directory or file based on current working directory. Relative path name traces the path from the current working directory through its parent or its subdirectories and files.

![](https://velog.velcdn.com/images/devbang/post/785eccac-0e8a-4923-9ba8-9900791c727a/image.png)

When our project folder sturcture looks like this and we want to bring `index.css` to `index.html`, we have to use `./` symbol since the resources folder and `index.html` file are in the same level.

Then, go into the resources folder with the file name `./resources/css/index.css`. Alternatively, we can omit `./`, and use `resources/css/index.css` in such a way that we discussed above.

Additionally, suppose if we have image folder like our folder structure above and we want to use it in CSS file. In that case, we should go up to the root directory, then find the `images/logo.png`.

```html
# From our folder structure, to get logo.png from CSS file ../images/logo.png
```

To wrap up, `./` represents the concept of navigating through nearby files and directories, while `../` represents of moving up to the parent folder and exporing surrounding files and directories.

### Absolute path

Absolute path or Absolute path name represents the complete name of a directory or file from the `/ or (root)` directory downward. Regardless of current working position in the file system, we can always find directory or file with the absolute path name.

Absoulte path name traces the path from the root directory, and always begin with the `/` symbol. Where it comes with the http protocol, usually means the recourses address on the internet like the image address that we copied for image above.

We can achieve the same result above by adding this line in html file as well as in the css file.

```
# To get logo.png from both index.html and CSS file

/images/logo.png
```

Notice that we don't have `. or ..` sign and solely the `/` sign. The `/` sign means we are starting from the `root`. More precisely, our address bar contais local address similar to `http://localhost:{portnumber}/{foldername}/index.html`.

We are accessing from that address, the root folder, and getting the `index.html` file. Same process, but by running `/images/logo.png`, we are getting the logo file from this address `http://localhost:{portnumber}/images/logo.png`.

Same story short, we can access the public website with the above method and difference is the `https://` protocol, and the address part is not local address but the public address.

### Localhost

If we check the live server, the port number should be displayed. And on the browser, address bar has the address like below:

```html
# The port number can be vary, in this case the number is 3000
http://127.0.0.1:3000/...{your path name}/index.html
http://localhost:3000/...{your path name}/index.html
```

Localhost is a host name that refers to the local machine currently making the request. In essence, localhost is our development environment and we can say it as local environment.

## Divide and Link Pages

### How to link another page

To link another page into the `index.html` file we can use the `<a>` HTML element.

The anchor element and its `href` attribute creates a _**hyperlink**_ to web pages, files, email addresses, locations in the same page, or anything else a URL can address.

The `href`, stands for hypertext reference, is an attribute where we can input the path and navigates to the provided URL.

We can link to another page with this `<a>` tag like this:

```html
<a href="https://www.google.com">Google</a>
```

Notice that we type the Google, because we need a content to interact. And we will see the blue text, when we click the text, the text bring us to the provided URL.

### Create and Link new page

Suppose we want to add another page called `about`, we need to create the html file, and link to that file as following:

```html
<a href="/about/about.html">About</a>
```

The anchor tag means that we are going to explore the path from the root to about folder. Then, it finds the file named `about.html`.

The address before the `/` is omitted, and it can be our localhost address, or the actual web page address when we upload this file into the server.

Important note is the browser finds `index.html` as default, so we can change the `about.html` inside of `about` folder to `index.html`.

![](https://velog.velcdn.com/images/devbang/post/908396e1-322e-43c8-9ff6-127e75ed2d64/image.png)

Then, we can change our path above to this:

```html
<a href="/about/about.html">About</a> # old address

<a href="/about">About</a> # new address
```

Also, we can add `Home` button like the below picture.

![](https://velog.velcdn.com/images/devbang/post/ff1b833a-a738-40ff-8894-71060aeb2682/image.png)

We learned that the `root` path is the absolute path and means our localhost address or the published webpage address. Hence, the `href="/"` means `href="{our address}/index.html"` but omitted, and it brings us to the `root` path or a homepage.

## Developer tool

### Temporary style change

When we open up the developer tool in browser, we can see many different tabs are opened. We are focusing on HTML now, but later we will interact much more with console when we start using JavaScript.

![](https://velog.velcdn.com/images/devbang/post/94e20d7a-1aec-47aa-b544-246c5bd319a1/image.png)

Click the element with the developer tool `inspector` or press `cmd + shift + C` and click the element. Modify the color or any attribute you want to add, once you reload the page, all the changes will disappear.

Another interesting thing that we can do is when we `hover` over the image or text, the content of the web interact with the mouse pointer.

We will go through the CSS selector and what it means in CSS chapter, but when we click the `:hov` button and check the checkbox, we can see what kind of styles applied to that content.

![](https://velog.velcdn.com/images/devbang/post/6b053095-f424-4c36-8e3a-4e64f45e562e/image.png)

Notice the checkbox is orange and also the html tag is colored orange. The content on the web is now showing the `hover` style even though we don't place the mouse pointer there. Interact with those tags and see how the website changes accordingly.

![](https://velog.velcdn.com/images/devbang/post/5ed85151-bf4a-4034-baf8-4e4f9cfbc1ae/image.png)

There is another tab called `computed` showing that the selected element's CSS style implementation details and `box model` for margin, border and padding.

# 📌 Takeaway

-

# 💻 Solution

- None

# 🔖 Review

- d
-
