# PULSE — procedural mesh synth

An audio-triggered 3D visualizer. PULSE listens to an audio input and, on every
pulse that crosses the threshold, re-rolls the whole scene: figure, mesh
density, formula coefficients, rotation, camera, replication layout and colour.
Between pulses the mesh spins on the rolled velocities.

Figures: superformula solids, harmonic spheres, noise-displaced tori and fields,
torus knots and box lattices, drawn as wireframes or point clouds.

Developed by **Sibilu**, 2026.

## Origin: visualizing Underrun triggers

PULSE was originally built to visualize the trigger outputs of **Underrun**.
Each trigger fires a pulse, and each pulse re-rolls the scene. Any audio
signal with clear transients will drive it too, from a mic, a drum machine or
a click track.

In the original setup, Underrun's trigger outs were patched into a VCA. The
VCA's level was turned right down, and its output went straight into an audio
interface input.

> [!WARNING]
> **I don't recommend copying this setup.** Eurorack trigger and gate signals
> are far hotter than the line level an audio interface expects. Patching them
> into a standard interface input can damage or destroy it. It only worked
> here with very careful level handling.
>
> Use a proper Eurorack audio interface or output module made to bring
> modular-level signals into a computer. Whatever you use, start with the
> level all the way down and bring it up slowly.

## Running it

It's a single HTML file (`pulse-synth.html`) with no build step. Browsers only
allow microphone access on `https://` or `http://localhost`, so opening the file
directly (`file://`) won't work. Serve the folder locally instead:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000/pulse-synth.html>, click **▶ start input** and
allow microphone access.
p5.js loads from a CDN, so you need an internet connection the first time.

It also works when hosted over HTTPS, for example with GitHub Pages.

## Controls

| Control | What it does |
| --- | --- |
| **src** / **ch** | Input device and channel (multi-channel interfaces are supported) |
| **polarity** | Fire on the rising (+) or falling (−) edge |
| **thresh** | Trigger level. It re-arms once the signal falls below half of this |
| **hold** | Minimum time between triggers, in ms |
| **figure** | Lock one figure, or pick a random one on each pulse |
| **render** | Wireframe, points, or random on each pulse |
| **color** | Colour theme. Each pulse draws a new colour from the theme |
| **complexity** | Upper limit on mesh resolution |
| **replicate** | Maximum copies in ring / grid / stack layouts |
| **rate** | Rotation speed |
| **chaos** | Amount of displacement and irregularity |
| **weight** | Line / point thickness |
| **zoom** / **camera** | Base zoom and camera dolly (0 = normal, 1 = inside the mesh) |
| **cam rand** | How far zoom and camera wander on each pulse |

Keyboard: **space** fires a manual pulse, **h** hides the panel, **f** toggles
fullscreen.

## Credit

If you use PULSE in a performance, video, installation or your own project, I'd
really appreciate a credit. Tag **@sibiluinstruments** on
[Instagram](https://www.instagram.com/sibiluinstruments/) or wherever you
post. This is a request, not a condition of the license.

## License

Released under the [MIT License](LICENSE). Copyright © 2026 Sibilu.

You're free to use, modify and redistribute this, including commercially,
as long as the copyright and license notice stay with the code. It comes with
no warranty.

### Third-party

PULSE uses [p5.js](https://p5js.org/) 1.9.4, which it loads from cdnjs at
runtime. p5.js isn't included in this repository. It is licensed separately
under the [GNU LGPL 2.1](https://github.com/processing/p5.js/blob/main/license.txt).
