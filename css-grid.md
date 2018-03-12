# CSS4 Grid: True layout finally arrives

There is no CSS Level 4… CSS the language no longer has levels. Technically this is CSS Grid level 1.

HTML 5.1 brings `<picture>` tag.

## Responsive Design

Defined by 3 characteristics

- Flexible grid-based layout
- Media queries
- Images that resize

## Floats

- A hack from the start, right after table-based layout.
- Features rows and cells.
- Rows clear the floats on the cells.
- Source ordering determines display, thoiugh some (minor) rearrangement is possible.
- Major disadvantage: equal column heights.

## Flexbox

- The first layout elements - but not designed to layout whole webpages.
- Features flex-containers (row) and flex-items (cells). Both are required to work.
- Excels at vertical centering and equal heights.
- Very easy to reorder.
- Major disadvantages.
  - Wasn't designed to be locked down for layouts. Works in 1 dimension only.
  - Browser support and syntax is challenging.

### 3 versions

- **2009:** `display: box`
- **2011:** `display: flexbox` // IE 11 only
- **2016:** `display: flex`

## CSS Grid

- Build into the CSS spec (now a recomendation).
- No "row" markup required.
- Designed to work in 2 dimensions.
- Flexbox for UI, Grid for major page layout.
- Offers column-span and row-span

### Support

- FF
- Chrome
- Safari
- Opera
- Edge 16+

#### Partial

- IE 10
- IE 11
- Edge 12-15

#### Workarounds

Polyfills are no good, use fallbacks instead.