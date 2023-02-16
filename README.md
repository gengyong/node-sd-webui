# Node Stable Diffusion WebUI Client

A Node.js client for using Automatic1111's Stable Diffusion WebUI.

## Current Features

This project is a work in progress. The currently supported features are:

- txt2img generation

## Installation

Add `node-sd-webui` to your project.

Using npm:

```sh
npm i -S node-sd-webui
```

Using yarn:

```sh
yarn add node-sd-webui
```

Using pnpm:

```sh
pnpm add node-sd-webui
```

## Usage

### txt2img

The `txt2img` function allows you to generate an image using the `txt2img`
functionality of the Stable Diffusion WebUI.

Basic Example:

```js
import sdwebui from 'node-sd-webui'
import { writeFileSync } from 'fs'

sdwebui()
  .txt2img({
    prompt: 'A photo of a mushroom',
  })
  .then(({ images }) => writeFileSync('path/to/image.png', images[0], 'base64'))
  .catch((err) => console.error(err))
```

Another example with a few more options:

```js
import sdwebui from 'node-sd-webui'
import { writeFileSync } from 'fs'

sdwebui()
  .txt2img({
    prompt: 'A photo of a mushroom, red cap, white spots',
    negativePrompt: 'blurry, cartoon, drawing, illustration',
    samplingMethod: 'DPM++ 2M Karras',
    width: 768,
    height: 512,
    steps: 20,
    batchSize: 5,
  })
  .then(({ images }) => {
    images.forEach((image, i) =>
      imagwriteFileSync(`path/to/image-${i}.png`, images[i], 'base64')
    )
  })
  .catch((err) => console.error(err))
```