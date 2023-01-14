# HTML <img>

- This is a void element (meaning, it cannot have any child content and cannot have an end tag) that requires two attributes to be useful: src and alt. The src attribute contains a URL pointing to the image you want to embed in the page. As with the href attribute for <a> elements, the src attribute can be a relative URL or an absolute URL. Without a src attribute, an img element has no image to load.

- The <img> tag is empty, it contains attributes only, and does not have a closing tag.

- The <img> tag has two required attributes:

  1. src - Specifies the path to the image
  2. alt - Specifies an alternate text for the image

- Images are not technically inserted into a web page; images are linked to web pages. The <img> tag creates a holding space for the referenced image.
- When a web page loads, it is the browser, at that moment, that gets the image from a web server and inserts it into the page. Therefore, make sure that the image actually stays in the same spot in relation to the web page.

- Always specify the width and height of an image. If width and height are not specified, the web page might flicker while the image loads.
- Web performance advocates have often advised to add dimensions to your images for best performance to allow the page to be laid out with the appropriate space for the image, before the image itself has been downloaded. This avoids a layout shift as the image is downloaded.

- To keep aspect ratio intact but also resize use:

```css
img {
  width: 100%;
  height: auto;
}
```

- to limit resizing to original size use:

```css
img {
  max-width: 100%;
  height: auto;
}
```

- HTML elements like <img> and <video> are sometimes referred to as replaced elements. This is because the element's content and size are defined by an external resource (like an image or video file), not by the contents of the element itself.

- However, you shouldn't alter the size of your images using HTML attributes. If you set the image size too big, you'll end up with images that look grainy, fuzzy, or too small, and wasting bandwidth downloading an image that is not fitting the user's needs. The image may also end up looking distorted, if you don't maintain the correct aspect ratio. You should use an image editor to put your image at the correct size before putting it on your webpage.

- If you do need to alter an image's size, you should use CSS instead of HTML width and height attributes in the <img> tag.

### Background Images

- The CSS background-image property, and the other background-\* properties, are used to control background image placement. For example, to place a background image on every paragraph on a page, you could do this:

```css
p {
  background-image: url("images/dinosaur.jpg");
}
```

- Why not just use images as background images using CSS as described above and why bother with HTML images? As hinted to above, CSS background images are for decoration only. If you just want to add something pretty to your page to enhance the visuals, this is fine. Though, such images have no semantic meaning at all. They can't have any text equivalents, are invisible to screen readers, and so on. This is where HTML images shine!

### background-size

- contain
  Scales the image as large as possible within its container without cropping or stretching the image. If the container is larger than the image, this will result in image tiling, unless the background-repeat property is set to no-repeat.

- cover
  Scales the image (while preserving its ratio) to the smallest possible size to fill the container (that is: both its height and width completely cover the container), leaving no empty space. If the proportions of the background differ from the element, the image is cropped either vertically or horizontally.

- auto
  Scales the background image in the corresponding direction such that its intrinsic proportions are maintained.

- <length>
  Stretches the image in the corresponding dimension to the specified length. Negative values are not allowed.

- <percentage>
  Stretches the image in the corresponding dimension to the specified percentage of the background positioning area. The background positioning area is determined by the value of background-origin (by default, the padding box). However, if the background's background-attachment value is fixed, the positioning area is instead the entire viewport. Negative values are not allowed.

## <figure> and <figcaption> Tags

- an example:

```html
<figure>
  <img
    src="images/dinosaur.jpg"
    alt="The head and torso of a dinosaur skeleton;
            it has a large head with long sharp teeth"
    width="400"
    height="341"
  />

  <figcaption>
    A T-Rex on display in the Manchester University Museum.
  </figcaption>
</figure>
```

- A figure doesn't have to be an image. It is an independent unit of content that:

  - Expresses your meaning in a compact, easy-to-grasp way.
  - Could go in several places in the page's linear flow.
  - Provides essential information supporting the main text.
    A figure could be several images, a code snippet, audio, video, equations, a table, or something else.
