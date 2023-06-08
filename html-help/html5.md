# HTML5

## Semantic Elements

- The `<nav>` HTML element represents a section of a page whose purpose is to provide navigation links, either within the current document or to other documents. Common examples of navigation sections are menus, tables of contents, and indexes.

- It's not necessary for all links to be contained in a `<nav>` element. `<nav>` is intended only for a major block of navigation links; typically the `<footer>` element often has a list of links that don't need to be in a `<nav>` element.

- A document may have several `<nav>` elements, for example, one for site navigation and one for intra-page navigation. aria-labelledby can be used in such case to promote accessibility

- The `<header>` HTML element represents introductory content, typically a group of introductory or navigational aids. It may contain some heading elements but also a logo, a search form, an author name, and other elements.

- A main document `<header>`:

```html
<header>
  <h1>Main Page Title</h1>
  <img src="mdn-logo-sm.png" alt="MDN logo" />
</header>
```

- `<header>` for an `<artical>`

```html
<article>
  <header>
    <h2>The Planet Earth</h2>
    <p>
      Posted on Wednesday, <time datetime="2017-10-04">4 October 2017</time> by
      Jane Smith
    </p>
  </header>
  <p>
    We live on a planet that's blue and green, with so many things still unseen.
  </p>
  <p><a href="https://example.com/the-planet-earth/">Continue reading…</a></p>
</article>
```

- The `<hgroup>` HTML element represents a heading and related content. It groups a single `<h1>–<h6>` element with one or more `<p>`.

- The `<hgroup>` element allows the grouping of a heading with any secondary content, such as subheadings, an alternative title, or tagline. Each of these types of content represented as a `<p>` element within the `<hgroup>`.

- The `<main>` HTML element represents the dominant content of the `<body>` of a document. The main content area consists of content that is directly related to or expands upon the central topic of a document, or the central functionality of an application.

- The content of a `<main>` element should be unique to the document. Content that is repeated across a set of documents or document sections such as sidebars, navigation links, copyright information, site logos, and search forms shouldn't be included unless the search form is the main function of the page.

- The `<aside>` HTML element represents a portion of a document whose content is only indirectly related to the document's main content. Asides are frequently presented as sidebars or call-out boxes.

- Do not use the `<aside>` element to tag parenthesized text, as this kind of text is considered part of the main flow. Example:

```html
<article>
  <p>
    The Disney movie <cite>The Little Mermaid</cite> was first released to
    theatres in 1989.
  </p>
  <aside>
    <p>The movie earned $87 million during its initial release.</p>
  </aside>
  <p>More info about the movie…</p>
</article>
```

- The `<caption>` HTML element specifies the caption (or title) of a table.

- If used, the `<caption>` element must be the first child of its parent `<table>` element.

- When the `<table>` element that contains the `<caption>` is the only descendant of a `<figure>` element, you should use the `<figcaption>` element instead of `<caption>`.

- The `<label>` HTML element represents a caption for an item in a user interface.

- The `<menu>` HTML element is described in the HTML specification as a semantic alternative to `<ul>`, but treated by browsers (and exposed through the accessibility tree) as no different than `<ul>`. It represents an unordered list of items (which are represented by `<li>` elements).

- The `<section>` HTML element represents a generic standalone section of a document, which doesn't have a more specific semantic element to represent it.
- Sections should always have a heading, with very few exceptions.

- `<section>` is a generic sectioning element, and should only be used if there isn't a more specific element to represent it. As an example, a navigation menu should be wrapped in a `<nav>` element, but a list of search results or a map display and its controls don't have specific elements, and could be put inside a `<section>`.

- The `<article>` HTML element represents a self-contained composition in a document, page, application, or site, which is intended to be independently distributable or reusable (e.g., in syndication). Examples include: a forum post, a magazine or newspaper article, or a blog entry, a product card, a user-submitted comment, an interactive widget or gadget, or any other independent item of content.

- Each `<article>` should be identified, typically by including a heading (`<h1> - <h6>` element) as a child of the `<article>` element.
- When an `<article>` element is nested, the inner element represents an article related to the outer element. For example, the comments of a blog post can be `<article>` elements nested in the `<article>` representing the blog post.
- Author information of an `<article>` element can be provided through the `<address>` element, but it doesn't apply to nested `<article>` elements.
- The publication date and time of an `<article>` element can be described using the datetime attribute of a `<time>` element.

- An `<article>` can have `<section>s`

- If the contents of the element represent a standalone, atomic unit of content that makes sense syndicated as a standalone piece (e.g. a blog post or blog comment, or a newspaper article), the `<article>` element would be a better choice.
- If the contents represent useful tangential information that works alongside the main content, but is not directly part of it (like related links, or an author bio), use an `<aside>`.
- If the contents represent the main content area of a document, use `<main>`.
- If you are only using the element as a styling wrapper, use a `<div>` instead.

- The `<optgroup>` HTML element creates a grouping of options within a `<select>` element.

- The `<option>` HTML element is used to define an item contained in a `<select>`, an `<optgroup>`, or a `<datalist>` element. As such, `<option>` can represent menu items in popups and other lists of items in an HTML document.

- The `<picture>` HTML element contains zero or more `<source>` elements and one `<img>` element to offer alternative versions of an image for different display/device scenarios.

- The `<pre>` HTML element represents preformatted text which is to be presented exactly as written in the HTML file. The text is typically rendered using a non-proportional, or monospaced, font. Whitespace inside this element is displayed as written.

- The `<q>` HTML element indicates that the enclosed text is a short inline quotation. Most modern browsers implement this by surrounding the text in quotation marks. This element is intended for short quotations that don't require paragraph breaks; for long quotations use the `<blockquote>` element.

- The `<small>` HTML element represents side-comments and small print, like copyright and legal text, independent of its styled presentation. By default, it renders text within it one font-size smaller, such as from small to x-small.

- The `<summary>` HTML element specifies a summary, caption, or legend for a `<details>` element's disclosure box. Clicking the `<summary>` element toggles the state of the parent `<details>` element open and closed.

- The `<title>` HTML element defines the document's title that is shown in a browser's title bar or a page's tab. It only contains text; tags within the element are ignored. The `<title>` element is always used within a page's `<head>` block.

The contents of a page title can have significant implications for `search engine optimization (SEO)`. In general, a longer, descriptive title performs better than short or generic titles. The content of the title is one of the components used by search engine algorithms to decide the order in which to list pages in search results. Also, the title is the initial "hook" by which you grab the attention of readers glancing at the search results page.

A few guidelines and tips for composing good titles:

- Avoid one- or two-word titles. Use a descriptive phrase, or a term-definition pairing for glossary or reference-style pages.
- Search engines typically display about the first 55–60 characters of a page title. Text beyond that may be lost, so try not to have titles longer than that. If you must use a longer title, make sure the important parts come earlier and that nothing critical is in the part of the title that is likely to be dropped.
- Don't use "keyword blobs." If your title is just a list of words, algorithms often reduce your page's position in the search results.
- Try to make sure your titles are as unique as possible within your own site. Duplicate—or near-duplicate—titles can contribute to inaccurate search results.
