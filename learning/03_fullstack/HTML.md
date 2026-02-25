# HTML
# Documentation
### [#](https://exposureninja.com/blog/what-is-seo/) What is SEO?
- **SEO** -> (**S**earch **E**ngine **O**ptimization) 
- الهدف الأساسي: جعل موقعك يظهر في **النتائج الأولى** في جوجل (أو غيره من محركات البحث) **بدون دفع إعلانات** (أي الظهور في النتائج العضوية / المجانية Organic Results)
- Started evolving in the late 1990s with search engines → today it’s one of the most important parts of digital marketing  
> **Almost every serious website** needs SEO to attract real visitors!
- SEO helps search engines **understand** your page’s content and decide **how useful** it is to searchers  
- Modern websites usually combine three big pieces that interact with SEO:
	- **HTML** — provides structure + semantic meaning
	- **High-quality content** — matches what people are actually searching for (search intent)
	- **CSS + JavaScript + speed + backlinks** — improves technical performance and user experience

---
### [#](https://www.semrush.com/blog/markup-language/) What are Markup Languages?
- **لغة الـ Markup** (Markup Language) هي نظام لـ **توصيف** النصوص والمحتوى باستخدام **علامات** (tags) خاصة
- لا تُعتبر لغة برمجة حقيقية (لا تحتوي على منطق أو حسابات معقدة) بل هي طريقة لإخبار الحاسوب/المتصفح: "هذا نص عادي، هذا عنوان، هذه صورة، هذا رابط..."
- Most famous example: **HTML** (HyperText Markup Language)  
- Other popular markup languages:
	- **XML** — used for storing & transporting structured data
	- **Markdown** — very easy way to format text (used on GitHub, Reddit, Notion…)
	- **BBCode** — old-school forum markup
- **Core idea:**  
	Content + tags = document that both humans and machines can understand

---

## [#](https://info.cern.ch/hypertext/WWW/TheProject.html) First HTML File
### [#](https://developer.mozilla.org/en-US/docs/Glossary/Tag) Tags and Attributes
- The smallest building blocks in HTML are **elements**
Most elements follow this pattern:
```html
<opening-tag>Content goes here</opening-tag>
```
- **Tag** = the part inside `< >`  
	- `<p>` → opening tag  
	- `</p>` → closing tag

- **Attribute** = extra information you add **inside** the opening tag only  
	Always written as: `name="value"`

Common examples:
```html
<a href="https://google.com">Go to Google</a>
<!-- href is the attribute -->

<img src="cat.jpg" alt="Cute cat photo">
<!-- src and alt are attributes -->

<div class="container" id="main-content">
  Content here
</div>
<!-- class and id are attributes -->
```

- Attributes only go in the **opening tag** — never in the closing tag, They either **add information** or **change behavior** of the element

---
### [#](https://developer.mozilla.org/en-US/docs/Glossary/Entity) HTML Entities
- Some characters are **reserved** in HTML (< > & " ')  
	If you write them directly, the browser thinks they are part of HTML code → error!

- **Solution:** Use **HTML Entities** (special escape codes)
	They always start with `&` and end with `;`

Most common ones:

| Character you want | Named Entity | Numeric Entity | Result        |
| ------------------ | ------------ | -------------- | ------------- |
| <                  | `&lt;`       | `&#60;`        | <             |
| >                  | `&gt;`       | `&#62;`        | >             |
| &                  | `&amp;`      | `&#38;`        | &             |
| "                  | `&quot;`     | `&#34;`        | "             |
| '                  | `&apos;`     | `&#39;`        | '             |
| Non-breaking space | `&nbsp;`     | `&#160;`       | (fixed space) |
| ©                  | `&copy;`     | `&#169;`       | ©             |
| ®                  | `&reg;`      | `&#174;`       | ®             |

Practical example:
```html
<p>5 &gt; 3 is true</p>
<p>Copyright &copy; 2026 Potato Inc.</p>
```

---
### [#](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Comments) HTML Comments
- Comments let you write **notes** inside your code  
	→ The browser **completely ignores** them and they never appear on the page

Syntax:
```html
<!-- This is a comment and won't show up -->
```

Real-world examples:
```html
<!-- Start of header section -->
<header>
  <h1>Welcome to the site</h1>
</header>

<!-- 
  Temporarily disabled analytics
  <script src="analytics.js"></script>
-->

<!-- TODO: Add hero image later -->
```

**Why use comments?**
- Explain code to yourself or teammates
- Temporarily disable parts of code without deleting
- Track changes during development

---
### [#](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Text/Whitespace) Whitespace in HTML
- **Whitespace** = spaces + tabs + line breaks

- **Default HTML behavior:**
	- Multiple consecutive spaces → collapsed into **one single space**
	- Line breaks → usually treated as a space (in normal flow)

Examples:
```html
<p>    Hello     World    </p>
<!-- Displays: Hello World -->

<p>
  Hello
  World
</p>
<!-- Displays: Hello World -->
```

**How to keep extra spaces or line breaks?**

1. Use `&nbsp;` (non-breaking space)
```html
<p>Hello&nbsp;&nbsp;&nbsp;World</p>
<!-- Displays: Hello   World -->
```

2. Use the `<pre>` element (preformatted text)
```html
<pre>
  Hello
     World
</pre>
<!-- Keeps all spaces and new lines exactly as written -->
```

3. Control it better with CSS (you’ll learn this later)
```css
white-space: pre;     /* preserves everything */
white-space: nowrap;  /* prevents line wrapping */
```
---
## [#](https://www.tutorialspoint.com/html/html_basic_tags.htm) Basic Tags
### [#](https://developer.mozilla.org/en-US/docs/Glossary/Doctype) `<!DOCTYPE html>`

- The **very first line** of every modern HTML file.
- Tells the browser:  
	- "This is an **HTML5** document"  
	- "Use **standards mode** (not old quirks mode)"

- Super short in HTML5 (only version you need today):  
  ```html
  <!DOCTYPE html>
  ```

- Important rules:  
	- Must be **line 1** — no spaces, no comments, nothing before it  
	- Case-insensitive (`<!doctype html>` works too)  
	- Without it → browser may render page incorrectly (broken layouts, weird spacing)
- Old versions (HTML4 / XHTML) had very long doctypes — ignore them completely now

**Quick tip:**  
Always start your file like this — no exceptions:

```html
<!DOCTYPE html>
<html lang="en">
```

---
### [#](https://www.w3schools.com/tags/tag_html.asp) The `<html>` Element

- The **root** container of the entire document  
- Everything else lives **inside** it

Basic structure:
```html
<!DOCTYPE html>
<html lang="en">
  <head>...</head>
  <body>...</body>
</html>
```

Key points:
- Only **one** `<html>` per page  
- Almost always include the `lang` attribute:  
	- `lang="en"` → English  
	- `lang="ar"` → Arabic  
	- `lang="fr"` → French  
-  Helps: screen readers, search engines, spell checkers, translations
---
### [#](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/head) The `<head>` Element

- Contains **metadata** (information **about** the page)  
- **Nothing** inside `<head>` is visible on the actual webpage

Typical location:
```html
<head>
  <!-- Metadata, title, links to CSS/JS, etc. go here -->
</head>
```

Common children inside `<head>`:
- `<title>` ............... page title (browser tab + search results)
- `<meta>` tags ..... charset, viewport, description...
- `<link>` ............... external CSS files, icons
- `<script>` ............ JavaScript (often placed here or at end of body)
- `<style>` ............. internal CSS rules
- favicon links, social sharing tags (Open Graph), etc.

**Core idea:**  
`<head>` = behind-the-scenes info for browsers • search engines • devices

---
### [#](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta) `<meta>` Tags

- Provide **metadata** about the document  
- Always live inside `<head>`  
- Self-closing (no `</meta>` needed in HTML5)

Most important ones every beginner should know:

- **Charset** (prevents garbled text)  
  ```html
  <meta charset="UTF-8">
  ```
  → Usually the **very first** `<meta>` tag

- **Viewport** (makes your site work nicely on phones/tablets)  
  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  ```
  → Essential for responsive / mobile-friendly design

- **Description** (controls snippet in Google search results)  
  ```html
  <meta name="description" content="Learn HTML the fun and easy way with clear examples.">
  ```

- **Other useful ones** (optional at first):
  ```html
  <meta name="author" content="Potato">
  <meta name="robots" content="index, follow">
  ```

Minimal modern `<head>` most people start with:
```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Awesome Page</title>
</head>
```

---
### [#](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/body) The `<body>` Element

- Where all **visible content** goes  
- This is what users actually **see** and interact with

Rules:
- Only **one** `<body>` per HTML document  
- Comes **after** `<head>`

Typical content inside `<body>`:
- Headings: `<h1>`, `<h2>`, ..., `<h6>`
- Paragraphs: `<p>`  
- Images: `<img>`  
- Links: `<a>`  
- Lists: `<ul>`, `<ol>`, `<li>`  
- Divisions/sections: `<div>`, `<section>`, `<article>`  
- Forms, buttons, videos, etc.

Simple example:
```html
<body>
  <h1>Hello, World!</h1>
  <p>Welcome to my first website.</p>
  <img src="sunset.jpg" alt="Beautiful sunset over the sea">
</body>
```

**Complete minimal HTML5 skeleton** (the foundation of every page):
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My First Web Page</title>
</head>
<body>
  <h1>Hi there!</h1>
  <p>I'm learning HTML — let's build something cool!</p>
</body>
</html>
```
---
## [#](https://roadmap.sh/ai/guide/html-textual-tags-a-concise-guide-1771995072862) Textual Tags
Quick overview of the most common tags used inside `<body>` for text and simple formatting.

### **Headings** 
— define importance and structure  
`<h1>` to `<h6>` (h1 = biggest/most important, h6 = smallest)  
  ```html
  <h1>Main Title</h1>
  <h2>Section</h2>
  <h3>Subsection</h3>
  ```
---
### **Page Title** 
(goes in `<head>`, shows in browser tab)  
  ```html
  <title>My Cool Website</title>
  ```
---
### **Paragraph** 
— normal blocks of text  
  ```html
  <p>This is a paragraph of content.</p>
  ```
---
### **Horizontal Rule** 
— thematic break / line  
  ```html
  <hr>
  ```
---
### **Line Break** 
— force a new line (without new paragraph)  
  ```html
  First line<br>Second line
  ```
---
### **Bold / Strong emphasis**  
  `<b>` → visual bold only  
  `<strong>` → bold + semantic importance (better for accessibility/SEO)  
  ```html
  This is <strong>very important</strong> text.
  ```
---
### **Preformatted Text**
— keeps spaces, tabs, and line breaks exactly as written  
  ```html
  <pre>
  Hello   World
      indented
  </pre>
  ```
---
### **Italic / Emphasized**  
  `<i>` → visual italic only  
  `<em>` → italic + semantic emphasis (screen readers stress it)  
  ```html
  This is <em>really cool</em>!
  ```
---
### **Highlight / Mark** 
— yellow background (like a marker)  
  ```html
  Search for <mark>HTML</mark> here.
  ```
---
### **Superscript & Subscript**
— for exponents, footnotes, chemistry...  
  ```html
  H<sub>2</sub>O   → H₂O  
  x<sup>2</sup>       → x²
  ```
---
### **Links** 
— the most important tag for navigation  
  ```html
  <a href="https://example.com">Visit Example</a>

  <!-- Open in new tab -->
  <a href="https://google.com" target="_blank">Google (new tab)</a>

  <!-- Link to email -->
  <a href="mailto:hello@site.com">Email me</a>
  ```

**Quick best-practice reminders:**
- Use `<strong>` and `<em>` over `<b>` and `<i>` when the text has meaning  
- Headings should be used in order (don't jump from h1 to h3)  
---
## [#](_blank) Grouping text

These are the two most common **container** tags in HTML.  
They don’t add any meaning or style by themselves — they exist purely to **group** content so you can style or manipulate it later (especially with CSS).

---
### [#](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/div) **`<div>`** — **block-level** container  
  • Takes full available width  
  • Starts on a new line  
  • Creates visible “boxes” or sections  
  • Most used tag for page layout structure

```html
<div>
  <h2>About Me</h2>
  <p>I love building websites.</p>
</div>

<div class="card">
  <img src="photo.jpg" alt="Profile">
  <h3>John Doe</h3>
  <p>Web Developer</p>
</div>
```

Common uses:
- Sections of a page  
- Cards, containers, wrappers  
- Grid/flexbox items  
- Adding background colors, borders, padding, margins
---
### [#](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/span) **`<span>`** — **inline** container  
  • Does **not** start a new line  
  • Only takes as much width as its content needs  
  • Perfect for styling small pieces of text inside a paragraph

```html
<p>
  This is normal text, but <span style="color: red;">this part</span> 
  is red and <span class="highlight">this is highlighted</span>.
</p>

<p>Price: $99 <span class="discount">(-20% off!)</span></p>
```

Common uses:
- Changing color, font, size of a few words  
- Adding icons or badges inside text  
- Tooltips or hover effects on small parts  
- Inline layout tweaks

## [#](https://roadmap.sh/ai/guide/search?term=HTML%20attributes&src=topic) Standard attributes
These are the most commonly used **global attributes** — they can be added to **almost any HTML element**.

They go inside the **opening tag** only.

### **id** — unique identifier for a single element  
- Must be **unique** on the entire page  
-  Used for:  
	- Linking to specific sections (`#section-id`)  
	- JavaScript targeting  
	- CSS (though `class` is preferred for styling)

```html
<h1 id="main-title">Welcome</h1>
<a href="#main-title">Jump to title</a>

<div id="contact-form">...</div>
```
---
### **class** — groups elements for styling or behavior  
• One element can have **multiple classes** (space-separated)  
• Same class can be used on **many** elements  
• Main tool for CSS targeting

```html
<p class="intro">This is an intro paragraph.</p>
<button class="btn btn-primary">Click me</button>

<div class="card featured sale">Special offer!</div>
```
---
### **data-* attributes** (custom data attributes)  
  • Start with `data-` followed by your own name (lowercase, use hyphens)  
  • Store extra information for JavaScript or CSS  
  • Very useful in modern web apps

```html
<button data-product-id="123" data-price="49.99">Add to Cart</button>

<div data-user-role="admin" class="user-profile">...</div>

<!-- Example: used by JS later -->
<img data-src="high-res.jpg" src="low-res.jpg" alt="Lazy loaded image">
```
---
### **style** — inline CSS (applies styles directly to this element)  
  • Quick for testing or one-off styles  
  • **Not recommended** for large projects (hard to maintain)  
  • Use external CSS + classes instead whenever possible

```html
<p style="color: navy; font-size: 1.2rem;">Styled paragraph</p>

<div style="background: #f0f0f0; padding: 20px; border-radius: 8px;">
  Quick card
</div>

<h2 style="text-align: center; color: #e74c3c;">Centered Red Title</h2>
```
---
## [#](https://www.w3schools.com/html/html_lists.asp) Lists and Types

Lists are a great way to manage time, figure out what needs to be done, and remember things. And it feels good when we check items off!

### `<ul>` Unordered lists
For **unordered lists**, also known as bullet points, start with the `<ul>` tag and wrap each item in a `<li>` list item element. Like so:

```html
<ul>
  <li>🧺 Go to laundromat.</li>
  <li>🖥 Code for 45 min.</li>
  <li>💅 Take a bubble bath.</li>
</ul>
```

The `<ul>` is great for listing things in any order. But what if we wanted to number the list?

---
### `<ol>` Ordered lists
For **ordered lists**, also known as numbered lists, we use the `<ol>` element:

```html
<ol>
  <li>🧺 Go to laundromat.</li>
  <li>🖥 Code for 45 min.</li>
  <li>💅 Take a bubble bath.</li>
</ol>
```

---
### **`<dl>`** Definition Lists

  Used for **term + description** pairs (like a glossary, FAQ, dictionary, or metadata)  
  • `<dt>` = definition term (the word or phrase)  
  • `<dd>` = definition / description (the explanation)

```html
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language — the skeleton of web pages</dd>

  <dt>CSS</dt>
  <dd>Cascading Style Sheets — controls appearance and layout</dd>

  <dt>JavaScript</dt>
  <dd>Makes pages interactive and dynamic</dd>
</dl>
```

Multiple descriptions for one term:
```html
<dt>padding</dt>
<dd>Space inside the border</dd>
<dd>Affects the background color</dd>
<dd>Does not move the element itself</dd>
```

---
### **Nested Lists** — Putting lists inside lists  
  You can place any list type (`<ul>`, `<ol>`, `<dl>`) inside an `<li>` or `<dd>`  
  • Browsers automatically indent nested levels  
  • Great for outlines, sub-menus, steps with details, categories & sub-categories

**Simple nested unordered example**
```html
<ul>
  <li>Frontend Development
    <ul>
      <li>HTML — structure</li>
      <li>CSS — styling</li>
      <li>JavaScript — interactivity</li>
    </ul>
  </li>
  <li>Backend Development
    <ul>
      <li>Node.js</li>
      <li>Python (Django / Flask)</li>
      <li>Ruby on Rails</li>
    </ul>
  </li>
</ul>
```

**Mixed nesting (ordered + definition)**
```html
<ol>
  <li>Learn the fundamentals
    <ul>
      <li>Tags and elements</li>
      <li>Attributes</li>
      <li>Lists (this section!)</li>
    </ul>
  </li>
  <li>Build small projects
    <dl>
      <dt>Project 1</dt>
      <dd>Personal landing page</dd>
      <dt>Project 2</dt>
      <dd>Interactive to-do list</dd>
    </dl>
  </li>
</ol>
```

**Quick best-practice notes**
- Use `<dl>` only when you truly have **term → explanation** relationships  
- Nesting is very common in real websites (especially menus, sitemaps, FAQs)  
- Don't nest too deeply (3–4 levels max is usually readable)  
- You can mix list types freely — `<ol>` inside `<ul>`, `<dl>` inside `<ol>`, etc.

**Real-world mini example**
```html
<h3>Web Development Basics – Quick Glossary</h3>
<dl>
  <dt>Semantic HTML</dt>
  <dd>Using meaningful tags like <code>&lt;header&gt;</code>, <code>&lt;article&gt;</code> instead of only <code>&lt;div&gt;</code></dd>
  
  <dt>Responsive Design</dt>
  <dd>Making websites adapt to different screen sizes</dd>
    <dd>Usually achieved with CSS media queries + viewport meta tag</dd>
</dl>

<h3>Learning Roadmap</h3>
<ol>
  <li>HTML
    <ul>
      <li>Text formatting</li>
      <li>Lists (all types)</li>
      <li>Links & images</li>
    </ul>
  </li>
  <li>CSS basics</li>
  <li>JavaScript fundamentals</li>
</ol>
```
---
## [#](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/table) Table Tag

Tables organize data in rows and columns — great for schedules, pricing, comparisons, scores, etc.

- Basic structure:  
	- `<table>` → the container  
	- `<tr>` → table row  
	- `<th>` → table header cell (bold & centered by default)  
	- `<td>` → table data cell

```html
<table>
  <tr>
    <th>Name</th>
    <th>Age</th>
    <th>City</th>
  </tr>
  <tr>
    <td>Alice</td>
    <td>28</td>
    <td>Cairo</td>
  </tr>
  <tr>
    <td>Bob</td>
    <td>34</td>
    <td>Alexandria</td>
  </tr>
</table>
```

- Useful additions:  
	- `scope="col"` or `scope="row"` on `<th>` → improves accessibility  
	- `colspan` / `rowspan` → merge cells
```html
<td colspan="2">Spans two columns</td>
<th rowspan="3">Spans three rows</th>
```

**Quick tips**  
- Use tables for **tabular data only** — not for layout (use CSS Grid/Flexbox instead)  
- Add `<thead>`, `<tbody>`, `<tfoot>` for better semantics & styling  
- Style with CSS (borders, padding, zebra stripes)

```html
<table>
  <thead>
    <tr><th>Item</th><th>Price</th></tr>
  </thead>
  <tbody>
    <tr><td>Apple</td><td>$1</td></tr>
    <!-- more rows -->
  </tbody>
</table>
```

---
## [#](https://learn.shayhowe.com/html-css/adding-media/) Embedding Media

HTML makes it easy to add images, audio, video, and external content.
### **Images** (`<img>`)
  Essential attributes: `src` (source), `alt` (accessibility + fallback)

```html
<img src="photo.jpg" alt="Sunset over the Nile in Cairo" width="600" height="400">

<!-- Responsive image with srcset -->
<img src="small.jpg" 
     srcset="medium.jpg 768w, large.jpg 1200w" 
     sizes="(max-width: 600px) 100vw, 50vw"
     alt="Responsive example">
```
---
### **Audio** (`<audio>`) 
— embed sound files  
	Include multiple `<source>` for format support (MP3, OGG, WAV)

```html
<audio controls>
  <source src="podcast.mp3" type="audio/mpeg">
  <source src="podcast.ogg" type="audio/ogg">
  Your browser does not support the audio element.
</audio>
```
---
### **Video** (`<video>`) 
— embed video files  
	Similar to audio + poster image, controls, autoplay, loop

```html
<video controls width="640" height="360" poster="thumbnail.jpg">
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.webm" type="video/webm">
  <track src="subtitles.vtt" kind="subtitles" srclang="en" label="English">
  Video not supported.
</video>
```

Best practices:  
- Provide multiple formats  
- Add `preload="metadata"` for faster page load  
- Use `playsinline` for mobile autoplay
---
### **Iframe** (`<iframe>`) 
— embed external pages/content (YouTube, maps, etc.)  
	Most common for third-party embeds

```html
<!-- YouTube video -->
<iframe width="560" height="315" 
        src="https://www.youtube.com/embed/dQw4w9WgXcQ" 
        title="YouTube video player" 
        frameborder="0" 
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
        allowfullscreen></iframe>

<!-- Google Map -->
<iframe src="https://www.google.com/maps/embed?pb=..." width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy"></iframe>
```
Key attributes: `title` (accessibility), `loading="lazy"`, `allowfullscreen`

---
### **CSP (Content Security Policy)** 
— security for embeds  
	CSP is an HTTP header (or `<meta>` tag) that controls what resources can load — helps prevent XSS attacks.

Common directives for media:
- `img-src` → controls images  
- `media-src` → audio/video sources  
- `frame-src` / `child-src` → iframes  
- `default-src` → fallback for everything

Example CSP (via `<meta>` tag):
```html
<meta http-equiv="Content-Security-Policy" content="
  default-src 'self';
  img-src 'self' https://images.example.com;
  media-src 'self' https://cdn.example.com;
  frame-src 'self' https://www.youtube.com https://maps.google.com;
">
```
---
## [#](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/form) Using Forms

Forms collect user input — search, login, contact, upload, etc.

- **`<form>`** — container  
  Key attributes: `action` (where to send), `method` ("get" or "post")

```html
<form action="/submit" method="post">
  <!-- inputs here -->
</form>
```

### **Labels and Inputs**  
  Always associate with `<label for="id">` for accessibility

```html
<label for="name">Name:</label>
<input type="text" id="name" name="name" required placeholder="Your name">
```

Common input types: `text`, `email`, `password`, `number`, `checkbox`, `radio`, `date`, `submit`

---
### **File Uploads** (`<input type="file">`)  
  Use `accept` to limit types, `multiple` for many files

```html
<label for="resume">Upload resume:</label>
<input type="file" id="resume" name="resume" accept=".pdf,.docx" required>
```

---
### **Form Validation**  
  Browser built-in: `required`, `pattern`, `minlength`, `type="email"`...

```html
<input type="email" required placeholder="email@example.com">
<input type="url" pattern="https?://.+">
```

Custom JS validation possible, but start with HTML.

- **Limitations**  
	- Client-side only (not secure) — always validate on server  
	- File size/type limits need server check  
	- Accessibility: use labels, `aria-describedby` for errors
---
**Tiny example**
```html
<form action="/contact" method="post">
  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required>

  <label for="message">Message:</label>
  <textarea id="message" name="message" rows="5"></textarea>

  <button type="submit">Send</button>
</form>
```
---
## [#](https://www.w3schools.com/html/html5_semantic_elements.asp) Semantic Markup
HTML5 semantic elements define page **regions** — better for accessibility, SEO, and maintainability than plain `<div>`.

### Highlighting Changes

These semantic tags show **edits** or **marked** text — useful for version history, reviews, or legal docs.

- **`<del>`** — deleted / struck-through text  
  • Shows removed content (strikethrough by default)

```html
<p>The meeting is on <del>Friday</del> Monday at 10 AM.</p>
```

- **`<ins>`** — inserted / underlined text  
  • Shows added content (underline by default)

```html
<p>The price is now $<ins>29</ins> <del>49</del>.</p>
```

- **`<s>`** — no longer accurate / irrelevant text  
  • Strikethrough without implying "deleted" (e.g., old prices, corrections)

```html
<p>Original price: <s>$99</s> Now only $59!</p>
```

- **`<mark>`** — highlighted / important text  
  • Yellow background by default — great for search results or emphasis

```html
<p>Search found: The <mark>HTML</mark> tutorial is here.</p>
```

**Quick tips**  
- Add `cite="url"` and `datetime="YYYY-MM-DD"` for traceability  
- Use these for meaning — not just visual effects (CSS can override styles)

```html
<p>Price changed on <time datetime="2026-02-20">Feb 20, 2026</time>:
  <del cite="changelog.html">Old</del> → <ins>New</ins></p>
```
---
### Layout Tags
1. **`<header>`** — introductory content / branding (logo, title, nav)  
  Usually at top of page or section

```html
<header>
  <h1>Potato's Site</h1>
  <nav>...</nav>
</header>
```

2. **`<nav>`** — major navigation links  
  (menu, sidebar links, pagination)

```html
<nav>
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/about">About</a></li>
  </ul>
</nav>
```

3. **`<main>`** — primary content (only one per page)

```html
<main>
  <h1>Main Article</h1>
  <p>...</p>
</main>
```

4. **`<section>`** — thematic grouping of content

```html
<section>
  <h2>Chapter 1</h2>
  <p>...</p>
</section>
```

5. **`<article>`** — self-contained content (blog post, news, comment)

```html
<article>
  <h2>Post Title</h2>
  <p>Content...</p>
</article>
```

6. **`<aside>`** — sidebar / related content (ads, quotes, links)

```html
<aside>
  <h3>Quick Links</h3>
  <ul>...</ul>
</aside>
```

7. **`<footer>`** — footer content (copyright, author, links)

```html
<footer>
  <p>&copy; 2026 Potato — Cairo, EG</p>
</footer>
```

**Quick skeleton example**
```html
<body>
  <header>...</header>
  <nav>...</nav>
  <main>
    <article>...</article>
    <aside>...</aside>
  </main>
  <footer>...</footer>
</body>
```
---
### Quotation / Citation Tags

These tags mark **quoted** or **referenced** content semantically.

1. **`<blockquote>`** — long block quotation  
	- Usually indented

```html
<blockquote cite="https://example.com/source">
  <p>This is a longer quote from another source.</p>
</blockquote>
```

2. **`<q>`** — short inline quotation  
	- Browser adds quotes automatically
```html
<p>She said <q>HTML is fun!</q> and kept coding.</p>
```

3. **`<cite>`** — title of a creative work  
	- Italic by default — use for book/movie/article titles

```html
<p>Read more in <cite>The Web Book</cite> by Potato.</p>
```

4. **`<abbr>`** — abbreviation with tooltip  
	- `title` shows full form on hover

```html
<p><abbr title="HyperText Markup Language">HTML</abbr> is awesome.</p>
```

5. **`<dfn>`** — defining instance of a term  
	- Marks the place where a term is defined

```html
<p>The <dfn>semantic web</dfn> uses meaningful tags.</p>
```

6. **`<address>`** — contact info for author/owner  
	- Italic by default — often in footer

```html
<address>
  Contact: Potato<br>
  Cairo, EG<br>
  <a href="mailto:potato@example.com">Email</a>
</address>
```
---
**Why semantic?**  
- Screen readers jump between regions  
- Search engines understand structure better  
- Cleaner code, easier CSS/JS targeting
---
## [#](https://www.freecodecamp.org/news/html-and-css-inline-style-external-stylesheet-css-code-examples/) Styling Basics
HTML structures content — CSS adds look. Three ways to include styles.

- **Inline CSS** (`style` attribute) — quick tests, overrides

```html
<p style="color: navy; font-size: 1.2rem;">Inline style</p>
```
---
- **Internal CSS** (`<style>` in `<head>`) — page-specific

```html
<head>
  <style>
    body { background: #f8f9fa; }
    h1 { color: #2c3e50; }
  </style>
</head>
```
---
- **External CSS** (`<link>` — best for most sites)  
  Reusable, cacheable, clean separation

```html
<head>
  <link rel="stylesheet" href="styles.css">
</head>
```
---
## [#](https://developer.mozilla.org/en-US/docs/Web/HTML/How_to/Add_JavaScript_to_your_web_page) Including JavaScript
Three main ways to add JavaScript to an HTML page — each has its use cases.

- **External Script** (`<script src="...">`) — best for most real projects  
	- Loads a separate `.js` file  
	- Reusable across pages, cacheable by browser, clean separation  
	- Place at end of `<body>` (or use `defer`/`async` attributes)

```html
<!-- Recommended placement: just before </body> -->
<script src="path/to/my/script.js" defer></script>
```
---
- **Internal Script** (`<script>` tag with code inside) — page-specific or small scripts  
	- Code lives directly in the HTML file  
	- Good for quick tests, one-page apps, or dynamic content generation  
	- Can go in `<head>` (with `defer`) or at end of `<body>`

```html
<script>
  console.log("Hello from internal script!");
  // more code here
</script>
```
---
- **Inline Script** (event attributes like `onclick`, `onchange`, etc.) — very quick / one-off actions  
	  - JavaScript code directly in an HTML attribute (no `<script>` tag needed)  
	  - Useful for tiny behaviors, prototyping, or old-school code  
	  - **Not recommended** for larger logic (hard to read/maintain/debug)

```html
<button onclick="alert('Clicked!')">Click me</button>

<input type="text" oninput="console.log(this.value)">
```

**Quick comparison**

| Method              | Location                          | Best For                          | Pros                              | Cons                              |
|---------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|
| External            | `<script src="...">`             | Most production sites             | Cacheable, reusable, organized    | Extra HTTP request                |
| Internal            | `<script> ...code... </script>`  | Page-specific or small JS         | No extra request, easy to see     | Bloats HTML, not reusable         |
| Inline (attributes) | `onclick="js code"`              | Very simple interactions          | Super fast to write               | Messy, hard to maintain, no separation |

**Modern best practices**
- Prefer **external** files with `defer` (or `async` when appropriate)  
- Avoid heavy inline/event-handler code — move logic to functions in external/internal scripts  
- Example recommended pattern:

```html
<!-- At the end of <body> -->
<script src="main.js" defer></script>

<!-- Or internal fallback -->
<script>
  // Quick debug or polyfill
  console.log("Page loaded!");
</script>
```
---
## [#](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Accessibility/HTML) Accesibility

Make sites usable by everyone — including screen readers, keyboard users, low vision.

Key practices:
- Use **semantic HTML** (headings, landmarks like `<main>`, `<nav>`)  
- Proper labels & associations (`<label for="id">`)  
- Alt text on images  
- Keyboard focus (no `tabindex` hacks unless needed)  
- ARIA only when HTML isn't enough  
- Color contrast ≥ 4.5:1  
- Meaningful link text (not "click here")

Semantic → built-in accessibility (e.g., `<button>` focusable by default)

**Quick win checklist**
- Run Lighthouse accessibility audit  
- Test with screen reader (VoiceOver, NVDA)  
- Navigate with keyboard only
## [#](https://developers.google.com/search/docs/fundamentals/seo-starter-guide) Basics of SEO

### SEO
**Search Engine Optimization** — تحسين محركات البحث  
- يخلي موقعك يظهر في النتائج الأولى (مجانًا، بدون إعلانات)  
- يساعد جوجل يفهم محتواك بشكل صح  
- يخلي المستخدم يلاقي موقعك بسهولة وسرعة  
أهم محرك بحث في العالم: **جوجل** (حوالي 90% من البحث)

### البحث بيشتغل إزاي  
- جوجل بيبعت **Crawlers** (روبوتات) تزحف على الإنترنت وتجمع الصفحات  
- معظم المواقع بتتفهرس **تلقائيًا** بعد النشر  
- مجرد نشر الموقع → كفاية كبداية (لكن مش كفاية عشان تطلع في الأول)

### النتائج بتظهر إمتى؟  
- ممكن ساعات أو أيام (للمواقع الجديدة)  
- غالبًا أسابيع أو شهور عشان تشوف تحسن حقيقي  
- مش كل تعديل بيأثر فورًا → استنى وتابع  
- الصبر مهم جدًا في SEO

### إزاي جوجل يلاقي ويفهم موقعك  
- تأكد إن موقعك مفهرس: ابحث في جوجل عن  
  `site:yourwebsite.com`  
- الروابط الخارجية (backlinks) من مواقع موثوقة → أقوى طريقة للاكتشاف  
- **Sitemap.xml** مفيد (يساعد الروبوتات) لكنه مش إجباري  
- استخدم **Google Search Console** عشان تتأكد إن الصفحات متاحة ومفهرسة صح  

#### تنظيم الموقع (Site Architecture)  
- هيكل بسيط وواضح → أفضل لجوجل والمستخدم  
- URLs مفهومة وقصيرة (مثال: `/html-tutorial` بدل `/page?id=123`)  
- صفحات متشابهة في مجلدات واحدة (folders)  
- تجنب المحتوى المكرر (duplicate content):  
	- حلول: **301 redirect** أو **rel="canonical"** tag

#### المحتوى
- اكتب محتوى **فريد**، **مفيد**، **سهل القراءة**، **محدث**  
- ركز على search intent : إيه اللي الناس عايزاه فعلاً؟  
- اكتب طبيعي — **بلاش حشو كلمات** (keyword stuffing)  
- مفيش عدد كلمات سحري (جودة > كمية)

#### الكلمات المفتاحية (Keywords) 
- ابحث عن الكلمات اللي الناس بتكتبها فعلاً  
- تجنب: meta keywords tag

#### الإعلانات والتصميم  
- عادي يكون في إعلانات، لكن **من غير إزعاج**  
- الموقع يكون سريع ومريح على الموبايل

#### الروابط (Links) 
- داخلية: تساعد جوجل يكتشف صفحات جديدة  
- خارجية: اربط مواقع موثوقة فقط  
- استخدم `rel="nofollow"` لو الرابط مش موثوق أو مدفوع  
- نص الرابط (anchor text) يكون واضح وطبيعي

#### شكل النتيجة في البحث (SERP Appearance)
- **Title** واضح + يعبر عن الصفحة (50–60 حرف)  
- **Meta Description** مختصر + جذاب (150–160 حرف)  

#### الصور والفيديو  
- صور عالية الجودة + واضحة  
- **Alt text** وصفي (يساعد في بحث الصور)  
- فيديو: عنوان ووصف مفهوم + transcript لو ممكن

#### الترويج والنشر  
- شارك على السوشيال ميديا  
- تفاعل مع الناس (تعليقات، ردود)  
- التسويق الشفهي (word-of-mouth) أقوى  
- بلاش إفراط في الترويج الرخيص

### حاجات ما عادتش مهمة أو غلط  
- Meta keywords  
- حشو كلمات  
- عدد كلمات ثابت (جودة أهم)  
- الاعتماد على PageRank لوحده  
- الاعتقاد إن E-E-A-T عامل ترتيب مباشر (هو إشارة جودة، مش عامل رسمي)

### اللي تهتم بيه
1. سجل موقعك في **Google Search Console** وتابعه  
2. حسّن المحتوى باستمرار (حدث، أضف، أعد كتابة)  
3. استخدم **Structured Data** (schema markup) لو المحتوى ينفع (مثل مقالات، منتجات، FAQs)  
4. ركز على **Core Web Vitals** (سرعة، تجربة مستخدم)  

# Assignments
- [Elements And Comments](https://elzero.org/html-assignments-lesson-from-1-to-5/) -> 4 **Assignments**
- [Heading And Attributes](https://elzero.org/html-assignments-lesson-from-6-to-10/) -> 7 **Assignments**
- [Link, Image, List](https://elzero.org/html-assignments-lesson-from-11-to-14/) -> 4 **Assignments**
- [Table, Div](https://elzero.org/html-assignments-lesson-from-15-to-18/) -> 3 **Assignments**
- [Audio, Video](https://elzero.org/html-assignments-lesson-from-19-to-23/) -> 4 **Assignments**
- [Form Part One](https://elzero.org/html-assignments-lesson-from-24-to-27/) -> 2 **Assignments**
- [Form Part Two](https://elzero.org/html-assignments-lesson-from-28-to-30/) -> 3 **Assignments**
- [Form Part Three](https://elzero.org/html-assignments-lesson-from-31-to-34/) -> 4 **Assignments**
- [iFrame, ARIA](https://elzero.org/html-assignments-lesson-from-35-to-37/) -> 2 **Assignments**
# Assignments Solution
## Elements and Comments
### Assignment no.1
```html
<!-- HTML = Hyper Text Markup Language -->
```
---
### Assignment no.2
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>My First Page</title>

    <meta charset="UTF-8">
    <link rel="stylesheet" href="css/style.css">

    <style>
    </style>

    <script>
    </script>
</head>
<body>
    <p>This is my First Page</p>
</body>
</html>
```
---
### Assignment no.3
```html
<!-- No, Yes, No, No -->
```
---
### Assignment no.4
```html
<!--
Meta Tags
- For defining the content encoding
- To make the view responsive
- Set the description of the web content
- To define something
-->
<meta charset="UTF-8">
<meta name="description" content="This Is Description For My First Page">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="author" content="Potato">
```
---
## Heading and Attributes
### Assignment no.1
```html
<!-- Type Question 1 Answer Below -->
<!DOCTYPE html>

<!-- Type Question 2 Answer Below -->
Quark Mode

<!-- Type Question 3 Answer Below -->
Nope

<!-- Type Question 4 Answer Below -->
Nope

<!-- Type Question 5 Answer Below -->
Heading Formats
```
---
### Assignment no.2
```html
<!-- Nope -->
```
---
### Assignment no.3
```html
<!-- Nope -->
```
---
### Assignment no.4
```html
<!-- Yes -->
```
---
### Assignment no.5
```html
<!--
title     - Global
href
src
hidden    - Global
charset
class     - Global
id        - Global
type
-->
```
---
### Assignment no.6
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Book Store</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="css/style.css">
</head>
<body>

    <h1>Book Store</h1>
    <p>a Book Store</p>

    <h2>Devices</h2>

    <h3>Gaming Laptop</h3>
    <p>a gaming laptop</p>
    <hr>

    <h3>Basic Laptop</h3>
    <p>a basic laptop</p>
    <hr>

    <h3>Computer</h3>
    <p>a computer</p>
    <hr>

    <h2>Accessories</h2>

    <h3>Mouse</h3>
    <p>a mouse</p>
    <hr>

    <h3>Keyboard</h3>
    <p>a keyboard</p>
    <hr>

    <h3>Headphone</h3>
    <p>a headphone</p>
    <hr>

</body>
</html>
```
---
### Assignment no.7
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>My Page</title>
</head>
<body>

    <h1>My Page</h1>

    <p>This Is My Page</p>
    <p>This Is My First Work</p>

    <h2>Section One</h2>
    <p>This Is Section One</p>

</body>
</html>
```
---
## Link, Image, List
### Assignment no.1
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>My Page</title>
</head>
<body>

    <h1>My Info</h1>

    <p>My Name is <b>Osama Elzero</b></p>
    <p>I am <b>Available</b> for Hire</p>
    <p>
        My Hour Old Price is <del>$10</del>
        And The New Price is <mark>$300</mark>
    </p>
    <p>
        Visit My Website From This Link
        <a href="">Elzero Academy</a>
    </p>

    <hr>

    <h2>Here is Some Of My Clients</h2>

    <img src="" alt="" width="150" height="150" style="background-color: black;">
    <img src="" alt="" width="150" height="150" style="background-color: red;">
    <img src="" alt="" width="150" height="150" style="background-color: blue;">

    <hr>

    <h2>My Skills</h2>

    <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>
            JavaScript
            <ul>
                <li>Vuejs</li>
                <li>Reactjs</li>
                <li>
                    Angular
                    <ol type="1" start="4">
                        <li>v4.0</li>
                        <li>v5.0</li>
                        <li>v6.0</li>
                        <li>v7.0</li>
                        <li>v8.0</li>
                    </ol>
                </li>
                <li>Svelte</li>
            </ul>
        </li>
        <li>Python</li>
    </ul>

</body>
</html>
```
---
### Assignment no.2
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>My Page</title>
</head>
<body>

    <ul>
        <li>One</li>
        <ol type="A" start="3">
            <li>C</li>
            <li>D</li>
            <li>E</li>
        </ol>

        <li>Two</li>
        <ol type="I" start="3">
            <li>3</li>
            <li>4</li>
            <li>5</li>
        </ol>

        <li>Three</li>
        <ol type="a" start="4" reversed>
            <li>d</li>
            <li>c</li>
            <li>b</li>
        </ol>
    </ul>

</body>
</html>
```
---
### Assignment no.3
```html
<!-- كسلت اعمله -->
```
---
### Assignment no.4
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>My Page</title>
</head>
<body>

    <dl>
        <dt>Learn Programming</dt>
        <dd>Learn Computer Science</dd>
        <dd>Learn Database</dd>

        <dt>Design</dt>
        <dd>Learn Graphics</dd>
        <dd>Learn Sketching</dd>
    </dl>

</body>
</html>
```
---
## Table, Div
##### Assignment no.1
```html
```
##### Assignment no.2
```html
```
##### Assignment no.3
```html
```
## Audio, Video
##### Assignment no.1
```html
```
##### Assignment no.2
```html
```
##### Assignment no.3
```html
```
##### Assignment no.4
```html
```

## Form Part 1
##### Assignment no.1
```html
```
##### Assignment no.2
```html
```
## Form Part 2
##### Assignment no.1
```html
```
##### Assignment no.2
```html
```
##### Assignment no.3
```html
```
## Form Part 3
##### Assignment no.1
```html
```
##### Assignment no.2
```html
```
##### Assignment no.3
```html
```
##### Assignment no.4
```html
```

## iFrame, ARIA
##### Assignment no.1
```html
```
##### Assignment no.2
```html
```
