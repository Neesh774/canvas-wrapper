# canvas-multiline-text

Draws a text in a rectangle on a canvas, on multiple lines. If a word is too long to fit in the rectangle, it will be cut off with a dash and continued on the next line.

It was conceived to be used on Node.js with Automattic's implementation of Canvas [`node-canvas`](https://github.com/Automattic/node-canvas), but it should work in browsers too.

Initialy developed for [Toast](https://github.com/Neesh774/Toast).

## Usage
This module exports a single function that draws a text on a canvas' 2d context, breaking it in multiple lines if necessary.

The function also returns the used font size for drawing text.

```javascript
drawMultilineText(text, context, options)
```

### Example
```javascript
const canvas = new Canvas(500, 300)
const drawMultilineText = require('canvas-multiline-text')

const fontSizeUsed = drawMultilineText(
	canvas.getContext('2d'),
	"Please could you stop the noise, I'm trying to get some rest from all the unborn chicken voices in my head. What's that? What's that?",
	{
		rect: {
			x: 10,
			y: 10,
			width: canvas.width - 20,
			height: canvas.height - 20
		},
		font: 'Merriweather',
		verbose: true,
		lineHeight: 1.4,
		minFontSize: 15,
		maxFontSize: 120
)

console.log('Text drawn with font size: ', fontSizeUsed)
```

### Options
The whole `options` parameter (well) if optional.
 * `font` - Used font name or font family. Default is `sans-serif`.
 * `minFontSize` - Min font size for text. Default is `30`.
 * `maxFontSize` - Max font size for text. Default is `100`.
 * `rect` - Area for text. Default is `{ x: 0, y: 0, width: ctx.canvas.width, height: ctx.canvas.height }`.
 * `stroke` - If true, `strokeText()` wil be used instead of `fillText()`. Default is `false`.
 * `lineHeight` - Multiplicator for line height. Default is `1.1`. *
 * `verbose` - If true, greenlock-express will log (see below) the server bootstrap.
 * `logFunction` - Custom function for logging, with signature `logFunction(message)`. Default is `console.log`.

## Dependencies
This module require some kind of Canvas object, so in Node.js you'll need to have [`node-canvas`](https://github.com/Automattic/node-canvas) installed, even if it's not in this modul's dependencies list.