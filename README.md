![Git Version](https://img.shields.io/github/package-json/v/vladmandic/face-api?style=flat-square&svg=true&label=git)
![NPM Version](https://img.shields.io/npm/v/@vladmandic/face-api.png?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/vladmandic/face-api?style=flat-square?svg=true)
![License](https://img.shields.io/github/license/vladmandic/face-api?style=flat-square?svg=true)
![GitHub Status Checks](https://img.shields.io/github/checks-status/vladmandic/face-api/master?style=flat-square?svg=true)
![Vulnerabilities](https://img.shields.io/snyk/vulnerabilities/github/vladmandic/face-api?style=flat-square?svg=true)

# FaceAPI

**AI-powered Face Detection & Rotation Tracking, Face Description & Recognition, Age & Gender & Emotion Prediction for Browser and NodeJS using TensorFlow/JS**

<br>

**Live Demo**: <https://vladmandic.github.io/face-api/demo/webcam.html>

<br>

## Additional Documentation

- [**Tutorial**](TUTORIAL.md)


<br><hr><br>

## Examples

<br>

### Browser

Browser example that uses static images and showcases both models  
as well as all of the extensions is included in `/demo/index.html`  
Example can be accessed directly using Git pages using URL:  
<https://vladmandic.github.io/face-api/demo/index.html>  

Browser example that uses live webcam is included in `/demo/webcam.html`  
Example can be accessed directly using Git pages using URL:  
<https://vladmandic.github.io/face-api/demo/webcam.html>  


<br>

**Demo using FaceAPI to process images**  
*Note: Photos shown below are taken by me*

![facemesh](https://github.com/ChetaN7895/Face-Api/assets/151900157/5127a90a-7dbc-42d2-9761-3ddc870543fb)
![sample1](https://github.com/ChetaN7895/Face-Api/assets/151900157/b8870143-6d45-4b11-aff0-87c996df42f8)
![screenshot-images~2](https://github.com/ChetaN7895/Face-Api/assets/151900157/e1a1fe8c-cb90-439e-a1ca-68f4bf5efa38)

**Demo using FaceAPI to process live webcam**  


![screenshot-images~3](https://github.com/ChetaN7895/Face-Api/assets/151900157/b47f09f1-0fb7-451a-a922-18aeb68d3aca)

![screenshot-webcam](https://github.com/ChetaN7895/Face-Api/assets/151900157/0805dc92-94eb-4c9a-8770-f794500f508f)

<br>

### NodeJS

NodeJS examples are:

- `/demo/node-simple.js`:
  Simplest possible NodeJS demo for FaceAPI in under 30 lines of JavaScript code  
- `/demo/node.js`:  
  Using `TFJS` native methods to load images without external dependencies  
- `/demo/node-canvas.js` and `/demo/node-image.js`:  
  Using external `canvas` module to load images  
  Which also allows for image drawing and saving inside `NodeJS` environment  
- `/demo/node-match.js`:  
  Simple demo that compares face similarity from a given image  
  to a second image or list of images in a folder  
- `/demo/node-multiprocess.js`:  
  Multiprocessing showcase that uses pool of worker processes  
  (`node-multiprocess-worker.js`)  
  Main starts fixed pool of worker processes with each worker having  
  it's instance of `FaceAPI`  
  Workers communicate with main when they are ready and main dispaches  
  job to each ready worker until job queue is empty  

```json


Note that `@tensorflow/tfjs-node` or `@tensorflow/tfjs-node-gpu`  
must be installed before using any **NodeJS** examples

<br><hr><br>

## Quick Start

Simply include latest version of `FaceAPI` directly from a CDN in your HTML:  
(pick one, `jsdelivr` or `unpkg`)

```html
<script src="https://cdn.jsdelivr.net/npm/@vladmandic/face-api/dist/face-api.js"></script>
<script src="https://unpkg.dev/@vladmandic/face-api/dist/face-api.js"></script>
```

## Installation

`FaceAPI` ships with several pre-build versions of the library:

- `dist/face-api.js`: IIFE format for client-side Browser execution  
   *with* TFJS pre-bundled
- `dist/face-api.esm.js`: ESM format for client-side Browser execution  
   *with* TFJS pre-bundled
- `dist/face-api.esm-nobundle.js`: ESM format for client-side Browser execution  
   *without* TFJS pre-bundled
- `dist/face-api.node.js`: CommonJS format for server-side NodeJS execution  
   *without* TFJS pre-bundled
- `dist/face-api.node-gpu.js`: CommonJS format for server-side NodeJS execution  
   *without* TFJS pre-bundled and optimized for CUDA GPU acceleration

Defaults are:

```json
{
  "main": "dist/face-api.node-js",
  "module": "dist/face-api.esm.js",
  "browser": "dist/face-api.esm.js",
}
```

Bundled `TFJS` can be used directly via export: `faceapi.tf`

Reason for additional `nobundle` version is if you want to  
include a specific version of TFJS and not rely on  pre-packaged one  

`FaceAPI` is compatible with TFJS 2.0+ and TFJS 3.0+  

All versions include `sourcemap`

<br><hr><br>

There are several ways to use FaceAPI:

### 1. IIFE script

*Recommened for quick tests and backward compatibility with older Browsers that do not support ESM such as IE*

This is simplest way for usage within Browser  
Simply download `dist/face-api.js`, include it in your `HTML` file & it's ready to use:

```html
<script src="dist/face-api.js"><script>
```

Or skip the download and include it directly from a CDN:

```html
<script src="https://cdn.jsdelivr.net/npm/@vladmandic/face-api/dist/face-api.js"></script>
```

IIFE script bundles TFJS and auto-registers global namespace `faceapi` within Window object which can be accessed directly from a `<script>` tag or from your JS file.  

<br>

### 2. ESM module

*Recommended for usage within Browser*

#### 2.1. Direct Import

To use ESM import directly in a Browser, you must import your script (e.g. `index.js`) with a `type="module"`  

```html
  <script src="./index.js" type="module">
```

and then in your `index.js`

```js
  import * as faceapi from 'dist/face-api.esm.js';
```

#### 2.2. With Bundler

Same as above, but expectation is that you've installed `@vladmandic/faceapi` package:

```shell
  npm install @vladmandic/face-api 
```

and that you'll package your application using a bundler such as `webpack`, `rollup` or `esbuild`  
in which case, you do not need to import a script as module - that depends on your bundler configuration  

```js
  import * as faceapi from '@vladmandic/face-api';
```

or if your bundler doesn't recognize `recommended` type, force usage with:

```js
  import * as faceapi from '@vladmandic/face-api/dist/face-api.esm.js';
```

or to use non-bundled version

```js
  import * as tf from `@tensorflow/tfjs`;
  import * as faceapi from '@vladmandic/face-api/dist/face-api.esm-nobundle.js';
```

<br>

### 3. NPM module

#### 3.1. Import CommonJS

*Recommended for NodeJS projects*

*Node: FaceAPI for NodeJS does not bundle TFJS due to binary dependencies that are installed during TFJS installation*

Install with:

```shell
  npm install @tensorflow/tfjs-node
  npm install @vladmandic/face-api 
```

And then use with:

```js
  const tf = require('@tensorflow/tfjs-node')
  const faceapi = require('@vladmandic/face-api');
```

If you want to force CommonJS module instead of relying on `recommended` field:

```js
  const faceapi = require('@vladmandic/face-api/dist/face-api.node.js');
```

If you want to GPU Accelerated execution in NodeJS, you must have CUDA libraries already installed and working  
Then install appropriate version of `FaceAPI`:

```shell
  npm install @tensorflow/tfjs-node-gpu
  npm install @vladmandic/face-api 
```

And then use with:

```js
  const tf = require('@tensorflow/tfjs-node-gpu')
  const faceapi = require('@vladmandic/face-api/dist/face-api.node-gpu.js'); // this loads face-api version with correct bindings for tfjs-node-gpu
```

If you want to use `FaceAPI` in a NodeJS on platforms where **tensorflow** binary libraries are not supported, you can use NodeJS **WASM** backend.  

```shell
  npm install @tensorflow/tfjs
  npm install @tensorflow/tfjs-backend-wasm
  npm install @vladmandic/face-api 
```

And then use with:

```js
  const tf = require('@tensorflow/tfjs');
  const wasm = require('@tensorflow/tfjs-backend-wasm');
  const faceapi = require('@vladmandic/face-api/dist/face-api.node-wasm.js'); // use this when using face-api in dev mode
  wasm.setWasmPaths('https://cdn.jsdelivr.net/npm/@tensorflow/tfjs-backend-wasm/dist/');
  await tf.setBackend('wasm');
  await tf.ready();
  ...
```

If you want to use graphical functions inside NodeJS,  
you must provide appropriate graphical library as  
NodeJS does not include implementation for DOM elements  
such as HTMLImageElement or HTMLCanvasElement:

Install `Canvas` for NodeJS:

```shell
npm install canvas
```

Patch NodeJS environment to use newly installed `Canvas` library:

```js
const canvas = require('canvas');
const faceapi = require('@vladmandic/face-api');

const { Canvas, Image, ImageData } = canvas
faceapi.env.monkeyPatch({ Canvas, Image, ImageData })
```

<br><hr><br>

## Weights

Pretrained models and their weights are included in `./model`.

<br><hr><br>

## Test & Dev Web Server

To install development dependencies, use `npm install --production=false`

Built-in test&dev web server can be started using

```shell
npm run dev
```

By default it starts HTTP server on port 8000 and HTTPS server on port 8001 and can be accessed as:  

- <https://localhost:8001/demo/index.html>
- <https://localhost:8001/demo/webcam.html>

```js

npm install @vladmandic/face-api
cd node_modules/@vladmandic/face-api
```

or clone a git project

```shell
git clone https://github.com/vladmandic/face-api
cd face-api
```

Then install all dependencies and run rebuild:

```shell
npm install --production=false
npm run build
```

Build process uses `@vladmandic/build` module that creates optimized build for each target:

```js
> @vladmandic/face-api@1.7.1 build /home/vlado/dev/face-api
> node build.js

 08:21:05 INFO:  Environment: { profile: 'production', config: '.build.json', package: 'package.json', tsconfig: true, eslintrc: true, git: true }
 08:21:05 INFO:  Toolchain: { build: '0.7.7', esbuild: '0.14.50', typescript: '4.7.4', typedoc: '0.23.9', eslint: '8.20.0' }
 08:21:05 INFO:  Build: { profile: 'production', steps: [ 'clean', 'compile', 'typings', 'typedoc', 'lint', 'changelog' ] }
5 08:21:05 STATE: Clean: { locations: [ 'dist/*', 'typedoc/*', 'types/lib/src' ] }
 08:21:05 STATE: Compile: { name: 'tfjs/node/cpu', format: 'cjs', platform: 'node', input: 'src/tfjs/tf-node.ts', output: 'dist/tfjs.esm.js', files: 1, inputBytes: 143, outputBytes: 614 }
08:21:05 STATE: Compile: { name: 'faceapi/node/cpu', format: 'cjs', platform: 'node', input: 'src/index.ts', output: 'dist/face-api.node.js', files: 162, inputBytes: 234137, outputBytes: 85701 }
2 08:21:05 STATE: Compile: { name: 'tfjs/node/gpu', format: 'cjs', platform: 'node', input: 'src/tfjs/tf-node-gpu.ts', output: 'dist/tfjs.esm.js', files: 1, inputBytes: 147, outputBytes: 618 }
 08:21:05 STATE: Compile: { name: 'faceapi/node/gpu', format: 'cjs', platform: 'node', input: 'src/index.ts', output: 'dist/face-api.node-gpu.js', files: 162, inputBytes: 234141, outputBytes: 85705 }
 08:21:05 STATE: Compile: { name: 'tfjs/node/wasm', format: 'cjs', platform: 'node', input: 'src/tfjs/tf-node-wasm.ts', output: 'dist/tfjs.esm.js', files: 1, inputBytes: 185, outputBytes: 670 }
08:21:05 STATE: Compile: { name: 'faceapi/node/wasm', format: 'cjs', platform: 'node', input: 'src/index.ts', output: 'dist/face-api.node-wasm.js', files: 162, inputBytes: 234193, outputBytes: 85755 }
 08:21:05 STATE: Compile: { name: 'tfjs/browser/tf-version', format: 'esm', platform: 'browser', input: 'src/tfjs/tf-version.ts', output: 'dist/tfjs.version.js', files: 1, inputBytes: 1063, outputBytes: 400 }
208:21:05 STATE: Compile: { name: 'tfjs/browser/esm/nobundle', format: 'esm', platform: 'browser', input: 'src/tfjs/tf-browser.ts', output: 'dist/tfjs.esm.js', files: 2, inputBytes: 910, outputBytes: 527 }
5 08:21:05 STATE: Compile: { name: 'faceapi/browser/esm/nobundle', format: 'esm', platform: 'browser', input: 'src/index.ts', output: 'dist/face-api.esm-nobundle.js', files: 162, inputBytes: 234050, outputBytes: 82787 }
 08:21:05 STATE: Compile: { name: 'tfjs/browser/esm/bundle', format: 'esm', platform: 'browser', input: 'src/tfjs/tf-browser.ts', output: 'dist/tfjs.esm.js', files: 11, inputBytes: 910, outputBytes: 1184871 }
2022-07-25 08:21:05 STATE: Compile: { name: 'faceapi/browser/iife/bundle', format: 'iife', platform: 'browser', input: 'src/index.ts', output: 'dist/face-api.js', files: 162, inputBytes: 1418394, outputBytes: 1264631 }
 08:21:05 STATE: Compile: { name: 'faceapi/browser/esm/bundle', format: 'esm', platform: 'browser', input: 'src/index.ts', output: 'dist/face-api.esm.js', files: 162, inputBytes: 1418394, outputBytes: 1264150 }
 08:21:07 STATE: Typings: { input: 'src/index.ts', output: 'types/lib', files: 93 }
2 08:21:09 STATE: TypeDoc: { input: 'src/index.ts', output: 'typedoc', objects: 154, generated: true }
2 08:21:13 STATE: Lint: { locations: [ 'src/' ], files: 174, errors: 0, warnings: 0 }
 08:21:14 STATE: ChangeLog: { repository: 'https://github.com/vladmandic/face-api', branch: 'master', output: 'CHANGELOG.md' }
 08:21:14 INFO:  Done...
25 08:21:14 STATE: Copy: { input: 'types/lib/dist/tfjs.esm.d.ts' }
5 08:21:15 STATE: API-Extractor: { succeeeded: true, errors: 0, warnings: 417 }
5 08:21:15 INFO:  FaceAPI Build complete...
```

<br><hr><br>

## Face Mesh

`FaceAPI` landmark model returns 68-point face mesh as detailed in the image below:

![facemesh](demo/facemesh.png)

<br><hr><br>

## Note

This is updated **face-api.js** with latest available TensorFlow/JS as the original is not compatible with **tfjs >=2.0**.  
Forked from [face-api.js](https://github.com/justadudewhohacks/face-api.js) version **0.22.2** which was released on March 22nd, 2020  

*Why?* I needed a FaceAPI that does not cause version conflict with newer versions of TensorFlow  
And since the original FaceAPI was open-source, I've released this version as well  

Changes ended up being too large for a simple pull request and it ended up being a full-fledged version on its own  
Plus many features were added since the original inception  

Although a lot of work has gone into this version of `FaceAPI` and it will continue to be maintained,  
at this time it is completely superseded by my newer library `Human` which covers the same use cases,  
but extends it with newer AI models, additional detection details, compatibility with latest web standard and more


<br>

## Differences

Compared to [face-api.js](https://github.com/justadudewhohacks/face-api.js) version **0.22.2**:

- Compatible with `TensorFlow/JS 2.0+, 3.0+ and 4.0+`  
  Currently using **`TensorFlow/JS` 4.16**  
  Original `face-api.js` is based on `TFJS` **1.7.4**  
- Compatible with `WebGL`, `CPU` and `WASM` TFJS Browser backends  
- Compatible with both `tfjs-node` and `tfjs-node-gpu` TFJS NodeJS backends  
- Updated all type castings for TypeScript type checking to `TypeScript 5.3`  
- Switched bundling from `UMD` to `ESM` + `CommonJS` with fallback to `IIFE`  
  Resulting code is optimized per-platform instead of being universal  
  Fully tree shakable when imported as an `ESM` module  
  Browser bundle process uses `ESBuild` instead of `Rollup`  
- Added separate `face-api` versions with `tfjs` pre-bundled and without `tfjs`  
  When using `-nobundle` version, user can load any version of `tfjs` manually  
- Typescript build process now targets `ES2018` and instead of dual `ES5`/`ES6`  
  Resulting code is clean ES2018 JavaScript without polyfills  
- Removed old tests, docs, examples  
- Removed old package dependencies (`karma`, `jasmine`, `babel`, etc.)  
- Updated all package dependencies  
- Updated TensorFlow/JS dependencies since backends were removed from `@tensorflow/tfjs-core`  
- Updated `mobileNetv1` model due to `batchNorm()` dependency  
- Added `version` class that returns JSON object with version of FaceAPI as well as linked TFJS  
- Added test/dev built-in HTTP & HTTPS Web server  
- Removed `mtcnn` and `tinyYolov2` models as they were non-functional in latest public version of `FaceAPI`  
  Which means valid models are **tinyFaceDetector** and **mobileNetv1**  
  *If there is a demand, I can re-implement them back.*  
- Added `face angle` calculations that returns `roll`, `yaw` and `pitch`  
- Added `typdoc` automatic API specification generation during build  
- Added `changelog` automatic generation during build  
- New process to generate **TypeDocs** bundle using API-Extractor

<br>

## Credits

- Original project: [face-api.js](https://github.com/justadudewhohacks/face-api.js)
- Original model weighs: [face-api.js-models](https://github.com/justadudewhohacks/face-api.js-models)
- ML API Documentation: [Tensorflow/JS](https://js.tensorflow.org/api/latest/)

<br>

![Stars](https://img.shields.io/github/stars/vladmandic/face-api?style=flat-square?svg=true)
![Forks](https://badgen.net/github/forks/vladmandic/face-api)
![Code Size](https://img.shields.io/github/languages/code-size/vladmandic/face-api?style=flat-square?svg=true)
![CDN](https://data.jsdelivr.com/v1/package/npm/@vladmandic/face-api/badge)<br>
![Downloads](https://img.shields.io/npm/dw/@vladmandic/face-api.png?style=flat-square)
![Downloads](https://img.shields.io/npm/dm/@vladmandic/face-api.png?style=flat-square)
![Downloads](https://img.shields.io/npm/dy/@vladmandic/face-api.png?style=flat-square)
