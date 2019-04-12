
class: center, middle

# GIFs in Go
.cols[
.left-col[
.left[<img src="avatar.png"width="200" />]
.left[**Go Discord**: @cegal]
.left[**GitHub**: @CamiloGarciaLaRotta]
]

.righ-col[
.right[<img src="dancing-gopher.gif" width="160" />]
.right[thanks @egonelbre]
]
]

???
just graduated in Software Engineering  
have been tinkering in Go for about 2 years

I am available on the go discord channel  
and you can find me on GitHub by my full name 

This talk is about the strenghts and weaknesses of multiple gif libraries in Go

---

# Background

???
I wrote a program a while back called gifhub  
A single example will clarify what it does

It follows the pipeline design for concurrency  
a stage for concurrently scraping the user profile for each year  
some stages to generate a graph
and a sink stage to bundle all frames into a GIF

--

### GifHub
.left[
.footnote[
tiny.cc/gifhub
]
]
--
.cols[
.left-col[
.center[<img src="campoy.gif" width="300" />]
]
.right-col[
```bash
gifhub -d 40 campoy
```
#### Dependencies
- urfave/cli
- ImageMagick  
  `SVG -> JPG -> GIF`
]
]

---
# Background

### The Problem

???
Thanks to the Discord chat who pointed this out to me  
I decided to release a new version without ImageMagick

--

Windows and OSX users must use containerized version

--

But more importantly...

--

<img src="imagemagick-cve.png" width="100%" />

---

# Playground

All the code can be found in the `gif-playground` branch

.left[
.footnote[
tiny.cc/gifhub
]
]
--
.left[### Libraries Explored]
.cols[
.left-column[
- image/gif (standard lib)
- llgcode/draw2d
- peterhellberg/gfx
- fogleman/gg
]
.right-column[
.no-bullet[
- `tiny.cc/stdlib`
- `tiny.cc/draw2d`
- `tiny.cc/gfx`
- `tiny.cc/gg`
]
]
]

---

# image/gif

---

# llgcode/draw2d

---

# peterhellberg/gfx

---

# fogleman/gg

---

# Removing Imagemagick for fogleman/gg
TODO: time both versions of gifhub
- no io wait, file creation, garbage collection

---

# Take Aways
- Removing non-Go dependencies is not always a question of fanatism. Its a way to ensure cross-platform apps. 
- stdlib is great, but for image manipulation user libs are better
- dont be afraid to look under the hood to understand how stdlib works
