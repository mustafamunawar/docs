# CSS Flexbox

## Properties applied on flex-container

- The style `display: flex` makes an element "flex-container"

- The "direct" children of the "flex-container" automatically becomes "flex-items"

- All flex-items together makes the `content` of the flex-container

- A flex-container's properties include `flex-direction`, `flex-wrap`, `flex-flow`, `justify-content`, `align-items` and `align-content`

- `flex-direction: row | row-reverse | column | column-reverse`

- if `flex-direction` is row then the "main axis" is left-to-right and the cross-axis is top-to-bottom

- if `flex-direction` is column then the "main axis" is top-to-bottom and the cross-axis is left-to-right

- `justify` means align on "main-axis" while `align` means align on cross-axis.

- There are three alignment properties `justify-content`, `align-content` and `align-items`.

- There is no `justify-items` property.

- `align-items` determines how flex items are laid out along the "cross axis" on the current line. Used most often for vertical alignment as `align-items: center`

- `align-items: stretch | flex-start | flex-end | center | baseline`

- Because the flexbox layout is direction-agnostic, `left`, `right` or `middle` are generalized to be `flex-start`, `flex-end` and `center` for alignment specifications.

- The `gap`, `row-gap` and `column-gap` properties explicitly controls the space between flex items. The specify and ensure the minimum gutter.

- The `gap` spacing is a minimum gutter, and if the gutter is bigger somehow (because of something like `justify-content: space-between`) then the gap will only take effect if that space would end up smaller.

- `flex-wrap: nowrap | wrap | wrap-reverse`

- `flex-flow` is short form of specifying `flex-direction` and `flex-wrap` together in one line

- `justify-content` defines the alignment along the main axis. It helps distribute extra free space leftover

- `justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly`

- `align-content` aligns a flex container’s lines within when there is extra space in the cross-axis, similar to how justify-content aligns individual items within the main-axis.

- when there is only one line `align-content` has no effect (to be confirmed) ???

- `align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch`

- `align-items` defines how flex items are laid out along the cross axis on the current line. Think of it as the `justify-content` version for the cross-axis. It is effective for flex-items that are in more than one line (multiline)

- `align-items: stretch | flex-start | flex-end | center | baseline `

## Properties applied on flex-items:

- `order: n` (where n is a number) on a flex-item forces it to be in nth position regardless of its order in the html markup.

- For `order` to work properly each flex-item should be given an order.

- `flex-grow` has meaning only if there is "remaining space" in flex-container after accomodating all flex-items.

- By default `flex-grow` is `0`, means the items will not grow even there is extra space in the flex-container

- `flex-shrink` comes in effect if the available space in flex-container is less than the total needed to accomodate all flex-items.

- By default `flex-grow` is `1` means, the items will shrink "equally" if the flex-container is smaller than the total space needed to accomodate all flex-items.

- The `flex-basis` property defines the size of the flex-item along the "main axis" of the flex container.

- `flex-basis: auto` looks up the "main size" of the element and defines the size. For example, on a horizontal flex container, the "main-size" is "width". Then `auto` will look for width. And on a vertical flex container, the "main-size" is "height". Then `auto` will look for height. if the "main size" is not specified then `auto` will fall back to `content`.

- `flex-basis: content` resolves the size based on the element’s content, unless width or height is set through normal box-sizing.

- In both the cases where `flex-basis` is either `auto` or `content`, if main size is specified, that size will take priority.

- If `flex-basis` is some measurement value (e.g. 50px, 5rem, 30% etc) This value will act as initial value. It is just as specifying width or height, but only more flexible. flex-basis: 20em; will set the initial size of the element to 20em. Its final size will be based on available space, `flex-grow` and `flex-shrink` values.

- It is recommended to use `flex-grow` and `flex-shrink` and `flex-basis` together using just `flex`.
