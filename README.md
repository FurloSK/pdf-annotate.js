#UPDATED VERSION

Fixed problems in my fork and updated PdfJS lib to docs/ example (I don't can update in NPM package. I always have more problems.)

- Annotation and highlighting worked in Safari (iPhone with iOS 12)
- Fix bug with Canvas that entering in repeat mode (overflow error)
- Fix render bugs. I updated PdfJS version and my render now is good

# pdf-annotate.js

[![build status](https://img.shields.io/travis/instructure/pdf-annotate.js.svg?style=flat-square)](https://travis-ci.org/instructure/pdf-annotate.js)
[![code coverage](https://img.shields.io/coveralls/instructure/pdf-annotate.js.svg?style=flat-square)](https://coveralls.io/r/instructure/pdf-annotate.js)

Annotation layer for [pdf.js](https://github.com/mozilla/pdf.js)

## Objectives

- Provide a low level annotation layer for [pdf.js](https://github.com/mozilla/pdf.js).
- Optional high level UI for managing annotations.
- Agnostic of backend, just supply your own `StoreAdapter` to fetch/store data.
- Prescribe annotation format.

## Example

```js
import __pdfjs from 'pdfjs-dist/build/pdf';
import PDFJSAnnotate from 'pdfjs-annotate';
import MyStoreAdapter from './myStoreAdapter';

const { UI } = PDFJSAnnotate;
const VIEWER = document.getElementById('viewer');
const RENDER_OPTIONS = {
  documentId: 'MyPDF.pdf',
  pdfDocument: null,
  scale: 1,
  rotate: 0
};

pdfjsLib.workerSrc = 'pdf.worker.js';
PDFJSAnnotate.setStoreAdapter(MyStoreAdapter);

pdfjsLib.getDocument(RENDER_OPTIONS.documentId).then((pdf) => {
  RENDER_OPTIONS.pdfDocument = pdf;
  VIEWER.appendChild(UI.createPage(1));
  UI.renderPage(1, RENDER_OPTIONS);
});

```

``` in HTML file, insert "viewport" with scale disabled because Safari in iPhone only work with it 
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0" />
```

See more [examples](/docs/ folder).

## Documentation

[View the docs](https://github.com/instructure/pdf-annotate.js/tree/master/docs).

## Developing

```bash
# clone the repo
$ git clone https://github.com/instructure/pdf-annotate.js.git
$ cd pdf-annotate.js

# intall dependencies
$ npm install

# start example server
$ npm start
$ open http://127.0.0.1:8080

# run tests
$ npm test
```
## License

MIT
