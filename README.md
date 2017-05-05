# SemToNotes Utils

<!-- BEGIN-MARKDOWN-TOC -->
* [Installation](#installation)
	* [Browser](#browser)
	* [Node.JS / CommonJS](#nodejs--commonjs)
* [Load in Browser](#load-in-browser)
* [API](#api)
	* [XrxUtils](#xrxutils)
		* [`applyStyle(shapes, styleDef)`](#applystyleshapes-styledef)
			* [Example](#example)
		* [`createDrawing(elem, width, height)`](#createdrawingelem-width-height)
		* [`createShape(shapeType, image, options)`](#createshapeshapetype-image-options)
		* [`drawFromSvg(svgString, drawing, options)`](#drawfromsvgsvgstring-drawing-options)
		* [`svgFromShapes(shapes)`](#svgfromshapesshapes)
		* [`svgFromDrawing(drawing)`](#svgfromdrawingdrawing)
		* [`navigationThumb(thumb, image, style={})`](#navigationthumbthumb-image-style---)
	* [CoordUtils](#coordutils)
		* [`angleFromMatrix(m00, m01)`](#anglefrommatrixm00-m01)
		* [`coordIIIF(polygons, imgwidth, imgheight)`](#coordiiifpolygons-imgwidth-imgheight)
		* [`abs2rel(coords, absval)`](#abs2relcoords-absval)
		* [`rel2abs(coords, val)`](#rel2abscoords-val)
		* [`isRectangle(c)`](#isrectanglec)
* [Authors](#authors)

<!-- END-MARKDOWN-TOC -->

## Installation

### Browser

```
webpack -p
```

Then include the built library in `./dist` and semtonotes as `window.xrx`, either with the official release or `semtonotes-client`

### Node.JS / CommonJS

```sh
npm install semtonotes-utils
```

## Load in Browser

```html
<!-- semtonotes must be loaded before, e.g.
<script src="https://unpkg.com/semtonotes-client@0.2.0"></script>
-->
<script src="path/to/xrx-utils.js"></script>
```

Or via unpkg's cdn:

```html
<script src="https://unpkg.com/semtonotes-client@0.2.0"></script>
<script src="https://unpkg.com/semtonotes-utils@0.1.7"></script>
```

## API

<!-- BEGIN-RENDER src/xrx-utils.js -->
### XrxUtils
#### `applyStyle(shapes, styleDef)`
Apply a set of styles to one or more stylable elements.

- `@param {Array|Shape-Like} shapes` Stylable SemToNotes elements (shapes, groups...)
- `@param {object} styleDef` is an object of key-value pairs which map to xrx.shape.Style
methods

##### Example

```js
xrxUtils.applyStyle(rect1, {fillColor: '#aa9900'})
```
#### `createDrawing(elem, width, height)`
Create a drawing in DOMElement `elem`. Overrides goog.style.getSize with
width/height for non-visible elements.
#### `createShape(shapeType, image, options)`
Options:
- `@param string shapeType` Shape Type, `Rectangle` or `Polygon`
- `@param xrx.drawing.Drawing image` the SemToNotes canvas to create the shape in
- `@param Object options` Options.
#### `drawFromSvg(svgString, drawing, options)`
Translate `svgString`, a string containing SVG, to shapes and draw them
in `drawing`.
For options see [shapesFromSvg](#shapesFromSvg).
#### `svgFromShapes(shapes)`
Generate SVG from a list of shapes or a shapeGroup.
Create a ShapeGroup from the rect/polygon of an SVG.
- `@param string svgString` SVG as a string
- `@param xrx.drawing.Drawing drawing` the drawing to create the group in
- `@param Object options`
- `@param Boolean options.absolute` Force absolute coordinates. Default: `false`
- `@param Boolean options.scaleWidth` Fixed scale factor to scale x-coordinates by.
      Calculated unless provided. Falls back to `1` if not possible (i.e. absolute coords)
- `@param Boolean options.scaleHeight` Fixed scale factor to scale y-coordinates by. Falls back to scaleWidth.
- `@param Boolean options.svgWidth` Provide the width of the SVG context to scale coordinates by.
- `@param Boolean options.svgWidth` ditto height
- `@param Boolean options.imgWidth` Override the width determined by the background image of the canvas.
- `@param Boolean options.imgWidth` ditto height
- `@returns xrx.shape.ShapeGroup`
#### `svgFromDrawing(drawing)`
Generate SVG from all shapes in a drawing.
#### `navigationThumb(thumb, image, style={})`
Show the viewbox of `image` as a rectangle in `thumb`

<!-- END-RENDER -->

<!-- BEGIN-RENDER src/coord-utils.js -->
### CoordUtils
#### `angleFromMatrix(m00, m01)`
Calculate the angle between two matrices.
#### `coordIIIF(polygons, imgwidth, imgheight)`
TODO
#### `abs2rel(coords, absval)`
`coords` is a list of float tuples. Multiply every float with 1000 and divide by `absval`
#### `rel2abs(coords, val)`
`coords` is a list of float tuples. Multiply every float with `val` and divide by 1000
#### `isRectangle(c)`
Determine whether an array of coordinates is a rectangle.

<!-- END-RENDER -->

## Authors

* Leonhard Maylein
* Jochen Barth
* [Dulip Withanage](https://github.com/withanage)
* [Konstantin Baierer](https://github.com/kba)
