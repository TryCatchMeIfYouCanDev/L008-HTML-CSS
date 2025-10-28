# LESSON EIGHT - CSS Fundamentals #

## 1. CSS Box Model ##

The Box Model is the fundamental model used by browsers to manage the layout of elements on a webpage, both horizontally and vertically. It defines how the total size of an element is calculated, considering four main components:

| Component | Description                                                             |
| --------- | ----------------------------------------------------------------------- |
| Content   | The area where the actual content (text, images) is displayed.          |
| Padding   | Transparent area surrounding the content.                               |
| Border    | The frame that wraps around the padding and content.                    |
| Margin    | Transparent space that separates the element from surrounding elements. |

### Key Properties ###

* `width`: sets the content width.
* `height`: sets the content height.
* `box-sizing: border-box`: includes padding and border in the width and height, making layout calculations more predictable.

### Element Behavior ###

* **Block elements**: default width 100%, occupying full container space. Percentage-based width is relative to the parent element.
* **Inline elements**: width and height depend on content and cannot be directly modified.

---

## 2. CSS Specificity ##

CSS specificity determines which styles are applied when multiple rules target the same element.

### Specificity Values ##

| Selector Type    | Example          | Specificity |
| ---------------- | ---------------- | ----------- |
| Tag              | `h1`             | (0,0,0,1)   |
| Class            | `.title`         | (0,0,1,0)   |
| ID               | `#title`         | (0,1,0,0)   |
| Tag + Class      | `h1.title`       | (0,0,1,1)   |
| Tag + ID         | `h1#title`       | (0,1,0,1)   |
| Tag + Class + ID | `h1.title#title` | (0,1,1,1)   |

### Important Notes ###

* Specificity sums in combined selectors: `div .class p` → (0,0,1,1)
* In case of a tie, the last declared CSS rule wins.
* `!important` overrides all specificity rules.

### Specificity Hierarchy ###

| Priority | Type                           | Example                                    |
| -------- | ------------------------------ | ------------------------------------------ |
| 1        | `!important`                   | `p { color: red !important; }`             |
| 2        | Inline styles                  | `<p style="color:red;">`                   |
| 3        | ID selectors                   | `#title { color: blue; }`                  |
| 4        | Class, attribute, pseudo-class | `.test {}` `[type="text"] {}` `a:hover {}` |
| 5        | Element                        | `p {}` `p::before {}`                      |
| 6        | Universal                      | `* {}`                                     |
| 7        | Descendant selectors           | `div p {}`                                 |
| 8        | Combinators (`+`, `>`, `~`)    | `div > p {}`                               |

---

## 3. CSS Pseudo-classes ##

Pseudo-classes define the style of an element based on its state or position within the document tree.

### Dynamic Pseudo-classes ###

| Pseudo-class | Description                            | Example                                     |
| ------------ | -------------------------------------- | ------------------------------------------- |
| `:hover`     | Element when hovered                   | `a:hover { text-decoration: none; }`        |
| `:active`    | Element when activated (e.g., clicked) | `button:active { background: gray; }`       |
| `:focus`     | Element in focus                       | `input:focus { border: 2px solid blue; }`   |
| `:checked`   | Checkbox or radio when selected        | `input:checked { outline: 2px solid red; }` |

### Link-related Pseudo-classes ###

| Pseudo-class | Description                   | Example                                      |
| ------------ | ----------------------------- | -------------------------------------------- |
| `:link`      | Unvisited link                | `a:link { color: blue; }`                    |
| `:visited`   | Visited link                  | `a:visited { color: purple; }`               |
| `:target`    | Element targeted by an anchor | `#section:target { background: lightgray; }` |
| `:any-link`  | Any hyperlink                 | `a:any-link { color: green; }`               |

### Genealogical Pseudo-classes ###

| Pseudo-class      | Description                      | Example                                 |
| ----------------- | -------------------------------- | --------------------------------------- |
| `:first-child`    | First child of a parent          | `p:first-child { font-weight: bold; }`  |
| `:last-child`     | Last child of a parent           | `li:last-child { color: red; }`         |
| `:nth-child(n)`   | nth child of a parent            | `tr:nth-child(2) { background: gray; }` |
| `:first-of-type`  | First of its type among siblings | `p:first-of-type { color: blue; }`      |
| `:last-of-type`   | Last of its type among siblings  | `p:last-of-type { color: green; }`      |
| `:nth-of-type(n)` | nth element of a type            | `p:nth-of-type(2) { color: purple; }`   |

---

## 4. CSS Selectors Overview ##

| Selector                           | Description                 | Example                                           |
| ---------------------------------- | --------------------------- | ------------------------------------------------- |
| Universal `*`                      | Select all elements         | `* { margin: 0; }`                                |
| Type                               | All elements of a type      | `p { color: blue; }`                              |
| Class `.`                          | Elements with a class       | `.box { background: red; }`                       |
| ID `#`                             | Element with ID             | `#header { font-size: 20px; }`                    |
| Descendant `A B`                   | B inside A                  | `div p { color: green; }`                         |
| Child `A > B`                      | Direct child                | `ul > li { list-style: none; }`                   |
| Adjacent `A + B`                   | First B immediately after A | `h1 + p { margin-top: 10px; }`                    |
| General sibling `A ~ B`            | All B after A               | `h2 ~ p { color: gray; }`                         |
| Attribute `[attr]`                 | Elements with attribute     | `[disabled] { opacity: 0.5; }`                    |
| Attribute equals `[attr="val"]`    | Exact match                 | `input[type="text"] { border: 1px solid black; }` |
| Attribute contains `[attr*="val"]` | Contains substring          | `[class*="btn"] { padding: 10px; }`               |
| Attribute starts `[attr^="val"]`   | Starts with                 | `[href^="https"] { color: blue; }`                |
| Attribute ends `[attr$="val"]`     | Ends with                   | `[src$=".jpg"] { border: 1px solid red; }`        |

---

## 5. Flexbox ##

Flexbox is a one-dimensional layout system for arranging items in a container, either in a row or column.

### Key Concepts ###

* **Flex Container**: parent element with `display: flex;`
* **Flex Items**: children of the container
* **Default behavior**: `flex-direction: row; flex-wrap: nowrap;`
* **Flex Wrap**: allows items to wrap onto multiple lines (`wrap`, `wrap-reverse`).

### Flex Container Properties ###

| Property          | Description                  | Values                                                                              |
| ----------------- | ---------------------------- | ----------------------------------------------------------------------------------- |
| `display`         | Activate Flex context        | `flex`, `inline-flex`                                                               |
| `flex-direction`  | Direction of main axis       | `row`, `row-reverse`, `column`, `column-reverse`                                    |
| `flex-wrap`       | Whether items can wrap       | `nowrap`, `wrap`, `wrap-reverse`                                                    |
| `justify-content` | Align items along main axis  | `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly` |
| `align-items`     | Align items along cross axis | `flex-start`, `flex-end`, `center`, `baseline`, `stretch`                           |
| `align-content`   | Align multiple lines         | `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `stretch`      |

### Flex Item Properties ###

| Property      | Description                                                        |
| ------------- | ------------------------------------------------------------------ |
| `flex-grow`   | How much an item can grow relative to others (default 0)           |
| `flex-shrink` | How much an item can shrink relative to others (default 1)         |
| `flex-basis`  | Initial size of an item before distributing space (default `auto`) |
| `flex`        | Shorthand for `flex-grow`, `flex-shrink`, `flex-basis`             |
| `align-self`  | Override `align-items` for single item                             |
| `order`       | Order of items; default 0                                          |

### Shorthand Properties ###

* `flex-flow`: combines `flex-direction` and `flex-wrap`.

### Notes ###

* Flexbox replaces the need for floats and clears in modern layouts.
* All items in the same row have equal height by default.
* Changing the order of items can be done with the `order` property instead of rearranging HTML.

---

** Useful Links **

* Steve Krug, *Don't Make Me Think!* (Web Usability)
1. https://en.wikipedia.org/wiki/Steve_Krug
2. https://www.amazon.de/Dont-Make-Think-Revisited-Usability/dp/9332542864/

*End of Class Notes Summary*
