# circle-progress.fscss

> Animated circular progress component plugin for FSCSS (v1.1.15+)

**Circle Progress** is a reusable radial progress indicator built entirely with CSS and FSCSS plugin logic.
It uses conic-gradient, CSS masks, and custom properties to generate a smooth circular progress arc with an animated glowing indicator.

*No JavaScript required.*


---

## 📦 Installation

1. **Include FSCSS**

```html
<script src="https://cdn.jsdelivr.net/npm/fscss@1.1.20/exec.min.js" defer></script>
```

---

2. **Import the plugin**
```css
@import(exec(_init circle-progress))
```
**For FSCSS Version 1.1.16+:**
```css
@import((*) from circle-progress) 
```
---

### 🚀 Basic Usage

```html
<script src="https://cdn.jsdelivr.net/npm/fscss@1.1.20/exec.min.js" defer></script>

<style>
@import(exec(_init circle-progress))

@progress-root()

@circle-progress(.progress-circle)

.p72 {
  @progress-range(72)
}
</style>

<div class="progress-circle p72">72%</div>
```
This generates a circular progress arc representing 72%.


---

### ⚙️ How It Works

The component is built using CSS conic-gradient to draw the progress arc.

conic-gradient(
  var(--progress-color-arc) calc(var(--progress-value) * 1%),
  var(--progress-color-track) 0%
)

Then a radial mask creates the donut-shaped ring.

A glowing animated dot follows the progress arc using rotation transforms.


---

### 🎨 Customization

The plugin exposes multiple helpers for customization.


---

**Progress Value**
```css
.p45 { @progress-range(45) }
.p88 { @progress-range(88) }
.p30 { @progress-range(30) }
```

---

**Size**
```css
.big { @progress-size(260px) }
.small { @progress-size(120px) }
```

---

**Stroke Thickness**
```css
.thin { @progress-stroke(8px) }
.thick { @progress-stroke(20px) }
```

---

**Animation**
```css
.animate {
  @progress-animate(1s)
}
```
This smoothly animates progress changes.


---

**🎨 Color Variants**

Colors are controlled with CSS custom properties.

**Example:**
```css
.blue {
  --progress-color-arc: #4d9fff;
  --progress-color-glow: rgba(77,159,255,0.45);
}

.amber {
  --progress-color-arc: #ffb830;
  --progress-color-glow: rgba(255,184,48,0.4);
}

.rose {
  --progress-color-arc: #ff5070;
  --progress-color-glow: rgba(255,80,112,0.4);
}
```
**Usage:**
```html
<div class="progress-circle p45 blue">45%</div>
```

---

### 🌟 Complete Example
```html
<!DOCTYPE html>
<html>
<head>
<script src="https://cdn.jsdelivr.net/npm/fscss@1.1.20/exec.min.js" defer></script>

<style>
@import(exec(_init circle-progress))

@progress-root()

body{
  background: var(--progress-color-bg);
}

@circle-progress(.progress-circle)

.p72 { @progress-range(72) }
.big { @progress-size(240px) }
</style>
</head>

<body>

<div class="progress-circle p72 big">72%</div>

</body>
</html>
```

---

### 📁 Source Code

File: circle-progress.fscss
FSCSS Version: v1.1.15+

Repository:

https://github.com/fscss-ttr/FSCSS


---

### 🎨 Plugin Info


Name:	circle-progress
Extension:	.fscss
Directive:	`@circle-progress()`
Version:	1.1.15+
Dependencies:	FSCSS v1.1.15+
Type:	UI Component Plugin



---

## 💡 Why Circle Progress?

**Feature	Benefit**

No JavaScript	Pure CSS implementation
Reusable plugin	Initialize once, use anywhere
Customizable	Size, colors, stroke, animation
Lightweight	No external dependencies
FSCSS powered	Uses `@define` plugin system



---

## 📋 Summary

**Circle Progress** converts this simple FSCSS call:

`@circle-progress(.progress-circle)`

Into a fully animated circular progress component using advanced CSS features.

The plugin demonstrates how FSCSS can be used to create reusable UI components without JavaScript.


---

🔗 Related

FSCSS Docs: https://fscss.devtem.org

FSCSS @define: https://fscss.devtem.org/define

FSCSS Arrays: https://fscss.devtem.org/arrays

FSCSS @Event
https://fscss.devtem.org/event

---

📝 Changelog

v1.1.15 up

• Initial release
• Built with `@define` plugin system
• Supports size, stroke, and animation utilities
• Customizable color system via CSS variables


---

Made with ❤️ using FSCSS
