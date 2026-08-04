# AUTOSCOPY

Live webcam feed rendered as an ASCII relief. Luminance is treated as a heightfield, gradients are derived from it, and the resulting surface normals are relit with a virtual light source that orbits independently of the room's real lighting — which is what reads as depth rather than a brightness threshold.

Depth is estimated, not sensed. A single RGB camera has no depth channel. Three cues stand in for one:

- **Luminance** — front-lit features (nose, brow, cheekbones) are brightest because they're nearest the light.
- **Shape-from-shading** — luminance treated as a heightfield; per-cell surface normals relit against a virtual light.
- **Background subtraction** — a learned static frame, subtracted, isolates the figure from the room.

## Requirements

- A webcam
- A browser with `getUserMedia` support (any current Chrome, Edge, or Firefox)
- Python 3, for serving the file locally

That's the whole stack. There's no backend, no image-processing library, no build step — it's a single self-contained HTML file. Python's only job is running a static file server, because `getUserMedia` requires a secure context and refuses to run from `file://`.

## Running it

```
start.bat
```

or manually:

```
python -m http.server 8000
```

then open `http://localhost:8000/autoscopy.html`.

## Controls

| Key | Action |
|---|---|
| `1`–`5` | depth mode (luma / relief / foreground / edge / composite) |
| `B` | learn background (step out of frame first) |
| `M` | toggle mirror |
| `F` | fullscreen |

Sidebar sliders cover grid resolution, relief strength, light orbit speed and elevation, foreground isolation, edge definition, glyph set, contrast, gamma, and temporal smoothing.

## Notes

- All processing is local. No frame is ever transmitted anywhere.
- Camera resolution is requested at up to 1080p (`ideal`, not `exact` — lesser hardware still connects) with a frame-rate floor; if a device negotiates an unusably slow mode, it retries once at a conservative fallback resolution.
- Tested against a Logitech QuickCam Pro 9000 (UVC-class, 2008). Should scale cleanly to any UVC webcam — the processing cost is bound to the character grid, not the source resolution.
