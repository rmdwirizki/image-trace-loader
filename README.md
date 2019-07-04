[![npm][npm]][npm-url]

# JSON Image Trace Loader
Loads images and exports traced outlines as image/svg+xml URL-encoded data to one JSON file

## Beware

Example folder not working. Just leave it be.

## Install
```bash
npm install --save-dev json-image-trace-loader
```

## Inspiration
Forked from [Image Trace Loader](https://github.com/ducban/image-trace-loader).

## Usage
The `json-image-trace-loader` loads your image and exports the url of the image as `src` and the image/svg+xml URL-encoded data as `trace` in a JSON File.

It will be used in conjunction with [url-loader][url-loader].

**webpack.config.js**
```js
module.exports = {
  module: {
    rules: [
      {
        test: /\.(gif|png|jpe?g)$/i,
        use: [
          {
            loader: 'json-image-trace-loader',
            options: {
              inputPath: 'images/',
              outputPath: 'data/',
              publicPath: 'public',
              file: 'traced.json'
            }
          },
          {
            loader: 'url-loader',
            options: {
              options: {
                name: 'images/[name].[ext]',
                limit: 8192
              }
            }
          }
        ]
      }
    ]
  }
}
```

**Output Example: public/data/traced.json**
```json
{
  "banner-img.png": {
    "src": "images/mix/banner-img.png",
    "trace": "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='956' height='851' viewBox='0 0 956 851' version='1'%3E%3Cpath d='M194 196l-5 2c-3 1-6 7-7 14-2 8-4 11-8 12-5 2-7 7-6 13 0 4 0 5-2 8-3 3-3 6 1 11 4 3 4 4 12 4s12-2 15-7l4-5c3-3 4-5 2-9v-6c1-2 1-2 4-1 4 0 4 0 5-3l3-3 1-5 1-6c4-6 1-14-7-18-5-2-9-3-13-1m574 56v26c0 3 1 3 4 4 11 1 1 2-32 2-36 0-37 0-38 2v3l-1 1-1-3c0-5-2-6-10-6h-7l-1 21c0 24 0 24 10 23 6-1 8-3 8-7s2-4 2 0l1 4h17c21 0 20 0 20 10l1 7h22c19 1 23 1 24-1h5c6 3 9 2 14-1 2-2 7-4 11-4l7-2h1l4 6 3 5 2 4c4 3 2 15-4 17-1 1-2 2-3 9v51a845 845 0 0 0 13 77c-3 1-8 5-8 7 0 1 39 2 40 1s0-4-3-7c-2-3-2-3-2-18 0-12 0-17-2-20v-76c3-48 2-57-8-78-5-11-10-16-15-16-2 0-2 0-2-2l1-6 3-6c2-3 3-6 0-9v-4c2-5 1-9-1-12-4-3-14-4-19-1-3 1-4 2-4 6s0 4 2 3h13c3 1 3 4 2 11-1 2-2 3-6 3l-4 2c0 2-4 1-5-1l-3-2v-5c0-1 1-2 3-2 3 0 3-3 0-3-3-1-7 3-7 7l1 7a566 566 0 0 1 5 13l1 1c-3 0-9 10-12 19l-3 10c-2 3-3 3-11 3h-9c-1-2 2-3 7-3h5v-38h-3l-4-1c-1-1 1-1 5-1l8-1 1-16v-14l-19-1c-16 0-19 0-19 2m-556 18l-5 1c-3 0-3 0 1 9s8 13 21 21l10 6c0 2 4 3 9 2h5l-3-2c-3-1-4-3-2-3 3 0-4-3-6-3s-5-2-11-7c-11-10-12-11-15-19-2-6-3-7-4-5m614 23c-2 0-2 0 0 4 2 5 11 8 16 4 4-2 2-7-3-6l-3-1c0-1-1-2-4-2l-6 1m-663 8l-3 11c0 8 3 14 9 17l5 2h-11l-11 1c-1 2 1 5 3 5s2 0 2 5a94252 94252 0 0 0-26 289c2 0 3-1 4-11l1-10 47-1c46 0 47 0 47-2s-1-2-47-2l-47-1 3-26v-4h46c44 0 45 0 45-2s-1-2-45-2l-45-1 1-13 1-15v-2h44c43 0 44-1 44-2 0-2-1-3-44-3h-43v-3l1-15 2-12 41-1h42l1 5a499 499 0 0 0 2 3c2-5 2-7-6-88a15032 15032 0 0 1-6-86c2-1 3-5 1-6h6l7 1-1 4c-1 5-1 13 1 25s1 20-2 24c-2 3-2 5-2 8 0 2 5 3 5 1 1-1 2-1 4 1l7 2 4 2c0 2 4 1 5-1h4c6 2 14-2 13-5-1-2-2-2-5-2-4 0-5 0-7-3l-3-5a1065 1065 0 0 0-7-57c0-8-2-9-28-18l-26-10-9-1-16-1-6-1-2 6m604 15c-1 3 0 6 3 8 4 3 7 1 7-6 0-5-8-7-10-2m-605 22l-2 10v9h55v-7l-2-10v-3h-26l-25 1m611 12c-2 0-4 1-4 3l18 57 22 69 5 14 2-2 6-2 3-2-22-67-23-69c-2-3-3-3-7-1m-23 5a4593 4593 0 0 1-43 132l11 5c2-1 46-139 45-140l-11-3-2 6m-591 8l-2 25-1 4h62v-2l-1-15-1-13h-29l-28 1m85 4l-2 9c-1 7-1 8 1 11 1 2 5 4 7 2 1 0 1-7-2-15l-4-7m405 28a212 212 0 0 1-51 64c-15 15-17 17-17 19l3 10c2 6 3 7 5 7s2 0 4 6l4 12 11 34c3 8 7 12 10 12 4 0 16-7 24-14l7-6 2 2 2 5 2 4c1 1 1 1 1-3l-2-9c0-3 0-4 2-4l3-1-3-2-2-2h2c4-1 3-4 0-3-4 0-4-2-1-5 2-2 4-2 12-1 7 2 10 4 11 11 0 6-2 15-5 16-2 0-3 4 0 5 2 1 6-2 8-5 1-3 2-4 5-4 4 0 6-3 6-8 0-4 0-5-3-7l-3-4c0-3-4-7-7-9l-6-2-9-1-6 1-5-4a146 146 0 0 0-11-10l6-4c13-8 24-23 31-39 6-16 10-38 10-58v-10h-4l-18-2h-14l-4 9m-493 5l-3 27 35 1h34v-5l-3-25-31-1h-32v3m688-1l-1 31c1 26 1 29 3 35l3 19c1 15 2 17 6 17l5-1-1-8-4-25c-2-20-3-26-6-30-1-3-2-9-2-22-1-16-2-18-3-16m-570 15l-10 1a166 166 0 0 0 10 74c4 9 13 25 14 24 1 0 3-4 4-9 3-7 4-8 6-8l6 11c3 9 4 13 3 14h-18c-2-1-2 5-2 64l1 66h21v-5l1-4 6 19 1 4-2 5c-2 0-3 2-3 3-1 1-2 2-6 2l-6 1c-4 1-10 12-11 20l-1 6v1c2 2 1 4-2 4l-4 1 3 1h3v20c0 23 0 24 9 32 7 6 6 3 4 27 0 11 0 11 2 15 5 7 6 7 30 7 20 0 23 0 43-4 41-6 56-13 56-22 0-5-4-9-11-11l-5-1 11-4 12-3 1-6 2-7v-1l3-12c1-9 2-12 1-13l-32-1-32 1-2 6-1 6-4-2c-2-2-3-2-5-15a211 211 0 0 0-6-26c-2-9-4-13-7-15v-1l2-1-5-1c-5 1-12 0-12-1l-3-3c-3-2-4-3-4-5s1-3 5-3c6 0 8-2 9-9s0-18-3-23v-6c4-6 1-11-5-11h-3l-1-36 1-36 6 1c12 2 30 3 43 2 20-2 19-1 19-7 0-13-8-33-19-48l-29-32-33-36-9-12h-16l-26 2m217 12c-4 3-6 9-3 14l4 5 33 1c29 0 30 0 30 2l1 3c2 2 2 3-2 3-3 1-4 4-1 7 1 2 1 2-1 5-3 3-3 6 0 7 3 0 3 2 0 5-3 2-2 4 3 5 2 1 2 1 1 3v5c0 2 0 3 3 3s3 0 2 4l-4 11c-7 13-11 30-8 34 5 5 31 19 37 19 3 0 3 2 2 5-3 3-2 6 2 10 3 3 3 3 2 6-1 5-1 8 3 9 3 1 4 2 3 7s0 7 5 8c3 1 4 1 4 6v5h9v5l1 6h6l1-1c1 0 2 1 1 2l2 5c4 4 4 8 1 9-3 2-4 3-4 6l-2 2c-6 2 2 8 12 11 8 2 9 1 11-2 1-5 4-5 5-1l4 2c1 0 2 1 2 3s0 2-6 2h-7v7c0 7 1 7-13 4-22-6-37-13-44-20-2-3-4-4-4-3 0 2 3 7 7 10 3 3 3 3 1 3l-2 1 4 1 10 3a203 203 0 0 0 41 12 589 589 0 0 1-6 30v1c2 0 2 0 0 12-1 6-2 11-1 12 1 2 8 5 10 4l4 1c0 3 4 2 5 0l5-15a82 82 0 0 1 4-15c0-3 4-20 6-22s3-1 4 4a373 373 0 0 0 4 27l-3-2c-3 0-10 3-10 5l9 22c1 1 2 1 4-1h4v3l1 2h2c1-2 5-3 6-1s5 1 7-1l2-8v-53l6-1c11 0 13-1 14-4v-10c0-7 0-8 2-10s2-3 2-13v-11l10-2c13-3 16-6 10-12l-6-4-4-3c0-2-1-3-10-3h-10v-23c0-27 1-26-12-26l-8 1 2 3 3 8c1 6 1 7-1 11v12l-2 18-1 21-1 4h-24l1-4 2-9 2-9 1-6c2-7 3-12 2-13-2-2-3 0-5 6a517 517 0 0 1-12 36c-2 0-3 1-4 4l-1 6c0 3-4 3-4 0l-3-2-3-4 1-5 1-5h-6c-5 0-6 0-7-3l-2-4-1-3c0-2-4-5-8-6-2-1-4-2-4-5-1-3-4-5-8-6l-2-4c0-4-1-6-5-7-3-2-3-2-3-7 0-4 0-5-2-6l-4-3v-4c0-3 0-5-2-8-3-4-3-6-2-10 0-2 1-2 4-2 6 1 7 0 4-9a739 739 0 0 1-9-34c1 0 2 0 2-3 0-4 0-4-3-4l-3-3c0-1-1-2-4-2l-5-2v-10c2-3 2-4 0-9l-2-5-3 3-5 6-2 3-2-3c-4-5-6-13-6-24l1-12c2-1 2-3 2-5-1-3-1-3 1-3 4 0 8-6 8-12 0-4-1-5-4-8l-3-3h-34c-33 0-35 0-38 2m-338 7l-3 27v3h38c34 0 37 0 37-2l-3-27v-2h-35l-34 1m-4 36a1062 1062 0 0 1-3 29l82 1-1-13-1-15v-3h-38l-39 1m555 23c-5 3-7 10-3 15 4 3 10 3 13-1 4-4 4-8-1-12-4-3-4-4-9-2m116 0c-3 0-5 4-5 9s2 8 8 8c7 0 12-9 7-14l-7-4-3 1m-500 16c-3 10-4 12-2 13h18c1-1 0-4-3-13-4-11-5-12-7-12s-2 1-6 12m401-11c-1 0-2 1-2 3v2h46c41 0 46 0 47-2 1-3-1-3-46-4l-45 1m-448 24l-8 1-7-1 1 65v65h10c10 0 10-1 10-3a17066 17066 0 0 1-1-127h-5m35 46l1 50v14l2-2c5-5 5-6 5-51v-42l-4-2-4-2v35m113 11l-1 4-1 4c-3 1-6 6-6 9l1 5c2 2 2 6 1 8l-2 5 2 5c1 2 1 6-1 9l-1 5c1 5 5 7 13 8l7 1h2l16-1 16 1h2a236 236 0 0 1 51 0l6-1c11 0 16-5 13-13l-3-4 2-4c2-5 3-8 1-11-2-2-2-6-1-9 3-3 2-7-2-11l-4-7v-3l-56-1-55 1m384 55c-6 2-10 5-10 7s0 2 4 0c11-5 27-5 40 2l1-2c-1-4-9-7-20-8l-15 1m27 21c-8 1-11 3-11 7l-1 2-2 1c-1 2 4 6 9 8s25 2 33 0c7-2 9-3 9-6 0-2-6-7-9-9l-2-1v-2h-26m97 5c-14 15-69 28-140 31l-19 1 1 2c0 2 2 2 16 2a1098 1098 0 0 0 72-8c43-7 69-17 73-29l1-3-4 4m-546 72c-2 9-3 7 8 15l11 8 5 3 5 3c1 2 2 2 12 2h11l3-17 4-17-29-1h-29l-1 4m-170 3a705 705 0 0 1-9 23l1 2s1 2 3 2l6 3 4 1 14-30c0-2-9-7-14-7-2 0-3 1-5 6m142 8v21c0 2 2 2 8 1l7 1-2 1c-4 0-11 3-11 5s2 2 25 2l27-1c3 0 3-3-1-6-2-2-3-2-19-2h-16v-3l2-6c0-2 0-3-3-4-5-2-10-6-13-12l-3-6-1 9m23 14l-1 4-1 2h14c12 0 14 0 13-1l-9-3-12-3c-4-1-4-1-4 1m313 72l-3 1c-1 0-5 5-4 6h24c1-1 0-2-9-5l-8-2m-93 4c-10 4-7 5 8 4l10-1c0-2-6-5-9-5l-9 2' fill='%23fcd444' fill-rule='evenodd'/%3E%3C/svg%3E"
  },
}
```

## Options
The loader options allows you to specify values for all the parameters of the [Potrace class][potrace-class], with the addition of `skipTraceIfBase64`.

|Name|Type|Default|Description|
|:--:|:--:|:-----:|:----------|
|**`turnPolicy`**|`{String}`|`TURNPOLICY_MINORITY`|How to resolve ambiguities in path decomposition. Possible values are `TURNPOLICY_BLACK`, `TURNPOLICY_WHITE`, `TURNPOLICY_LEFT`, `TURNPOLICY_RIGHT`, `TURNPOLICY_MINORITY`, `TURNPOLICY_MAJORITY`. Refer to page 4 of [this document][potrace-algorithm] for more information|
|**`turdSize`**|`{Number}`|`100`|Suppress speckles of up to this size. Larger values significantly reduce the size of the traced outline|
|**`alphaMax`**|`{Number}`|`1`|Corner threshold parameter. Lower values results in rougher edges, but significantly reduces the size of the traced outline|
|**`optCurve`**|`{Boolean}`|`true`|Curve optimization|
|**`optTolerance`**|`{Number}`|`0.2`|Curve optimization tolerance|
|**`threshold`**|`{Number\|String}`|`THRESHOLD_AUTO`|Threshold below which the color is considered `color`. Should be a number in range 0..255 or `THRESHOLD_AUTO` in which case threshold will be selected automatically using [Algorithm For Multilevel Thresholding][multilevel-thresholding] |
|**`flipColors`**|`{Boolean}`|`false`|Specifies whether fill color and background color should be swapped|
|**`color`**|`{String}`|`COLOR_AUTO`|Fill color. `COLOR_AUTO` will extract and use the most prominent color of the source image|
|**`background`**|`{String}`|`COLOR_TRANSPARENT`|Background color|
|**`skipTraceIfBase64`**|`{Boolean}`|`false`|If set to `true`, will not generate a traced outline if the image already is base64 encoded. Useful when the inlined base64 representation is enough, and you don't want to bloat your files with unused traces|
|**`inputPath`**|`{String}`|`''`|Image file location if exist or chained from another loader (ex: url-loader)|
|**`outputPath`**|`{String}`|`null` (required)|File JSON path|
|**`publicPath`**|`{String}`|`null`|Prepend dir to the file JSON path|
|**`file`**|`{String}`|`null (required)`|File JSON name|

[npm]: https://img.shields.io/npm/v/image-trace-loader.svg
[npm-url]: https://npmjs.com/package/image-trace-loader
[file-loader]: https://github.com/webpack-contrib/file-loader
[url-loader]: https://github.com/webpack-contrib/url-loader
[potrace-class]: https://github.com/tooolbox/node-potrace#parameters
[potrace-algorithm]: http://potrace.sourceforge.net/potrace.pdf
[multilevel-thresholding]: http://www.iis.sinica.edu.tw/page/jise/2001/200109_01.pdf
