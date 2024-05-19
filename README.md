# blurhash-js

> This project is based on [Dens49's blurhash-js](https://github.com/Dens49/blurhash-js), implemented with js class

## Usage

### Embedding

`<script src="blurhash.js"></script>`

### Decode

```javascript
const pixels = await BlurHash.decode(blurhash, width, height, punch);

const canvas = document.createElement("canvas");
const ctx = canvas.getContext("2d");
canvas.width = width;
canvas.height = height;
ctx.width = width;
ctx.height = height;
ctx.putImageData(new ImageData(pixels, width, height), 0, 0);

const img = document.getElementById("my-image");
img.src = canvas.toDataURL();
```

### Encode

```javascript
const img = document.getElementById("my-image");
img.onload = () => {
  const canvas = document.createElement("canvas");
  const ctx = canvas.getContext("2d");
  canvas.width = img.width;
  canvas.height = img.height;
  ctx.width = img.width;
  ctx.height = img.height;
  ctx.drawImage(img, 0, 0);
  const pixels = ctx.getImageData(0, 0, img.width, img.height).data;
  
  const hash = await BlurHash.encode(pixels, width, height, componentX, componentY);
}
```
