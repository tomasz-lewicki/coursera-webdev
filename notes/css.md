
# CSS

Anatomy of a CSS rule:

This rule changes property `color` to `blue` for every `p` html element.
```css
p{
    color: blue;
}
```

- finish with semicolon! (`;`)
- the rule will work for every paragraph in the document!


## Selectors

There are 3 kinds of selectors:
- element 
- class (defined with `.`)
- id (defined with `#`)

1. Element selector. Will select certain html __elements__. For example, paragraphs.
```css
p{
    color: blue;
}
```

2. Will target html elements belonging to a certain __class__.
html:
```html
<p class="blue-par">I'm blue </p>
<p>I'm not blue</p>
```

CSS:
```
.blue-par{
    color: blue;
}
```

3. ID selector

CSS:
```CSS
#par3{
    color: blue;
}
```

html:
```html
<p id="par2">I'm not blue</p>
<p id="par3">I'm blue</p>
```

## Combining selectors


1. Every paragraph that belongs to class `big`:
```css
p.big{
    font-size:20px;
}
```

2. Child selector. Every `p` that's a __direct__ child of `article`.
```css
article > p{
    color: blue;
}
```

3. Descendant selector. Similar to child, but applies to all descendants.
```css
article p{
    color: blue
}
```

## Pseudo-class selectors

Selectors that we want to activate based on some activity that user does:
- `:link`
- `:visited`
- `:hover`
- `:active` (the user pressed the button, but not yet released)
- `:nth-child`

__block__ element will try to take up as much horizontal space as its containing element will allow!

## Style placement
1. Inline styling: the least reusable
2. `<style>` element at the top of the page
3. External style sheets (`css` file):
- can be used on multiple pages
- you avoid re-downloading the same sheet over and over


## Conflict resolution

1. Cascading algorithm

- Last decleration wins!
- Last == the last processed one (html document is processed top-to-bottom)
- External CSS precedence depends on where it's linked (e.g. `<head>`)
- No conflict -> no problem: just mege the rules
  
2. Inheritance 
- Children inherit parents' rules
- This way, if we apply something to `<body>` (which is the root of the DOM tree), we apply it everything on the page.

3. Specificity
- A more specific rule wins!
- Order of specificity:
  - `style="..."`
  - ID
  - class
  - \# of elements (e.g. `div p{color: red;}`) has 2
- You can still override with `!important`

## Styling rules

Typical font setup:
```css
#myPar{
    font-family: Arial, Helvetica, sans-serif;
    font-family: "Times New Roman", Times, serif; /* typical serif setup*/
    color: #0000ff;
    font-style: italic; 
    font-weight: 900; /* value from 100-900. 400 is normal, 700 is bold */
    font-weight: bold; 
    font-size: 24px; /* Browser default is 16px */

    text-transform: lowercase;
    text-align: right; /* left, center, justify */
}
```

Relative font sizes:
```css
body{
    font-size: 200%; /* take browser's default and increase it by 20% */
    font-size: 2em; /* relative to M letter width*/
}
```

Relative font sizes have a __cumulative__ effect!


## Box Model

Every html element follows a __box model__.
This means that every element has:
- content (the meat)
- padding
- border
- margin

What's annyoing is that by default the prettyDiv will have 314px. (content+padding+border).
We can change it by changing `box-sizing` parameter from `content-box` to `border-box`.

```css
#prettyDiv{
    background-color: blue;
    padding: 5px;
    border: 2px;
    margin: 10px;
    width: 300px; 
    box-sizing: border-box; /* the sane choice */
}
```

How to apply `box-sizing: border-box;` to every element?

This will __not__ work! `box-sizing` is not inherited.
```css
body {
    box-sizing: border-box
}
```

Instead we have to use a wildcard selector:
```css
* {
    box-sizing: border-box
}
```

## Box Model: Margins

1. Horizontal margins add up.
2. Vertical margins collapse, and the cumulative margin has the larger value

## Box Model: Overflow

What happens if there's too much content in an element to display?
- by default the content will _overflow_
- We can change this behavior via `overflow` property

```css
body{
    oveflow: [visible|hidden|auto(automatic scrollbars)|scroll(scrollbars always on)];
}
```

## Positioning


- Floating
  - Floating takes the document out of the regular document flow!
  - To resume normal document flow, use the `clear` property
- Static (the default document flow)
- Relative
  - the element is positioned relative to it's `static` postion
  - achieved with `top`, `botom`, `left`, `right` offset properties
  - As far as the the rest of the elements is concerned, they act as if the offset element were still at its static postion.
- Absolute postioning
  - offsets are relative to the position of the nearrest non-static ancestor
  - if no ancestors, there's always the `html` element, which is set to `relative`
  - the other elements don't realize the element is there


## Media Queries

```
@media (max-width: 800px) /* if this evaluates to true, apply the styles in braces*/
{
    p{
        color: black;
    }
}
```

Combining queries
```
@media (min-width: 992px) and (max-width: 1200px) /* 'and' operator, the most common */
@media (min-width: 1200px) , (orientation: horizontal) /* 'or' operator */
```

Do not overlap breakpoints (results in convoluted/messy stylesheets)

## Responsive design

- Content should be like water, filling in different devices
- Sometimes visibility can change too, based on available space (we nmight collapse some stuff and add "Read more...").
- 12 column layout:
    + why? because it's divisible by 2, 3 and 4
    + can be nested

- By default a lot of browsers will zoom out (e.g. scale everything by 0.4)
- You can fix that by specifying: _(so ugly by the way!)_
```
<meta name"viewport", content="width=device-width, initial-scale">
```

## Bootstrap

- Your grid system has to be within a `class="container`
- `container-fluid` gives you padding
- __row__ - horizontal group of __columns__