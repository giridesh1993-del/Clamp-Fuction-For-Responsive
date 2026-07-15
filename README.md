# clamp() Generator

An interactive tool for generating fluid, responsive CSS `clamp()` values — for `font-size`, `padding`, and `margin` — without doing the math by hand.

**[Live Demo](https://yourusername.github.io/repo-name/)** ← update this link once published

![clamp() generator screenshot](screenshot.png)
<!-- Add a screenshot to the repo and update the path above -->

## Why

Fluid typography and spacing with `clamp()` is powerful, but the formula behind it isn't obvious:

```css
font-size: clamp(1rem, 0.5rem + 1.5vw, 1.5rem);
```

This tool removes the manual calculation. Set your viewport range and either a minimum or maximum value, and the other side — along with the full `clamp()` expression — is generated for you.

## Features

- **Bidirectional calculation** — enter either MIN or MAX and the other value is calculated automatically, scaled to the same ratio as your viewport range
- **Works for any length-based property** — font-size, padding, and margin presets included (margin supports negative values)
- **px / rem toggle** for both value and output units
- **Live preview** with a draggable viewport-width slider to see the value scale in real time
- **One-click copy** of the generated `clamp()` string or full CSS declaration
- No build step, no dependencies — a single static HTML file

## Usage

1. Open the tool ([live demo](https://yourusername.github.io/repo-name/) or `index.html` locally)
2. Set your **viewport min/max** (required) — e.g. `1280px` to `1440px`
3. Enter a **MIN** or **MAX** value — the other is calculated for you
4. Choose the property tab (font-size / padding / margin) and px/rem unit
5. Copy the generated `clamp()` value or full CSS line
6. Drag the preview slider to confirm how it scales before using it

## How the calculation works

The minimum and maximum values scale at the same ratio as the viewport:

```
min = max × (viewportMin / viewportMax)
```

From there, the fluid `clamp()` value is built using the standard linear-interpolation formula:

```
slope = (max - min) / (viewportMax - viewportMin)
intersection = min - slope × viewportMin
clamp(min, intersection + slope × 100vw, max)
```

## Running locally

No build tools required — it's a single self-contained HTML file.

```bash
git clone https://github.com/yourusername/repo-name.git
cd repo-name
open index.html   # or just double-click the file
```

## Tech

Plain HTML, CSS, and vanilla JavaScript. No frameworks, no build step, no dependencies.

## License

MIT — free to use, modify, and distribute.

## Contributing

Issues and pull requests are welcome. If you spot a calculation edge case or have a feature idea, open an issue.
