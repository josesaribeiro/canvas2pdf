# Canvas2PDF 

Canvas2PDF exports an HTML canvas to PDF. In other words, this library lets you build a PDF document 
using the canvas API.

## How it works

We create a mock 2d canvas context. Use the canvas context like you would on a normal canvas. As you call methods, we 
use PDFKit to generate a PDF document.

## Usage

```javascript
//Create a new PDF canvas context.
var ctx = new canvas2pdf.Context(blobStream());

//draw your canvas like you would normally
ctx.fillStyle='yellow';
ctx.fillRect(100,100,100,100);
// more canvas drawing, etc...

//convert your PDF to a Blob and save to file
ctx.stream.on('finish', function () {
    var blob = ctx.stream.toBlob('application/pdf');
    saveAs(blob, 'example.pdf', true);
});
ctx.end();
```

## Dependencies
+ [PDFKit](http://pdfkit.org/)
+ [blob-stream](https://github.com/devongovett/blob-stream) required when using in a web browser.

## Using with node.js

`canvas2pdf` works with node.js. Note that neither a DOM or canvas library is needed.  

## Interactive Browser Demo
[Open Demo](https://joshua-gould.github.io/canvas2pdf/demo.html)

## Notes
+ Inspired by [Canvas2Svg](https://github.com/gliffy/canvas2svg)
+ Calling fill and then stroke consecutively only executes fill
+ Some canvas 2d context methods are not implemented yet (e.g. setTransform and arcTo)

## Status
[![Build Status](https://travis-ci.org/joshua-gould/canvas2pdf.svg?branch=master)](https://travis-ci.org/joshua-gould/canvas2pdf)

## License
MIT
