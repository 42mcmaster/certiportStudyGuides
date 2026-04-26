# Certiport ITS HTML & CSS — Student Study Guide

A self-paced review for the Certiport / GMetrix Information Technology Specialist (ITS) HTML & CSS certification exam.

---

## How to Use This Guide

This guide is structured as **thirteen short modules**, building from the foundations of an HTML document up through CSS layout, responsive design, and finishing with test-taking strategy. Work through them in order — each module assumes the ones before it.

Every module follows the same rhythm:

1. **Concept** — read the explanation.
2. **Anchor** — a small diagram, table, code snippet, or rule of thumb you should be able to redraw from memory.
3. **Self-check** — exam-style question(s) plus "explain the distractor" practice.

The single most powerful study habit for this exam is **explaining why the wrong answers are wrong**. If you can do that, the right answer takes care of itself.

### What This Exam Tests Most Heavily

Across the practice exams, the heaviest weight is on:

- **CSS selectors and properties** — class vs. ID vs. element, pseudo-classes, the cascade.
- **Document structure debugging** — boilerplate, nesting order, void elements.
- **HTML form and media tags** — inputs, methods, `<video>`, `<audio>`, `<track>`.
- **Semantic HTML5** — picking the correct tag (`<header>`, `<nav>`, `<article>`, etc.) for a layout description.
- **Box model and units** — borders, margin/padding shorthand, relative vs. absolute units.

Lighter coverage: deep Flexbox/Grid layout, transforms, and animations. Don't ignore them, but don't drown in them.

---

## Table of Contents

1. [HTML Document Structure & Syntax](#module-1--html-document-structure--syntax)
2. [Head, Metadata, SEO, and Comments](#module-2--head-metadata-seo-and-comments)
3. [Text Content & Typography](#module-3--text-content--typography)
4. [Lists, Tables, and Character Entities](#module-4--lists-tables-and-character-entities)
5. [Hyperlinks, Images, and Image Maps](#module-5--hyperlinks-images-and-image-maps)
6. [Forms and HTTP Methods](#module-6--forms-and-http-methods)
7. [Multimedia: Audio, Video, and Tracks](#module-7--multimedia-audio-video-and-tracks)
8. [Semantic HTML5 Elements](#module-8--semantic-html5-elements)
9. [CSS Selectors and Stylesheet Placement](#module-9--css-selectors-and-stylesheet-placement)
10. [The Cascade, Specificity, and Inheritance](#module-10--the-cascade-specificity-and-inheritance)
11. [Colors, Backgrounds, the Box Model, and CSS Units](#module-11--colors-backgrounds-the-box-model-and-css-units)
12. [Layout, Positioning, Responsive Design, and Accessibility](#module-12--layout-positioning-responsive-design-and-accessibility)
13. [Test-Taking Strategy and Final Review](#module-13--test-taking-strategy-and-final-review)
14. [Exam-Day Cheat Card](#exam-day-cheat-card)
15. [Master Glossary](#master-glossary)

---

## Module 1 — HTML Document Structure & Syntax

### Concept

The exam expects you to recognize a correct HTML5 boilerplate skeleton instantly and to debug improperly nested or unclosed tags. Most "what's wrong with this code?" questions fall into one of three traps: a tag in the wrong section (e.g., `<title>` outside `<head>`), tags closed in the wrong order, or a missing/incorrect closing tag.

### Anchor: The HTML5 Boilerplate

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page title shown in the browser tab</title>
    <meta charset="UTF-8">
  </head>
  <body>
    <h1>Largest heading — visible content</h1>
    <p>Paragraph of body text.</p>
  </body>
</html>
```

What goes where:

- **`<!DOCTYPE html>`** — must be the first line; tells the browser this is HTML5.
- **`<head>`** — *not* shown on the page. Holds `<title>`, `<meta>`, `<link>`, `<script>`, `<style>`.
- **`<body>`** — everything the user sees: headings, paragraphs, images, links, etc.

### Anchor: The Nesting Rule (LIFO)

Tags must close in **reverse** order of opening — last opened, first closed.

```html
✅  <p><strong>Hello</strong></p>
❌  <p><strong>Hello</p></strong>
```

### Anchor: Void / Self-Closing Elements

Some elements have no content and no closing tag:

```
<br>     line break
<hr>     horizontal rule
<img>    image
<input>  form input
<meta>   metadata
<link>   external resource
```

You may see them written with a trailing slash (`<br />`) — both forms are accepted in HTML5.

### Self-Check

> Which placement is correct?
> A) `<title>` inside `<body>`
> B) `<h1>` inside `<head>`
> C) `<title>` inside `<head>`, `<h1>` inside `<body>`
> D) `<meta>` inside `<body>`

**Answer:** C.
**Why the others are wrong:** A and B swap which section each tag belongs to. D puts metadata where it isn't recognized.

> Which line of code is improperly nested?
> A) `<div><p>Hello</p></div>`
> B) `<p><em>Hi</em></p>`
> C) `<div><p>Bye</div></p>`
> D) `<ul><li>Item</li></ul>`

**Answer:** C — `</div>` closes before `</p>` even though `<p>` opened last.

---

## Module 2 — Head, Metadata, SEO, and Comments

### Concept

The `<head>` is the page's behind-the-scenes control panel. The exam tests whether you know what each `<meta>` tag does, how scripts and fallbacks work, and how to write comments in HTML versus CSS versus JavaScript.

### Anchor: The Most-Tested `<meta>` Tags

| Tag                                                                  | What It Does                                          |
| -------------------------------------------------------------------- | ----------------------------------------------------- |
| `<meta charset="UTF-8">`                                             | Character encoding (replaces older `ISO-8859-1`)      |
| `<meta name="description" content="…">`                              | Page summary for search engines (SEO)                 |
| `<meta name="keywords" content="…">`                                 | Search keywords (legacy SEO)                          |
| `<meta name="viewport" content="width=device-width, initial-scale=1.0">` | Required for responsive design on mobile        |
| `<meta name="robots" content="…">`                                   | Tells crawlers whether to index/follow                |
| `<meta name="google" content="notranslate">`                         | Opts out of Google Translate                          |

### Anchor: Scripts and Fallbacks

```html
<script src="app.js"></script>      <!-- loads or embeds JavaScript -->
<noscript>JavaScript is required to use this page.</noscript>
```

`<noscript>` shows fallback content **only** when JavaScript is disabled or unsupported.

### Anchor: Comments by Language

Comments are non-rendered notes left for developers. Each language has its own syntax — the exam mixes them as distractors.

| Language    | Syntax                  |
| ----------- | ----------------------- |
| HTML        | `<!-- comment -->`      |
| CSS         | `/* comment */`         |
| JavaScript  | `// comment` (single line) or `/* */` (multi-line) |

### Self-Check

> Which `<meta>` tag is required to make a page render correctly on mobile devices?
> A) `<meta charset="UTF-8">`
> B) `<meta name="keywords" content="…">`
> C) `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
> D) `<meta name="description" content="…">`

**Answer:** C. Without the viewport tag, mobile browsers shrink the desktop layout to fit.

> Which is a valid CSS comment?
> A) `<!-- color is red -->`
> B) `// color is red`
> C) `/* color is red */`
> D) `# color is red`

**Answer:** C. A is HTML, B is JavaScript single-line, D isn't valid in either.

---

## Module 3 — Text Content & Typography

### Concept

Text is split between **block** elements (which break onto a new line and take the full width) and **inline** elements (which sit inside a line of text without breaking it). Most typography questions hinge on this distinction plus a small set of CSS font properties.

### Anchor: Block vs. Inline

```
BLOCK (breaks the line, takes full width):
  <h1>–<h6>  <p>  <div>  <section>  <article>  <header>  <footer>

INLINE (sits inside a line, no break):
  <span>  <a>  <strong>  <em>  <img>  <br>
```

A common trap: `<span>` looks like `<p>` to a beginner, but `<span>` does **not** break the line.

### Anchor: Heading Hierarchy and Line Tools

- `<h1>` is the largest, `<h6>` is the smallest. Use them in order; don't skip levels for styling.
- `<br>` — line break with **no** blank line skipped.
- `<hr>` — horizontal rule (a line across the page).
- `<p>` — paragraph; produces blank space above and below.

### Anchor: The CSS Typography Toolkit

| Property                  | Example                                       | What It Does                                  |
| ------------------------- | --------------------------------------------- | --------------------------------------------- |
| `font-family`             | `font-family: "Helvetica", Arial, sans-serif;`| Font with **fallbacks**, ending in a generic family |
| `font-size`               | `font-size: 16px;` or `1em`                   | Text size                                     |
| `font-weight`             | `font-weight: bold;` / `400` / `700`          | Boldness                                      |
| `font-style`              | `font-style: italic;`                         | Italic / normal                               |
| `font-variant`            | `font-variant: small-caps;`                   | Small caps                                    |
| `line-height`             | `line-height: 1.5;`                           | Vertical spacing between lines                |
| `text-decoration`         | `text-decoration: underline;` / `none`        | Underline / strike / none                     |
| `text-indent`             | `text-indent: 2em;`                           | First-line indentation                        |
| `letter-spacing`          | `letter-spacing: 0.05em;`                     | Spacing between characters                    |
| `word-wrap` / `overflow-wrap` | `overflow-wrap: break-word;`              | Forces long words to wrap                     |

The exam loves `font-family` fallbacks. The list goes from most specific to most generic, ending in a generic family (`serif`, `sans-serif`, `monospace`, `cursive`, `fantasy`).

### Self-Check

> Which element is inline and does **not** force a line break?
> A) `<p>`
> B) `<span>`
> C) `<div>`
> D) `<section>`

**Answer:** B.

> Which CSS rule applies a fallback chain ending in a generic family?
> A) `font-family: Arial;`
> B) `font-family: "Open Sans", Arial, sans-serif;`
> C) `font: bold;`
> D) `font-family: sans-serif, "Open Sans";`

**Answer:** B — specific name, fallback name, generic family at the end. D has the order reversed.

---

## Module 4 — Lists, Tables, and Character Entities

### Concept

Three small but reliable question clusters: choosing the right list type, building a basic table, and spelling reserved characters using HTML entities.

### Anchor: List Types

| Tag      | Use For                                                     | Renders As            |
| -------- | ----------------------------------------------------------- | --------------------- |
| `<ul>`   | **Unordered** — order doesn't matter                        | Bullets               |
| `<ol>`   | **Ordered** — sequence matters (steps, ranking)             | Numbers               |
| `<dl>`   | **Description list** — terms paired with definitions        | Term / definition     |

`<dl>` uses `<dt>` (term) and `<dd>` (definition) inside it.

### Anchor: The Table Skeleton

```html
<table>
  <caption>Sales by Quarter</caption>
  <tr>
    <th>Quarter</th>
    <th>Revenue</th>
  </tr>
  <tr>
    <td>Q1</td>
    <td>$120,000</td>
  </tr>
</table>
```

- `<table>` — the container.
- `<caption>` — the table's title.
- `<tr>` — table row.
- `<th>` — header cell (bold, centered by default).
- `<td>` — data cell.
- `colspan="N"` — make a cell span multiple columns.
- `rowspan="N"` — make a cell span multiple rows.

### Anchor: Common Character Entities

| Entity      | Renders As |
| ----------- | ---------- |
| `&copy;`    | ©          |
| `&lt;`      | <          |
| `&gt;`      | >          |
| `&amp;`     | &          |
| `&nbsp;`    | (non-breaking space) |
| `&quot;`    | "          |

Use entities whenever you need to display a reserved character (`<`, `>`, `&`) as text rather than as code.

### Self-Check

> A recipe lists steps that must be followed in order. Which list type fits best?
> A) `<ul>`
> B) `<ol>`
> C) `<dl>`
> D) `<dir>`

**Answer:** B. Steps in sequence → ordered list.

> Which entity renders the `<` character so a browser does not interpret it as the start of a tag?
> A) `&copy;`
> B) `&lt;`
> C) `&nbsp;`
> D) `&amp;`

**Answer:** B.

---

## Module 5 — Hyperlinks, Images, and Image Maps

### Concept

The `<a>` and `<img>` tags appear all over the exam. You need fluency in their attributes, in **relative vs. absolute** paths, and in the `<map>` / `<area>` system for clickable hotspots.

### Anchor: The Anchor Tag

```html
<a href="https://example.com">External link</a>
<a href="about.html">Internal page</a>
<a href="#section2">Jump within the same page</a>
<a href="https://example.com" target="_blank">Opens in a new tab</a>
```

- `href` — destination URL or fragment.
- `target="_blank"` — opens link in a new tab/window.
- Fragment links pair `href="#id"` with an element that has `id="id"` somewhere on the page.

### Anchor: Absolute vs. Relative URLs

```
ABSOLUTE   →  https://example.com/images/logo.png   (full URL)
RELATIVE   →  images/logo.png                       (same folder + subfolder)
              ../styles/main.css                    (parent folder)
              /assets/style.css                     (site-root relative)
```

Given a folder tree, you'll be asked to pick the correct path. Memorize: `..` means "go up one level."

### Anchor: The Image Tag

```html
<img src="images/cat.png"
     alt="A black cat sitting on a windowsill"
     title="My cat, Pepper"
     width="320" height="240">
```

- **`src`** — image path.
- **`alt`** — text shown if the image fails to load and read aloud by screen readers (accessibility-critical).
- **`title`** — tooltip shown on hover.
- **`width` / `height`** — pixel sizing.

### Anchor: Clickable Images and Image Maps

To make a whole image a link, wrap it:

```html
<a href="home.html"><img src="logo.png" alt="Home"></a>
```

To make **specific regions** of an image clickable, use an image map:

```html
<img src="floorplan.png" alt="Floor plan" usemap="#rooms">
<map name="rooms">
  <area shape="rect" coords="34,44,270,350" href="kitchen.html" alt="Kitchen">
  <area shape="circle" coords="500,200,80" href="patio.html" alt="Patio">
</map>
```

Common trap: `<map>` is **not** for geographic latitude/longitude maps. It's for clickable hotspots on an `<img>`.

### Self-Check

> A page in `/projects/index.html` needs to link to `/styles/main.css`. Which relative path works?
> A) `main.css`
> B) `../styles/main.css`
> C) `styles/main.css`
> D) `./main.css`

**Answer:** B. Go up one level out of `/projects/`, then down into `/styles/`.

> Which attribute provides the fallback/accessibility text for an image?
> A) `title`
> B) `alt`
> C) `name`
> D) `caption`

**Answer:** B. `title` is the hover tooltip; `alt` is the accessibility text.

---

## Module 6 — Forms and HTTP Methods

### Concept

Forms are tested in two layers: which **HTTP method** the form uses to submit, and how the form's **inputs and labels** are structured.

### Anchor: HTTP Methods

| Method   | Purpose                                  | Notes                                            |
| -------- | ---------------------------------------- | ------------------------------------------------ |
| **GET**  | Retrieve / read data                     | Parameters appear **in the URL** (visible)       |
| **POST** | Create / submit new data                 | Parameters in the request body (not in the URL)  |
| **PUT**  | Update / replace existing data           |                                                  |
| **DELETE** | Remove data                            |                                                  |

A common exam trap: "Which method should be used to submit sensitive form data?" → **POST**, because GET would expose the data in the URL.

### Anchor: A Basic Form

```html
<form action="/signup" method="post">
  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required>

  <label for="age">Age:</label>
  <input type="number" id="age" name="age" min="13" max="120" value="18">

  <label for="bio">Bio:</label>
  <textarea id="bio" name="bio" rows="4" cols="40" maxlength="200"></textarea>

  <label for="role">Role:</label>
  <select id="role" name="role">
    <option value="student">Student</option>
    <option value="teacher">Teacher</option>
  </select>

  <button type="submit">Sign up</button>
</form>
```

Things to memorize:

- **`<label for="x">` pairs with `<input id="x">`** — clicking the label focuses the input. Crucial for accessibility.
- **`name`** is what gets submitted; **`id`** is for CSS/JavaScript targeting and for label association.
- **`required`** — boolean attribute that blocks submission when empty.
- Common input `type` values: `text`, `email`, `number`, `password`, `radio`, `checkbox`, `submit`, `date`.
- **`<textarea>`** uses `rows`, `cols`, `maxlength`.
- **`<select>` + `<option>`** = dropdown menu.

### Anchor: Submitting and Embedding

- `<button type="submit">Send</button>` and `<input type="submit" value="Send">` both submit the form.
- `<iframe src="page.html" width="600" height="400">` embeds another page. Watch the attributes — `src`, not `href`.

### Self-Check

> Which input would best collect a user's age, restricting it to whole numbers between 13 and 120?
> A) `<input type="text" maxlength="3">`
> B) `<input type="age">`
> C) `<input type="number" min="13" max="120">`
> D) `<input type="range">`

**Answer:** C.

> Which HTTP method appends form data to the URL and is therefore unsafe for sensitive information?
> A) GET
> B) POST
> C) PUT
> D) DELETE

**Answer:** A.

---

## Module 7 — Multimedia: Audio, Video, and Tracks

### Concept

HTML5 `<video>` and `<audio>` elements have a small set of attributes the exam tests heavily. The newer `<track>` element is the additional twist on Practice Exam 2.

### Anchor: The `<video>` Element

```html
<video controls width="640" height="360">
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.mov" type="video/quicktime">
  <track src="subs.vtt" kind="subtitles" srclang="en" label="English">
  Your browser does not support the video tag.
</video>
```

- **`controls`** — boolean attribute that shows play/pause UI. Either present or absent (`controls` or `controls="controls"`).
- **Multiple `<source>` children** — the browser uses the first format it can play.
- **`type`** — the MIME type (e.g., `video/mp4`, `audio/mp3`).
- **Fallback text** between the tags is shown by browsers that don't support the element.
- **`<track>`** — adds captions or subtitles via a `.vtt` file. Attributes:
  - `src` — `.vtt` file path
  - `kind` — `subtitles` or `captions`
  - `srclang` — language code (e.g., `en`)
  - `label` — human-readable label

### Anchor: The `<audio>` Element

```html
<audio controls>
  <source src="song.mp3" type="audio/mp3">
  <source src="song.ogg" type="audio/ogg">
  Your browser does not support the audio tag.
</audio>
```

Same rules as `<video>`: `controls` is boolean, multiple `<source>` for format fallback, fallback text inside the element.

### Self-Check

> Which attribute, when present, makes a `<video>` element show play/pause controls?
> A) `play`
> B) `controls`
> C) `autoplay`
> D) `interface`

**Answer:** B.

> Which element provides captions for a video, sourced from a `.vtt` file?
> A) `<source>`
> B) `<caption>`
> C) `<track>`
> D) `<subtitle>`

**Answer:** C. `<caption>` is for tables, not video.

---

## Module 8 — Semantic HTML5 Elements

### Concept

Semantic tags describe **what** content is, not **what it looks like**. The exam constantly gives you a layout description and asks you to pick the matching tag.

### Anchor: The Semantic Map

```
┌─────────────────────────────────────────────────┐
│ <header>   site banner / page header            │
├──────────────────────────┬──────────────────────┤
│ <nav>      links menu                           │
├──────────────────────────┼──────────────────────┤
│ <main>     primary content area                 │
│   <article> a single self-contained story       │
│   <section> a thematic grouping of content      │
│   <figure>  image + <figcaption> caption        │
│                          │ <aside> sidebar / related notes │
├──────────────────────────┴──────────────────────┤
│ <footer>   page footer (copyright, contacts)    │
└─────────────────────────────────────────────────┘
```

### Anchor: Tag → Purpose

| Tag                    | Use When                                                      |
| ---------------------- | ------------------------------------------------------------- |
| `<header>`             | Page or section banner — logo, title, intro                   |
| `<nav>`                | Group of navigation links                                     |
| `<main>`               | The page's primary content (only one per page)                |
| `<section>`            | A thematic group of content with its own heading              |
| `<article>`            | A single self-contained story / post / item                   |
| `<aside>`              | Side note related to the main content (sidebars, callouts)    |
| `<figure>` + `<figcaption>` | Image (or chart, code block) with a caption             |
| `<footer>`             | Page or section footer — copyright, contact info, small print |
| `<address>`            | Contact information for the author or owner                   |
| `<details>` + `<summary>` | Collapsible / expandable content (no JS needed)            |

### Anchor: Generic Containers vs. Semantic Tags

- **`<div>`** — generic block container; reach for it only when no semantic tag fits.
- **`<span>`** — generic inline container; same idea, inline.

If a `<section>`, `<article>`, `<header>`, or other semantic tag fits, use it instead of `<div>`. The exam rewards picking the most specific tag.

### Self-Check

> A blog page has many independent posts, each with its own heading and content. Which tag best wraps each post?
> A) `<div>`
> B) `<section>`
> C) `<article>`
> D) `<aside>`

**Answer:** C. A self-contained piece of content → `<article>`.

> Which element creates an expandable / collapsible block without JavaScript?
> A) `<details>` and `<summary>`
> B) `<aside>` and `<header>`
> C) `<section>` and `<footer>`
> D) `<div>` and `<span>`

**Answer:** A.

---

## Module 9 — CSS Selectors and Stylesheet Placement

### Concept

CSS questions on this exam fall into two big buckets: **where** to put styles, and **how** to target the right elements with selectors. Practice Exam 2 specifically asks students to drag-rank stylesheet types and selectors by precedence, so this is high-leverage material.

### Anchor: Three Places to Put CSS

| Type                     | Where It Lives                                  | Best For                                       |
| ------------------------ | ----------------------------------------------- | ---------------------------------------------- |
| **External stylesheet**  | A separate `.css` file linked via `<link>` in `<head>` | A whole site — reuse across many pages   |
| **Internal / embedded**  | Inside `<style>` in the page's `<head>`         | Styling **one** page only                      |
| **Inline**               | `style=""` attribute on a single element        | A single element only — least reusable         |

```html
<!-- External -->
<link rel="stylesheet" href="styles.css">

<!-- Internal -->
<style>
  p { color: navy; }
</style>

<!-- Inline -->
<p style="color: navy;">Hello</p>
```

### Anchor: The Selector Toolkit

| Selector                | Targets                                           | Example                  |
| ----------------------- | ------------------------------------------------- | ------------------------ |
| `*`                     | Universal — every element                         | `* { margin: 0; }`       |
| `p`                     | Element selector — every `<p>`                    | `p { color: red; }`      |
| `.note`                 | Class — every element with `class="note"`         | `.note { color: gray; }` |
| `#main`                 | ID — the **single** element with `id="main"`      | `#main { width: 80%; }`  |
| `article p`             | Descendant — every `<p>` inside an `<article>`    | `article p { ... }`      |
| `h1, h2`                | Group — applies to all listed selectors            | `h1, h2 { color: navy; }`|
| `a:link`                | Pseudo-class — unvisited link                     |                          |
| `a:visited`             | Already-visited link                              |                          |
| `a:hover`               | Mouse hovering over the link                      |                          |
| `a:active`              | Link being clicked                                |                          |

### Anchor: Class vs. ID — The Rule

- **Class (`.name`)** — used on **many** elements; one element can have multiple classes.
- **ID (`#name`)** — used on **exactly one** element per page; should be unique.

If you might style or select more than one element the same way, use a class. If it's a singular landmark like `#main-nav` or `#footer`, use an ID.

### Self-Check

> Which selector targets only `<p>` elements that are inside an `<article>`?
> A) `p, article`
> B) `article p`
> C) `article > .p`
> D) `#article p`

**Answer:** B. `article p` is the descendant selector.

> Which stylesheet type is best when you want one set of rules to apply across an entire multi-page website?
> A) Inline styles
> B) Internal stylesheet
> C) External stylesheet
> D) HTML comments

**Answer:** C.

---

## Module 10 — The Cascade, Specificity, and Inheritance

### Concept

This is the **single most-tested CSS topic** on the exam. Practice Exam 2 has multiple questions where you must read code with body styles, element selectors, classes, and inline styles — and predict the final color or font.

### Anchor: The Specificity Ladder

When two rules target the same element, the **more specific** one wins. From least to most specific:

```
                         ↑  most specific
   !important       — overrides almost everything
   Inline styles    — style="" on the element itself
   IDs              — #main
   Classes          — .note  (also pseudo-classes :hover, attribute selectors)
   Element selectors — p, h1, div
   Universal selector / inherited values  — *
                         ↓  least specific
```

If specificity ties, the **last rule declared wins** (this is the "cascade" part — order matters as a tie-breaker).

### Anchor: `!important` — Use Sparingly

```css
p { color: red !important; }
```

`!important` overrides normal specificity. It's a sledgehammer — overuse makes stylesheets unmaintainable, but the exam expects you to recognize what it does.

### Anchor: Inheritance — Which Properties Pass Down?

Some properties **inherit** from a parent to its children automatically; others don't.

| Inherits                                      | Does NOT inherit                                  |
| --------------------------------------------- | ------------------------------------------------- |
| `color`                                       | `margin`, `padding`, `border`                     |
| `font-family`, `font-size`, `font-weight`     | `width`, `height`                                 |
| `line-height`, `text-align`                   | `background` (background colors don't inherit)    |
| `visibility`                                  | `display`, `position`                             |

Rule of thumb: **text-related properties tend to inherit; box-related properties don't.**

### Anchor: Reading a Cascade Question

Given this code:

```html
<style>
  body { color: blue; }
  p    { color: green; }
  .note { color: orange; }
  #intro { color: purple; }
</style>

<p id="intro" class="note" style="color: red;">Hello</p>
```

What color is "Hello"?

Walk the ladder, top down: **inline `style="color: red;"` wins** over the ID, the class, the element selector, and the body. Answer: **red**.

If the inline style were removed, `#intro` (ID) would win → purple. Remove the ID, `.note` wins → orange. And so on.

### Self-Check

> Rank the following from highest to lowest specificity:
> A) Element selector, Class, ID, Inline style
> B) Inline style, ID, Class, Element selector
> C) ID, Inline style, Class, Element selector
> D) Class, Inline style, ID, Element selector

**Answer:** B.

> A `<p>` has a class `.note` (orange in the stylesheet) and `style="color: blue;"` inline. What color does it render?
> A) Orange — the class came first
> B) Black — they cancel out
> C) Blue — inline beats class
> D) Red — neither applies

**Answer:** C. Inline beats class on the specificity ladder.

---

## Module 11 — Colors, Backgrounds, the Box Model, and CSS Units

### Concept

This is a multi-topic module because the exam threads these concepts together — you can't size a box without knowing its units, and you can't pick a background without knowing how color works.

### Anchor: Hex Color Notation

```
#RRGGBB
  │ │ │
  │ │ └── Blue intensity   (00 = none, FF = max)
  │ └──── Green intensity
  └────── Red intensity

#000000  →  black
#FFFFFF  →  white
#FF0000  →  pure red
#00FF00  →  pure green
#0000FF  →  pure blue
```

A pair closer to `00` is darker for that channel; closer to `FF` is brighter. Named colors (`red`, `navy`, `tomato`) work too, but the exam expects fluency in hex.

### Anchor: Background Properties

```css
.hero {
  background-color: #112233;
  background-image: url("hero.jpg");
  background-repeat: no-repeat;       /* repeat | repeat-x | repeat-y | no-repeat */
  background-size: cover;             /* auto | cover | contain | fixed dims */
  background-position: center;
}
```

Common gotcha: **`opacity`** is the real CSS property for transparency. `transparency` is not a valid CSS property (it's an exam distractor).

### Anchor: The Box Model

Every element is a box composed of four concentric layers:

```
┌──────────────────── margin ────────────────────┐
│   ┌────────────── border ──────────────┐      │
│   │   ┌────────── padding ────────┐    │      │
│   │   │      content (width × height)  │      │
│   │   └─────────────────────────────┘   │      │
│   └─────────────────────────────────────┘      │
└────────────────────────────────────────────────┘
```

- **`width` / `height`** — the content area.
- **`padding`** — space *inside* the border, around the content.
- **`border`** — the box's edge.
- **`margin`** — space *outside* the border, between this box and others.

### Anchor: Margin / Padding Shorthand

```css
margin: 10px;                  /* all four sides              */
margin: 10px 20px;             /* top/bottom  |  left/right   */
margin: 10px 20px 30px;        /* top  |  left/right  |  bottom */
margin: 10px 20px 30px 40px;   /* top  |  right  |  bottom  |  left  (clockwise) */
margin: 0 auto;                /* horizontally center a block */
```

The same shorthand rules apply to `padding` and to `border-width`.

### Anchor: Border Properties and `border-radius`

```css
.card {
  border-style: solid;
  border-color: #333;
  border-width: 2px 1px 3px 1px;   /* top, right, bottom, left */
  border-radius: 8px;              /* rounded corners */
}
```

Or all at once with the shorthand: `border: 2px solid #333;`.

### Anchor: CSS Units — Relative vs. Absolute

| Type        | Units                              | Notes                                  |
| ----------- | ---------------------------------- | -------------------------------------- |
| **Relative** | `em`, `rem`, `%`, `vw`, `vh`      | Scale with font size or viewport       |
| **Absolute** | `px`, `pt`, `cm`, `in`, `mm`      | Fixed physical or device units         |

- `em` — relative to the parent element's font size.
- `rem` — relative to the **root** element's font size.
- `%` — relative to the parent.
- `vw` / `vh` — viewport width / height percentage.

**Accessibility tie-in:** relative units (especially `em` / `rem`) honor user zoom and font-size preferences. Absolute units like `px` and `pt` may not scale the same way for users who increase text size.

### Self-Check

> What does `margin: 10px 20px 30px 40px;` mean?
> A) All four sides are 10px
> B) Top 10, right 20, bottom 30, left 40 (clockwise from top)
> C) Top 10, left 20, bottom 30, right 40
> D) Top/bottom 10, left/right 20

**Answer:** B. Four-value shorthand goes top → right → bottom → left.

> Which CSS unit is **relative** and best supports users who rely on browser zoom or larger fonts?
> A) `px`
> B) `pt`
> C) `em`
> D) `cm`

**Answer:** C.

---

## Module 12 — Layout, Positioning, Responsive Design, and Accessibility

### Concept

This module covers how elements are arranged on the page, how to make designs adapt to different screen sizes, and how to make them work for everyone — including users on assistive tech.

### Anchor: `display` vs. `visibility` vs. `overflow`

| Property                       | Effect                                                              |
| ------------------------------ | ------------------------------------------------------------------- |
| `display: none`                | Removes the element entirely — no space reserved                    |
| `visibility: hidden`           | Hides the element but **keeps its space**                           |
| `visibility: collapse`         | Collapses table rows/columns (no effect on most other elements)     |
| `display: block`               | Block element — full width, breaks the line                         |
| `display: inline`              | Inline — flows in text, no line break                               |
| `display: inline-block`        | Flows like inline but accepts width/height                          |
| `overflow: visible`            | Default — content overflows past the box                            |
| `overflow: hidden`             | Clips content that overflows                                        |
| `overflow: scroll`             | **Always** shows scrollbars                                         |
| `overflow: auto`               | Shows scrollbars **only when needed**                               |

Common trap: a scrollbar only appears if the container has a fixed height (or width) that the content actually exceeds. `overflow: scroll` on a tall container with little content still shows scrollbars; `overflow: auto` does not.

### Anchor: Centering and Alignment

| Goal                                | Property                                   |
| ----------------------------------- | ------------------------------------------ |
| Center text inside an element       | `text-align: center;`                      |
| Center a block element horizontally | `margin: 0 auto;` (with a set width)       |
| Align flex children                 | `align-items` (cross-axis), `justify-content` (main axis) |
| Float content to one side           | `float: left;` / `float: right;`           |

### Anchor: Positioning

```css
.box { position: static;   }   /* default — normal flow */
.box { position: relative; }   /* offset from its NORMAL position */
.box { position: absolute; }   /* offset from nearest POSITIONED ancestor (or <body>) */
.box { position: fixed;    }   /* offset from the VIEWPORT — stays put on scroll */
```

The exam loves "what does this element use as its reference frame?" Memorize:

- **relative** → its own normal-flow location.
- **absolute** → the nearest ancestor that has any non-static position (else the document body).
- **fixed** → the browser viewport.

### Anchor: CSS Grid (Recognition Level)

```css
.layout {
  display: grid;
  grid-template-columns: 100px auto 100px;   /* fixed | flexible | fixed */
}
```

You don't need to be a Grid expert; you should recognize the syntax and know `auto` makes a column take whatever space is left.

### Anchor: Responsive Design — Three Required Pieces

1. **The viewport meta tag** — without it, mobile layouts break.

   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   ```

2. **Media queries** — apply different styles at different screen widths.

   ```css
   @media only screen and (max-width: 640px) {
     .sidebar { display: none; }
     body     { font-size: 14px; }
   }
   ```

3. **The `<picture>` element** — serves different images at different sizes (art direction).

   ```html
   <picture>
     <source media="(min-width: 640px)" srcset="hero-large.jpg">
     <source media="(min-width: 320px)" srcset="hero-medium.jpg">
     <img src="hero-small.jpg" alt="Hero image">
   </picture>
   ```

### Anchor: Accessibility Essentials

Beyond `alt` text on images, the exam tests:

- **Readable / well-known fonts** — avoid decorative fonts for body text.
- **Relative units** — `em` / `rem` honor user zoom; `px` / `pt` may not.
- **`tabindex` attribute** — controls keyboard tab order through links and form fields. `tabindex="0"` puts an element in the natural tab order; positive values force a custom order; `-1` removes it from tabbing.
- **`<label for="…">`** — pair every form input with a label.

### Anchor: Cross-Browser Compatibility

- **Vendor prefixes** — older or experimental properties may need a prefix:

  | Prefix      | Browser                    |
  | ----------- | -------------------------- |
  | `-webkit-`  | Safari, Chrome             |
  | `-moz-`     | Firefox                    |
  | `-ms-`      | Edge / Internet Explorer   |
  | `-o-`       | Opera                      |

- **CSS framework** — a multi-stylesheet library that ships with prebuilt components and a responsive grid (e.g., **Bootstrap**).
- **CSS template** — boilerplate starter code; less comprehensive than a framework.

### Self-Check

> Which property hides an element but **keeps the space it would have occupied**?
> A) `display: none`
> B) `visibility: hidden`
> C) `opacity: 0` only
> D) `overflow: hidden`

**Answer:** B. `display: none` removes it from layout entirely.

> An element has `position: fixed`. What is its reference frame?
> A) The element's normal flow position
> B) The nearest positioned ancestor
> C) The browser viewport
> D) The `<body>` element regardless of scroll

**Answer:** C. Fixed = pinned to the viewport, so it stays put when the page scrolls.

> Which tag, included in the `<head>`, is essential for responsive design on mobile devices?
> A) `<meta charset="UTF-8">`
> B) `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
> C) `<meta name="description" content="…">`
> D) `<link rel="stylesheet" href="responsive.css">`

**Answer:** B.

---

## Module 13 — Test-Taking Strategy and Final Review

### The Distractor-Autopsy Method

For every practice question, do this:

1. Pick your answer.
2. **For each *wrong* option, write one sentence explaining why it is wrong.**
3. Only then check the answer key.

If you can articulate why every distractor is wrong, you have actually mastered the concept. If you can't, that's where to study next.

### Strategies for the Question Formats

- **Single-answer multiple choice** — Eliminate the obvious wrong answers first. Two options usually look plausible; one of them has a small, specific flaw. Find it.
- **Multi-select "Choose 2/3"** — Read every option as an independent Yes/No question. Don't stop at the first two that look good.
- **Drag-and-drop matching** — Place the certain pairs first, then match the leftovers by elimination.
- **Drag-rank ordering (specificity!)** — Memorize the ladder cold. Write it out at the start of the exam if it helps.
- **Code-reading questions** — Walk the cascade ladder step by step; don't skim.

### Reading Code Under Time Pressure

When a code block appears, before reading the answer choices:

1. Identify the **kind of code** — HTML, CSS, or both.
2. Spot any **inline `style=""`**, IDs (`#`), classes (`.`), and `!important`.
3. Trace the **cascade** for each property the question is asking about.
4. Then evaluate each answer.

This 5-second habit prevents most code-reading mistakes.

### One Sentence to Repeat During the Exam

Pick one of these and repeat it under your breath whenever you get stuck:

- *"Inline beats ID beats class beats element."*
- *"Tags close in reverse order."*
- *"`<title>` lives in `<head>`; `<h1>` lives in `<body>`."*
- *"Class for many, ID for one."*
- *"`em` honors zoom; `px` doesn't."*
- *"`display: none` removes; `visibility: hidden` keeps space."*

### Mock Quiz (12 Questions Across the Whole Exam)

Try these timed — about 75 seconds per question.

1. Which placement is correct: `<title>` in `<head>` or in `<body>`?
2. Which is the correct HTML5 viewport meta tag?
3. A list of recipe steps in order — `<ul>`, `<ol>`, or `<dl>`?
4. Which entity displays a `<` character on the page?
5. From `/projects/index.html`, what's the relative path to `/styles/main.css`?
6. Which input type is correct for an age field with min 13 and max 120?
7. Which attribute, when present, makes a `<video>` element show play/pause UI?
8. Which element provides English subtitles inside a `<video>`?
9. Rank from highest to lowest specificity: Class, Inline style, Element selector, ID.
10. What does `margin: 10px 20px 30px 40px;` set, in order?
11. Which CSS unit best supports user zoom for accessibility — `px`, `pt`, `cm`, or `em`?
12. Which property hides an element while keeping its space — `display: none` or `visibility: hidden`?

#### Answer Key (cover until done)

1. **`<head>`** — Module 1.
2. **`<meta name="viewport" content="width=device-width, initial-scale=1.0">`** — Module 12.
3. **`<ol>`** — sequence matters. Module 4.
4. **`&lt;`** — Module 4.
5. **`../styles/main.css`** — go up one level, then into `/styles/`. Module 5.
6. **`<input type="number" min="13" max="120">`** — Module 6.
7. **`controls`** — Module 7.
8. **`<track kind="subtitles" src="…vtt" srclang="en">`** — Module 7.
9. **Inline style > ID > Class > Element selector** — Module 10.
10. **Top 10, right 20, bottom 30, left 40** (clockwise from top) — Module 11.
11. **`em`** (relative units honor zoom) — Module 11 / 12.
12. **`visibility: hidden`** keeps the space; `display: none` removes it — Module 12.

---

## Exam-Day Cheat Card

Read this on the morning of the exam. It's the whole guide compressed into a single paragraph:

> An HTML5 page starts with `<!DOCTYPE html>`, then `<html>` with `<head>` (metadata, `<title>`, `<meta>`, `<link>`, `<style>`, `<script>`) and `<body>` (visible content). Tags close in reverse order; void tags like `<br>`, `<hr>`, `<img>`, `<input>`, `<meta>`, `<link>` have no closing tag. The viewport meta tag is required for responsive mobile layouts; `<meta name="description">` and `name="keywords"` drive SEO. HTML comments use `<!-- -->`, CSS uses `/* */`, JavaScript uses `//` or `/* */`. Block elements (`<p>`, `<div>`, `<h1>`–`<h6>`) break the line; inline elements (`<span>`, `<a>`, `<img>`, `<br>`) don't. Ordered lists are `<ol>`, unordered are `<ul>`, description lists are `<dl>`; tables use `<table>`, `<tr>`, `<th>`, `<td>`, plus `colspan`/`rowspan`. Use entities like `&lt;`, `&gt;`, `&amp;`, `&copy;`, `&nbsp;` for reserved characters. Anchors need `href`; `target="_blank"` opens a new tab; `#id` jumps within the page. Images need `src` and `alt`; `..` means "go up one folder." Image maps use `<map>` and `<area>`. Forms: GET appends to URL (visible), POST is in the body (private). Pair `<label for="x">` with `<input id="x">`; `<input type="number" min max>`, `<input type="email">`, `required`, `<select>`/`<option>`, `<textarea rows cols maxlength>`, `<iframe src>`. Media: `<video>`/`<audio>` with multiple `<source>` children, the boolean `controls` attribute, fallback text inside, and `<track kind="subtitles" src=".vtt">` for captions. Semantic HTML5 — `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<figure>`/`<figcaption>`, `<footer>`, `<address>`, `<details>`/`<summary>` — beats `<div>` whenever a specific tag fits. CSS lives external (whole site), internal (one page), or inline (one element). Selectors: `*`, `p`, `.class`, `#id`, descendant `article p`, group `h1, h2`, link pseudo-classes `:link`/`:visited`/`:hover`/`:active`. Specificity: `!important` > inline > ID > class > element > universal; ties go to the last rule declared. Text properties (color, font) inherit; box properties (margin, width) don't. Hex `#RRGGBB`: closer to `00` darker, closer to `FF` brighter. `opacity` is the real transparency property. Box model: content → padding → border → margin; shorthand goes top, right, bottom, left clockwise. Relative units (`em`, `rem`, `%`, `vw`, `vh`) honor zoom; absolute (`px`, `pt`, `cm`) don't. `display: none` removes space; `visibility: hidden` keeps it. `overflow: scroll` always shows scrollbars; `auto` shows them only when needed. `position: relative` from itself, `absolute` from the nearest positioned ancestor, `fixed` from the viewport. `display: grid` with `grid-template-columns: 100px auto 100px` gives fixed-flexible-fixed columns. Media queries `@media only screen and (max-width: 640px)` adapt by viewport size; `<picture>` with `<source media>` swaps images. Vendor prefixes: `-webkit-`, `-moz-`, `-ms-`, `-o-`. Bootstrap is a CSS framework. `tabindex` controls keyboard order; `<label>` and `alt` are accessibility staples.

---

## Master Glossary

**Absolute Path / URL** — a full URL including protocol and domain (e.g., `https://example.com/img.png`).

**Accessibility** — designing pages so they work for users on assistive tech, keyboard navigation, and zoom/font-size preferences.

**`alt` Attribute** — fallback / accessibility text for an `<img>`.

**Anchor (`<a>`)** — element creating a hyperlink via the `href` attribute.

**Attribute** — a name/value pair on an HTML tag (e.g., `src="x.png"`).

**Block Element** — element that takes the full width and starts on a new line (e.g., `<p>`, `<div>`).

**Bootstrap** — a popular CSS framework providing prebuilt responsive components.

**Box Model** — the four layers of every element: content → padding → border → margin.

**Cascade** — the rule that the more specific style wins; ties go to the last-declared rule.

**Character Entity** — code that represents a reserved or special character (e.g., `&lt;` for `<`).

**Class Selector (`.name`)** — targets all elements with that class; can be applied to many elements.

**Comment (HTML)** — `<!-- … -->`. CSS uses `/* … */`. JavaScript uses `//` or `/* */`.

**CSS Framework** — multi-stylesheet library (e.g., Bootstrap).

**CSS Template** — boilerplate starter code, less comprehensive than a framework.

**Descendant Selector** — `article p` — every `<p>` inside an `<article>`.

**`display` Property** — controls how an element renders (`block`, `inline`, `inline-block`, `none`, `grid`, etc.).

**External Stylesheet** — a separate `.css` file linked from `<head>`; best for site-wide styles.

**Fragment Link** — `href="#id"` — jumps to an element with a matching `id` on the same page.

**GET / POST / PUT / DELETE** — HTTP methods. GET retrieves (URL params); POST submits (body); PUT updates; DELETE removes.

**Hex Color** — `#RRGGBB` notation; pairs encode red, green, and blue intensity.

**`href`** — destination of an anchor.

**ID Selector (`#name`)** — targets the **single** element with that ID; should be unique per page.

**Image Map** — `<map>` + `<area>` to make specific regions of an image clickable.

**`!important`** — overrides normal specificity; use sparingly.

**Inheritance** — text-related properties pass from parent to child; box properties generally do not.

**Inline Element** — element that flows within text without a line break (e.g., `<span>`, `<a>`).

**Inline Style** — `style=""` directly on an element; highest non-`!important` specificity.

**Internal / Embedded Stylesheet** — CSS inside `<style>` in the page's `<head>`.

**`<label for="x">`** — pairs with `<input id="x">` for accessible form labeling.

**Media Query** — `@media (max-width: 640px) { … }` — applies styles at certain viewport sizes.

**`<meta>` Tag** — head-level metadata (charset, description, keywords, viewport, robots).

**Pseudo-class** — `a:hover`, `a:visited`, etc. — styles based on element state.

**Relative Path / URL** — a path relative to the current file (e.g., `images/x.png`, `../styles/main.css`).

**Relative Units** — `em`, `rem`, `%`, `vw`, `vh` — scale with parent or viewport.

**Responsive Design** — adapting layout to screen size using viewport meta, media queries, and flexible images.

**Root Element** — `<html>`. `rem` is relative to the root font size.

**Selector** — the part of a CSS rule that targets elements.

**Self-Closing / Void Element** — element with no closing tag (`<br>`, `<hr>`, `<img>`, `<input>`, `<meta>`, `<link>`).

**Semantic HTML5** — tags that describe meaning, not appearance (`<header>`, `<nav>`, `<article>`, etc.).

**Specificity** — the system that decides which CSS rule wins: inline > ID > class > element.

**`tabindex`** — controls keyboard tab order for interactive elements.

**`target="_blank"`** — opens a link in a new tab/window.

**`<track>`** — provides captions or subtitles inside `<video>`, sourced from a `.vtt` file.

**Universal Selector (`*`)** — matches every element.

**Vendor Prefix** — `-webkit-`, `-moz-`, `-ms-`, `-o-` — browser-specific CSS extensions.

**Viewport Meta Tag** — `<meta name="viewport" content="width=device-width, initial-scale=1.0">` — required for responsive mobile rendering.

**`visibility` vs. `display`** — `visibility: hidden` keeps the element's space; `display: none` removes it from the layout.
