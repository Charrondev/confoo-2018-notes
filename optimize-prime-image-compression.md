# Optimize Prime: More Pixels than meet the eye

_Henri_ **@HenriHelvetica**

## Why optimize images

- For user experience.

  > 53% of visitors" will abadon a page that takes 3 seconds or more to load

- The mobile antenna takes ~1 second to wake from sleep, leaving you with ~1 second.

- LTE, 4g, 3g aren't to be trusted. There is also network throttling.

- 72% of pages send desktop assets to mobile.

- 7% of sites are at least 2x smaller on mobile.

- SEO.

  > We should not be optimising for $3000 computers with fast connections.

- Images use up a lot processing power and memory. Out-of-memory erros are very common in low end devices, and the the #1 culprit is images.

### Memory

```
height * width * 4 * (rgba)
500 * 500 * 4 = 1,000,000 bytes
```

### Battery

> The amount of energy used to render images is proportional to the number and size of images on the page.

## The Known Targets

### GIF

- Oldest format.
- Raster format.
- Lossless + lossy optimizations.
- Extremely well supported.
- Transparent or not (no alpha channel).
- Known for bloat.
- More known for animations*.
- ~~Ironically fading in popularity.~~
- Being replaced by H.264 mp4.
- Antiquated.
- ~~*Completely useless format\**.~~

### PNG

- Dates from 1996.
- Raster format.
- Lossless + lossy compression.
- Alpha channel (transparency).
- Phenomenal support.
- Popular format.
- Animations via APNG.
- Varying bit depths (PNG8 vs PNG24).
- Contains EXIF data.

### SVG

- Dates from 1999.
- Vector format.
- Amazing for logos, icons, some illustrations.
- Fantastic support.
- Animations.
- Compresses well via gzip/brottli.
- More compression via SVGO/SVGOMG.
- Growing in popularity*.
- Resolution independant*.

### WEBP

- Dates from 2010.
- Google technology.
- Lossy and Lossless compression.
- Alpha channel (transparent).
- Animations.
- Poor support currently (Chrome only, Firefox implementing Mozilla@Bugzilla#856375).
- Not many encoding tools.
- Fantastic data savings over JPG and PNG.
- Promosing future*.

### JPG

- Dates from 1992.
- Lossy + Lossless raster format.
- Pristine support.
- By far the most common web format.
- The most common format used by cameras.
- Best for actual photographs.
- Contains EXIF data.
- Capable of extreme expressions.
- Friendliest computationally.
- Propriatary varients.

#### EXIF (Exchangable Image File Format) Data

Over 5092 distinct metadata fields across a collection of images.

On average EXIF data makes up 16% of JPEG size.

#### Chroma subsampling

Eyes are more sensitive to light than color, so we can eleminate some color information. 4:4:4 is no information loss. 

- YCbCr 4:4:4
- YCbCr 4:2:2
- YCbCr 4:2:0
- YCbCr 4:1:0

## The Solutions

- Leverage the strength of each image format and the available tools.
- Incorporate `webp` into your solution.
  - Chrome + Samsung Internet + Opera + Firefox + UC Browser on mobile are 65% of market and all support `webp`.
- Use the `<picture>` element to serve different types of images to different browsers that support different formats and sizes.
- Design Direction
  - Smaller colour palettes and lower contrast lead to more compressable data.
- Lazy load
  - On average 2/3s of page is out of the view port.
  - Only about 50% of users scroll to the bottom.

### Tools

- NCC image checker (chrome plugin).
- RespImageLint - Linter for responsive images.
- Chrome Devtools
  - Lighthouse - Auditing tool in chrome dev tools.
- https://webpagetest.org
- ImageOptim (compressor with GUI and CLI).
- https://responsivebreakpoints.com - Responsive image breakpoint generator.
- https://image.guide