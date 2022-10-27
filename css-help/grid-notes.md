# CSS Grid

## Terminology

- Grid container: the element with `display: grid` or `display: inline-grid`
- This creates ` grid formatting context` for chidren of container (called "Grid elements").
- Grid elements: the direct descendents (children) of grid-container
- Grid lines: The dividing lines that make up the structure of the grid. They are vertical (“column grid lines”) and horizontal (“row grid lines”)
- Grid lines are defined implicitly when grid tracks are defined
- A grid track is the space between two adjacent grid lines.
- Grid tracks are defined in the explicit grid by using the `grid-template-columns` (defines column tracks) and `grid-template-rows` (defines row tracks) (you can also use the shorthand `grid` or `grid-template`).
- The value given to `grid-template-columns` or `grid-template-rows` is called `track list`, a space separated list of sizes (in px, % rem etc.)
- If elements (block (div) or inline(span) other than a string) are directly added to Grid container without defining tracks, they become rows.
- If a string is directly added to container, it is implicitly wrapped in an element and becomes a row-track.
- Common `grid-template-columns` usage:
- `grid-template-columns: 100px 300px 200px` creates 3 columns of widths 100px, 200px and 300px
- `grid-template-columns: 1fr 1fr 1fr` creates 3 equal-sized columns. Each column size is the `available space in the container divided by 3`
- `grid-template-columns: repeat(2, 10em 1fr)` repeats 2 times the `10em 1fr` so track list becomes `10em 1fr 10em 1fr`. Thus a 4 columns track.
- `grid-template-columns: repeat(auto-fill, 200px)` fills the container with as many 200px columns as will fit leaving a gap at the end if there is spare space.
- `grid-template-columns: repeat(auto-fill, minmax(200px, 1fr))` fills the container with as many 200px columns as will fit then distributes the remaining space equally between the created columns.
- `grid-template-columns: [full-start] 1fr [content-start] 3fr [content-end] 1fr [full-end]` creates 3 columns 1fr 3fr 1fr. So there are 4 (3+1) grid-column lines. By default these are numbers starting at 1 (1, 2, 3 and 4). But here the line numbers are changed to names using square brackets. 'full-start', 'content-start' etc. are custom line names.
- We can use any length units, or a percentage to create tracks. If the size of the tracks adds up to less than is available in the grid container, then by default the tracks will line up at the start of the container and the spare space will go to the end. This is because the default value of align-content and justify-content is start.

- `grid-template-columns: min-content max-content fit-content(10em)` uses 3keywords `min-content`, `max-content` and `fit-content(max-size)` where max-size argument is required.
- `min-content` column-track size will be `the size of the longest word in the column or largest fixed-size element` . it will wrap the content.
- `max-content` will cause the content to not do any soft-wrapping at all. In such column, any string of text will unwrap which may cause overflow.
- `fit-content(max-size)` the track will act like `max-content` with no wrapping until max-size value. At that point, it will start wrapping as normal. So the track may be smaller than the max-size, but never larger than max-size.

- If you end up with tracks that take up more space than you have in your container, they will overflow. If you use percentages then, as with percentage-based float or flex layouts, you will need to take care that the total percentage is not more than 100% if you want to avoid overflow.

- `2fr 3fr 1fr` in this track list (2+3+1) = 6, so 1fr = `'available-space'/6`,
- in the fr specification it `available-space` not the total-space of container which is divided. If any of your tracks contain a fixed-size element or a long word that can’t be wrapped, `this will be laid out before the space is shared out`.
- note the frs consume all available space so no space at end.

- `fr` can be mixed with fixed length tracks.
- `grid-template-columns: 100px 1fr 200px;` means first track 100px, third track 200px and second track take the remaining avail-able space.

- repeat(n, track-list ) saves typing out the same value or values over and over again.
- `grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr` can be shorten to
- `grid-template-columns: repeat(12, 1fr)` (you can use any unit like 200px etc.)
- multiple size values can also be repeated like
- `grid-template-columns: repeat(2, 1fr 200px 2fr)` means `grid-template-columns:1fr 200px 2fr 1fr 200px 2fr `
- repeat()can be part of a track-list like: `grid-template-columns: 1fr repeat(3,200px) 1fr`
- you can also use the keywords `auto-fill` or `auto-fit` in place of n in repeat function. That would mean container will be filled with as many tracks as will fit.

- `explicit grid` is when we use `grid-template-columns` and `grid-template-rows` to define grid tracks.
- `implicit grid` is when Grid creates grid tracks itself. These implicit tracks will be auto-sized by default.
- But you can set a size for implicit rows or columns by using the `grid-auto-rows` or `grid-auto-columns` properties.
- These properties take a track-list, so if you want all implicit columns to be at least 200 pixels tall but grow if there is more content, you could use the following:
- `grid-auto-rows: minmax(200px, auto)`

- `grid-auto-rows: auto 100px` means row-1 = auto-sized, row-2 = 100px, row3 = auto-sized, row4 = 100px and so on.

- Many layouts that make use of Grid don’t do any placement. They simply rely on placing the items in source order — one in each grid cell. This placement happens just by using `display: grid`, `grid-template-columns` and `grid-template-rows` css on the container (the parent). No Grid related css is specified for grid-elements (i.e. children). But once the Grid structure is defined the child elements can be explicitly placed in desired cells inth Grid. Following are the details:

- A child element is placed in a grid-area by specifying its 2 bounding column line numbers (or names) and 2 bounding row-line numbers (or names)
- These 4 bounding lines are specified by grid-column-start, grid-column-end, grid-row-start, grid-row-end.
- For a grid-element to be in second and third columns and 1, 2 and 3 rows the css will be:

```css
.item {
  grid-column-start: 2;
  grid-column-end: 4;
  grid-row-start: 1;
  grid-row-end: 4;
}
```

- or the same can be achieved with following the short hand notation which is the best way to specify:

```css
.item {
  grid-column: 2/4;
  grid-row: 1/4;
}
```

- if it is only one track then the second number can be omitted, i.e. `grid-column: 2/3` can be written as `grid-column: 2`
- Still more shorthand is `grid-area` which specifies all of `grid-row-start, grid-column-start, grid-row-end, grid-column-end` values in one go.
-

```css
.item {
  grid-area: 1 / 2 / 4 / 4; /*grid-area: start-row-value / start-col-value / end-row-value / end-col-value */
}
```
