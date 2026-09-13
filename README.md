# circle-progress.fscss

> Circular UI module for FSCSS — progress rings, pie charts, steps, multi-track, and themes.

**Circle Progress** is a pure-CSS circular component library built with FSCSS `@define`.  
It uses `conic-gradient`, CSS masks, and custom properties — no JavaScript required for rendering.

Compatible with **FSCSS v1.1.15+** (when `@define` shipped). Examples use the **1.2.1** runtime.
We are using runtime only for those examples

---

## Installation

**1. Include FSCSS**

HTML Example:
```html
<script src="https://cdn.jsdelivr.net/npm/fscss@1.2.1/runtime.min.js" defer></script>
```

**2. Import the module**

```css
/* classic init */
@import(exec(_init circle-progress))
```

```css
/* or selective / wildcard (1.1.16+) */
@import((*) from circle-progress)
```

---

## Quick start

[samples/example.html](samples/example.html)

```html
<script src="https://cdn.jsdelivr.net/npm/fscss@1.2.1/runtime.min.js" defer></script>

<style>
@import((*) from circle-progress)

@progress-root()
@circle-progress(.progress-circle)

.p72 { @progress-range(72) }
</style>

<div class="progress-circle p72">72%</div>
```

---

## Components

| Define | Role |
|--------|------|
| `@progress-root()` | Design tokens (size, stroke, colors, value) |
| `@circle-progress(sel)` | Donut progress ring + optional glow tip |
| `@circle-pie(sel)` | Solid pie slice |
| `@circle-pie-multi(sel)` | Multi-slice pie (`--pie-a` … `--pie-d`) |
| `@circle-steps(sel)` | Segmented steps ring |
| `@circle-multi(sel)` | Concentric multi-track scaffold |
| `@circle-bars-host(sel)` | Radial tick/bar host |

### Helpers

| Define | Purpose |
|--------|---------|
| `@progress-range(n)` | Set value 0–100 (`--progress-value`) |
| `@progress-size(px)` | Ring diameter |
| `@progress-stroke(px)` | Arc thickness |
| `@progress-animate(time)` | Transition on value change |
| `@progress-colors(arc, glow)` | Arc + glow colors |
| `@steps-done(n)` / `@steps-total(n)` | Steps ring counts |
| `@progress-theme-mint()` … `violet()` | One-call color themes |

---

## How the ring works

```css
background: conic-gradient(
  var(--progress-color-arc) calc(var(--progress-value) * 1%),
  var(--progress-color-track) 0%
);
```

A radial mask punches the center to form the donut.  
The tip marker is positioned with `transform: rotate(calc(var(--progress-value) * 3.6deg))`.

`--progress-value` replaces the older hashed token `--progress-6fb4d3f` (still written for back-compat).

---

## Customization

**Value**

```css
.p45 { @progress-range(45) }
.p88 { @progress-range(88) }
```

**Size & stroke**

```css
.big  { @progress-size(260px) }
.thin { @progress-stroke(8px) }
```

**Themes**

```css
.mint  { @progress-theme-mint() }
.blue  { @progress-theme-blue() }
.amber { @progress-theme-amber() }
.rose  { @progress-theme-rose() }
.violet { @progress-theme-violet() }
```

Or set variables directly:

```css
.custom {
  --progress-color-arc: #4d9fff;
  --progress-color-glow: rgba(77, 159, 255, 0.45);
}
```

**Steps**

```css
.s5 { @steps-done(5) @steps-total(8) }
```

```html
<div class="circle-steps s5">5/8</div>
```

**Multi pie**

```css
.pie-a {
  --pie-a: 30;
  --pie-b: 25;
  --pie-c: 20;
  --pie-d: 15;
}
```

```html
<div class="circle-pie-multi pie-a"></div>
```

---

## Nested rings

Compose by nesting elements and overriding size/stroke:

```html
<div class="progress-circle p72" style="--progress-size:200px">
  <div class="progress-circle p41" style="--progress-size:120px;--progress-stroke:10px">41</div>
</div>
```

---

## Complete example

```html
<!DOCTYPE html>
<html>
<head>
<script src="https://cdn.jsdelivr.net/npm/fscss@1.2.1/runtime.min.js" defer></script>
<style>
@import((*) from circle-progress)

@progress-root()
@circle-progress(.progress-circle)
@circle-pie(.circle-pie)
@circle-steps(.circle-steps)

body { background: var(--progress-color-bg); color: var(--progress-color-value); }

.p72 { @progress-range(72) }
.p30 { @progress-range(30) --progress-color-arc: #ff5070; }
.steps-5 { @steps-done(5) @steps-total(8) }
.big { @progress-size(220px) }
</style>
</head>
<body>
  <div class="progress-circle p72 big">72%</div>
  <div class="circle-pie p30">30%</div>
  <div class="circle-steps steps-5">5/8</div>
</body>
</html>
```

---

## Module info

| | |
|--|--|
| **Name** | circle-progress |
| **File** | `circle-progress.fscss` |
| **FSCSS** | `^1.1.15` (examples: 1.2.1) |
| **Type** | UI component library |
| **License** | MIT |

---

## Why this module?

| Feature | Benefit |
|---------|---------|
| No JavaScript | Pure CSS rendering |
| `@define` based | Reusable, composable |
| Multiple shapes | Ring, pie, steps, multi |
| Token-driven | Size, stroke, colors, value |
| Back-compatible | Works from FSCSS 1.1.15 up |

---

## Related

- [FSCSS Docs](https://fscss.devtem.org)
- [@define](https://fscss.devtem.org/define)
- [Arrays](https://fscss.devtem.org/arrays)
- [Events](https://fscss.devtem.org/event)
- [st-core.fscss](https://github.com/fscss-ttr/st-core.fscss)

---

## Changelog

### v2.0.0
- Expanded into a full circular UI module
- Added `@circle-pie`, `@circle-pie-multi`, `@circle-steps`, `@circle-multi`, `@circle-bars-host`
- Renamed progress token to `--progress-value` (legacy `--progress-6fb4d3f` still set)
- Theme helpers: mint, blue, amber, rose, violet
- Docs and examples target FSCSS 1.2.1 runtime; minimum remains 1.1.15

### v1.0.0 (FSCSS 1.1.15)
- Initial release: `@circle-progress`, range/size/stroke/animate helpers
- Conic-gradient ring + mask + glow tip

---

Made with ❤️ using FSCSS
