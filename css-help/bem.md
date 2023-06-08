# BEM (Block Element Modifier) CSS class naming convention

## BEM Requirements

- Names are written in lowercase Latin letters.

- Words are separated by a hyphen -.

- The block is top-level item, its name defines the namespace for its elements and element modifiers.

- The element name is separated from the block name by two underscores \_\_ .

- The modifier name is separated from the block or element name by two dashes -- .

### Some BEM Examples

.block

`.block__element`

`.block__element--modifier`

- Note each of block, element and modifier can have hyphens (single dashes) in their names.

- Let's take a card-with-image block example with following CSS:

- `.card-with-image {}`
- `.card-with-image__image {}`
- `.card-with-image__description {}`
- `.card-with-image__button--submit {}`
- `.card-with-image__button--cancel {}`

The "block" is "card-with-image". Note that it has hypens(dashes) to separate words as in usual CSS class names
The "elements" are one "image", one "description" and two "button" items. These are preceeded by two undederscores
The "modifiers" are "submit" and "cancel" to represent two variation of "button" element. The modifiers "submit" and "cancel" are preceeded by two hyphens.
