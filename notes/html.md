# HTML basics

### Why is html a  **markup** language?

_markup_ = annotation

For example:

```html
<title>How to sharpen yout knife</title>
```

This is content: `How to sharpen yout knife`
This is the markup `<title>   </title>`

### html tag
1. This is an html tag: `<p>` and `p` is the element
2. Some popular tags:
- `<br>` - line break
- `<hr>` - horizontal rule
3. Tag attirubtes
- Below `id` is an *attirubte name*, and `myParagraph` is an *attribute value*
```html
<p id="myParagraph">Hello!</p>
``` 
4. Spaces: You can put spaces everythere
5. Quotes:
   - Single (`'`) and double (`"`) quotes are the same thing
   - It's good practise to surround attirbute values with quotes
   - If you have multiple qoutes, you need to open them interchangeably. 
   - You can nest quotes to infinity and beyond
  
6. Self closing tags. For example a paragraph that's currently empty could be just: </p>. It's funky, so don't do that.

### Browser compatibility tools

1. `https://caniuse.com/` check tag-browser compatibility
2. `browserstack.com` check websites on old browsers 
3. `validator.w3.org/` check if html valid

### html file structure

Browsers always interpret html sequentailly (from top to bottom).
1. Start with 
```html
<!doctype html>
```

Why? If you don't, then the browser will try to render your page in "quirks" mode, 
along with all the old, non-standard compliant pages.

2. `<html>` tag: contains the entire document
3. `<head>` tag: contains metadata on how to render the main content, e.g. what character encoding it uses.
4. `<title>` tag: basically what goes omn the header of the tab in chrome
In other words, all the info that the browser should have `prior` to rendering the webpage.
5. `<body>` tag: the root of all content visible to the user

### Content model:
- block level element: start a newline by default. `<div>` (division) is the most generic block ement
- inline elements: stays in the same line. `<span>` is the most generic inline element

### Semantic elements:

`h1` tags are what we call _semantic elements_.
- That means, that they carry meaning aside from their content.
- _Semantic_ - relating to meaning in language or logic.
- For example, any `<div>` could be styled to look like `<h1>` heading, but wouldn't provide _description_ for the content (i.e. _what it is_).
- `h1` tag should convey the meaning of the rest of the content!

Other semantic elements:

- `<header>`: company logo, navigation bar, etc.
- `<nav>`: navigation
- `<section>`
- `<article>`
- `<aside>`
- `<footer>`

They are all block elements! Structurally they don't give you any more than a regular `<div>` tag, but semantically they do!


### Lists:

- Lists let us group related content.
- We use `<ul>` or `<ol>` tags for it
- We use `<li>` elements for each item.


### Html enities:

Often used for ecaping characters. You should always escape:
- `<`. Use `&lt;` instead.
- `>`. Use `&gt;`.
- `&`. Use `&amp;`.

Other for other useful characters:
- `©`. Use `&copy;`.
- `&nbsp;`: a non-breaking space.'

### Links

1. A typical link:
```html
<a href="/about" title="link to the 'about' page">About</a>
```

2. You can put a `div` inside of a link (useful when clicking on a company logo).
```html
<a href="/about" title="link to the 'about' page">
    <div>
    </div>
</a>
```

3. If you want the webpage to open in a new tab, you should specify attribute `target=_blank`.
Alternatively, the value of this attribute could to a different iframe (`target=_self`, )

4. Links starting with `#` (pound) (fragment identifiers) let you refer to a specific fragment of a webpage by their element ids.

<a href="#MyHtmlElementId"></a>

### Images

- <img> tag is an __inline__ element!
- It's a good idea to specify `width` and `height` of the image. The browser will then reserve space while loading (avoids "jumpy" loading).

