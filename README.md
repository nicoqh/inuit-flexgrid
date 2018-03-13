# inuit-flexgrid

Flexbox grid for [inuitcss](https://github.com/inuitcss/inuitcss).

Support for IE9 currently prevents inuitcss from using the flexbox layout mode.
This plugin serves as an alternative to the core layout system.

## Installation

npm:

```
npm install inuit-flexgrid --save
```

Yarn:

```
yarn add inuit-flexgrid
```

Import the plugin in the *objects* section of main.scss:

```scss
@import "node_modules/inuit-flexgrid/objects/objects.grid";
```

## Quick start

Cells are full-width and will stack on top of each other by default:

```html
<div class="o-grid">
  <div class="o-grid__cell">
  </div>
  <div class="o-grid__cell">
  </div>
</div>
```

Cells will in most cases be accompanied by utility classes that divide the grid
into fractions. These are provided by inuitcss:

```html
<div class="o-grid">
  <div class="o-grid__cell u-1/2">
  </div>
  <div class="o-grid__cell u-1/2">
  </div>
</div>
```

## Usage and configuration

### Distribute cells equally

`o-grid--auto` will divide the space equally between all containing cells
without the need for width utility classes. Sets `flex: 1 0 0` on cell elements
(`.o-grid > .o-grid__cell`).

```html
<div class="o-grid o-grid--auto">
  <div class="o-grid__cell">
    50%
  </div>
  <div class="o-grid__cell">
    50%
  </div>
</div>
```

### Horizontal alignment

`o-grid` can be used with the following modifiers for horizontal alignment:

* `o-grid--left`: Align cells left. Uses `justify-content: flex-start` (default).
* `o-grid--center`: Horizontally center cells. Uses `justify-content: center`.
* `o-grid--right`: Align cells right. Uses `justify-content: flex-end`.
* `o-grid--between`: Distribute free space between the cells. Uses `justify-content: space-between`.
* `o-grid--around`: Distribute free space around the cells. Uses `justify-content: space-around`.

If you want to omit some of the modifiers, or change their suffixes (`--left`,
`--center` etc.), simply set the `$inuit-flexgrid-alignment-values` before
importing `objects.grid`.

```scss
$inuit-flexgrid-alignment-values: (
    '--top': 'flex-start',
    '--middle': 'center',
    '--bottom': 'flex-end',
    '--baseline': 'baseline',
    '--stretch': 'stretch',
);

@import "node_modules/inuit-flexgrid/objects/objects.grid";
```

### Vertical alignment

`o-grid` can be used with the following modifiers for vertical alignment.

* `o-grid--stretch`: Stretch cells to fit the container. Uses `align-items: stretch` (default).
* `o-grid--middle`: Vertically center cells. Uses `align-items: center`.
* `o-grid--bottom`: Align cells to the bottom. Uses `align-items: flex-end`.
* `o-grid--top`: Align cells to the top. Uses `align-items: flex-start`.
* `o-grid--baseline`: Position cells at the baseline of the container. Uses `align-items: baseline`.

While the above modifier classes will affect every cell in the grid, you can
also align *specific cells* by using the following modifier classes with
`o-grid__cell`:

* `o-grid__cell--stretch`: Stretch cell to fit the container.
* `o-grid__cell--middle`: Vertically align cell.
* `o-grid__cell--bottom`: Align cell to the bottom.
* `o-grid__cell--top`: Align cell to the top.
* `o-grid__cell--baseline`: Position cell at the baseline of the container.

If you want to omit some of the modifiers, or change their suffixes (`--middle`,
`--bottom` etc.), simply set the `$inuit-flexgrid-justify-values` before
importing `objects.grid`.

```scss
$inuit-flexgrid-justify-values: (
    '--left': 'flex-start',
    '--center': 'center',
    '--right': 'flex-end',
    '--between': 'space-between',
    '--around': 'space-around',
);

@import "node_modules/inuit-flexgrid/objects/objects.grid";
```

### Content distribution

You can change the direction cells are placed in the grid with the following
classes:

* `o-grid--column`: Sets `flex-direction: column`. Cells will be layed out from
  top to bottom instead of from left to right.
* `o-grid--column-reverse`: Sets `flex-direction: column-reverse`. Cells will be
  layoued out from bottom to top.

### Reverse the order of cells

* `o-grid--reverse`: Place cells from right to left. Uses `flex-direction: row-reverse`.

### Pulling

You can pull cells to the left or to the right with the following modifier
classes:

* `o-grid__cell--pull-left`: Sets `margin-right: auto`.
* `o-grid__cell--pull-right`: Sets `margin-left: auto`.

### Gutter sizes

A set of gutter widths are provided as modifier classes. For example, the
following block will generate a grid with "large" gutters and a grid with no
gutters at all:

```html
<div class="o-grid o-grid--large">
    <div class="o-grid__cell">
    </div>
</div>

<div class="o-grid o-grid--flush">
    <div class="o-grid__cell">
    </div>
</div>
```

Available gutter sizes:

* `o-grid--tiny`
* `o-grid--small`
* `o-grid--large`
* `o-grid--huge`
* `o-grid--flush`

Without a modifier, the default gutter size is equal to `$inuit-global-spacing-unit`.
You have full control over which modifier classes are generated and how they are
suffixed. Simply override the `$inuit-flexgrid-spacing-sizes` variable before you
import the grid object:

```scss
$inuit-flexgrid-spacing-sizes: (
    null: $your-spacing-unit
    '--xs': $your-spacing-unit-xs,
    '--sm': $your-spacing-unit-sm,
    '--lg': $your-spacing-unit-lg,
    '--xl': $your-spacing-unit-xl,
    '--none': 0
) !default;

@import "node_modules/inuit-flexgrid/objects/objects.grid";
```

Remember to include the `null` key if you want the default `o-grid`
(without modifiers) to have gutters.
