<p style="text-align:center;">
<img src="./github/readme-rec2.webp" style="border-radius: 20px;">
</p>

# Animation perf test

A tiny perf test for comparing browser animation techniques with a lot of moving & changing sizes items.

## Modes

| Mode                              | How it animates                  | Properties                  |
| --------------------------------- | -------------------------------- | --------------------------- |
| `js-style-transform`              | JS, every frame                  | `transform`                 |
| `js-animate-transform`            | Web Animations API               | `translate`, `scale`        |
| `css-animate-transform`           | CSS keyframes                    | `translate`, `scale`        |
| `js-style-pos`                    | JS, every frame                  | `left/top` + `width/height` |
| `css-animate-pos`                 | CSS keyframes                    | `left/top` + `width/height` |
| `js-style-margin`                 | JS, every frame                  | `margin` + `width/height`   |
| `css-animate-margin`              | CSS keyframes                    | `margin` + `width/height`   |
| `js-style-margin + forced reflow` | JS, layout read after each write | `margin` + `width/height`   |

## Measuring

- This page has no built-in fps counter on purpose. JS metrics like `requestAnimationFrame` deltas are unreliable here: they only measure the main thread, so they miss compositor-driven animations (transform, WAAPI, CSS keyframes).
- Use DevTools in you browser instead. In Chrome:
  - **Rendering → Frame Rendering Stats** for a live fps meter and GPU memory.
  - **Performance tab → Record** for the full breakdown of Recalculate Style, Layout, Paint and Composite, plus dropped frames.
- Run each mode for a few seconds before reading numbers, and compare at the same item count and window size.
