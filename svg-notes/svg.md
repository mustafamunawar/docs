# SVG Notes

By default, [an SVG] will be drawn at the size specified in the code, regardless of the size of the canvas. What happens if you set the height or width (or both) to "auto" for these SVGs? The default size for HTML replaced elements will be used: 300px wide, 150px tall. This applies for <img>, <object> or <iframe>. The default 300x150 size also applies to inline <svg> elements within HTML documents, but that's a relatively recent consensus from the HTML5 specifications: other browsers will by default expand inline SVG to the full size of the viewport—equivalent to width: 100vw; height: 100vh; — which is the default size for SVG files that are opened directly in their own browser tab. Internet Explorer cuts the difference, using width of 100% and height of 150px for images and inline SVG.

If no size (width & height)is specified on an svg element AND no viewbox is specified then default width = 300px and height= 250px.
However as soon as a viewbox is specified svg width and height become 100% of containing element. But if svg width & height are specified then they remain the same and viewbox creates a panning & zooming mechanism wrt svg specified size (note as said before if size on svg is not specified then specifying viewbox make svg size equal to its container)

The order in which you list the attributes makes no difference, only the attribute names.
If any of the geometric attributes are left out, the corresponding coordinate will default to 0.
All SVG shapes, even <line> and <polyline>, are by default styled with fill: black and stroke: none. This means that, by default, a <line> will not be visible. There is no area inside a straight line to be filled in.
We can use CSS styles or use directly svg element’s presentation attributes to set these attributes.
In addition to user coordinate values, each attribute can be given as a percentage, or as a length with unit. The units defined in SVG 1.1 are the same as those defined in CSS 2: px, pt, pc, cm, mm, in, em, and ex.

An <svg> element can have its own <style> and <script> elements.

When creating svg drawing elements in JS you need to use createElementNS with the SVG namespace URI in order to create a valid SVG element. However, the namespace can be accessed from the namespaceURI property of any existing SVG element.

As with <line>, if any of the geometric attributes x, y, width, or height are not specified on a <rect>, they default to 0. However, if either width or height is zero, the rectangle will not be drawn at all—not even the stroke. A negative width or height is invalid.
The value of each attribute can be specified as a length, percentage, or number. Numbers are lengths in user units, which are equivalent to px units. Percentages are proportional to the SVG size: its width, its height, or its diagonal divided by √2, depending on whether the measurement is horizontal, vertical, or other.
When used within an HTML <img> tag or CSS background-url, SVGs act identically to bitmaps. The browser will disable any scripts, links, and other interactive features embedded into the SVG file. You can manipulate that SVG using CSS in an identical way to other images using transform, filters, etc. The results are often superior to bitmaps because SVGs can be infinitely scaled.

An SVG can be inlined directly in CSS code as a background image. This can be ideal for smaller, reusable icons and avoids additional HTTP requests. For example:
.mysvgbackground {
background: url('data:image/svg+xml;utf8,<svg xmlns="https://www.w3.org/2000/svg" viewBox="0 0 800 600"><circle cx="400" cy="300" r="50" stroke-width="5" stroke="#f00" fill="#ff0" /></svg>') center center no-repeat;
}

SVGs can be placed directly into HTML markup. The image then becomes part of the DOM and can be manipulated using CSS and JavaScript.

SVG elements such as paths, circles, rectangles etc. can be targeted by CSS selectors and have the styling modified using standard SVG attributes as CSS properties. For example:

/_ CSS styling for all SVG circles _/
circle {
stroke-width: 20;
stroke: #f00;
fill: #ff0;
}
This overrides any attributes defined within the SVG because the CSS has a higher specificity. SVG CSS styling offers several benefits:

• attribute-based styling can be removed from the SVG entirely to reduce the page weight.
• CSS styling can be reused across any number of SVGs on any number of pages.
• the whole SVG or individual elements of the image can have CSS effects applied using :hover, transition, animation etc.

The group element <g> is used for logically grouping together sets of related graphical elements.
The <g> element groups all of its descendants into one group. It usually has an id attribute to give that group a name. Any styles you apply to the <g> element will also be applied to all of its descendants. This makes it easy to add styles, transformations, interactivity, and even animations to entire groups of objects. The <g> element has one more feature: it can have its own <title> and <desc> tags that help make it more accessible to screen readers.
<g> elements don’t allow for x and y attributes to change the group’s position. You can, however, use transforms on groups. e.g.
<g class="logs" transform="translate(0,10)">

A group (<g>) provides a logical structure to the shapes in your graphic, but it has the additional advantage that styles applied to a group will be inherited by the shapes within it. The inherited value will be used to draw the shape unless the shape element specifically sets a different value for the same property.

Although the “<g>” element gives us an opportunity to group elements, it is not possible to assign a position to the “<g>” element itself. Although if <g> is used as template then it can be transformed in the <use>.

The <use> element lets you reuse existing elements, giving you a similar functionality to the copy-paste functionality in a graphics editor. It can be used to reuse a single element, or a group of elements defined with the <g> element. Example of a <use>:
<use x="100" y="100" xlink:href="#bird" />
Problems with <use> for simple elements and groups (not unders <defs> or <symbol>:
The x and y coordinates are a shorthand for translating an element using the transform attribute. They are relative to original svg not to the origin.
The “instances/copies” of the original element will have the exact same styles as the original element.
An element (or a group <g> ) can be reused by using <use> if it is already rendered on the canvas. You can’t have an element as template. It has to be rendered first.

The <defs> element is used to define elements without directly rendering them [..] and that element will serve as a template for future use using <use>.
Just writing svg elements and groups (with assigned ids) between <defs> and </defs> make them “templates” that can be instanciated using <use> elaments. Any shape element (rect, line etc.), <g> and <symbol> can be put inside the <defs> element:
The <defs> element serves as a container for referenced content. Graphics inside a <defs> element won’t display until referenced elsewhere. They’re defined inside <defs>, but need to be called by another element or attribute before they’re rendered to the screen.

Benefits of Symbol element:
• The viewBox can be defined on the symbol, so you don’t need to use it in the markup (easier and less error prone).
• title and desc tags can be added within the <symbol> and they kinda “come along for the ride” when the symbol gets used, making accessibility easier to do right.
• Symbols don’t display as you define them, so no need for a <defs> block.

“In svg first the element is styled under absence of filter effects, clipping, masking, and opacity. Then the element and its descendants are drawn on a temporary canvas. In a last step the following effects are applied to the element in order: filter effects, clipping, masking and opacity.”
(Therefore, you need to wrap the masked element in a <g> and apply the glow filter there!)
