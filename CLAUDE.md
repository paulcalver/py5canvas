# py5canvas

Fork of https://github.com/colormotor/py5canvas — a Processing/p5js-style 2D drawing library for Python (pyCairo + moderngl/GLFW, optional slimgui GUI and OSC).

## Git remotes

- `origin` → https://github.com/paulcalver/py5canvas (my fork, push here)
- `upstream` → https://github.com/colormotor/py5canvas (original)
- Default branch is `main`. Pull updates with `git pull upstream main`.

## Environment

- Conda (Miniforge, installed via Homebrew) env named `py5`, Python 3.12, created from `environment.yaml`.
- py5canvas is installed editable (`pip install -e .`), so edits to `py5canvas/` take effect immediately.
- Extras installed: slimgui (GUI), python-osc (OSC), easydict, rumore, pyperclip, xdialog.
- Always activate first: `conda activate py5`. The system Python (3.9) is not used.
- Rebuild from scratch: `mamba env create --name py5 -f environment.yaml && conda activate py5 && pip install -e . python-osc`

## Running

- Interactive sketch (opens a window, live-reloads on save): `python examples/basic_animation.py`
- Notebook tutorial: `jupyter notebook examples/canvas_tutorial.ipynb`
- Sketch structure: `from py5canvas import *`, define `setup()` and `draw()`, end with `run()`.
- Verified working: `examples/basic_animation.py` runs and shows the orbiting circle.

## Sketch conventions

- Use `snake_case` (`create_canvas`, not `createCanvas`).
- Names like `scale`, `rotate` are injected canvas functions; don't reuse them as variables. Alternatively use `run(inject=False)` with `sketch.canvas`.
- Modifying a module-level variable inside `draw()` needs `global`, or keep state in an `EasyDict`/container.
- `parameters()` returning a dict auto-builds a GUI; values are available as `params.<lower_snake_name>` and auto-saved to a JSON next to the sketch.
- Settings are saved to `~/Library/Application Support/py5canvas/settings.json`.
- OSC: client on port 9998, server on 9999; define `received_osc(addr, value)` to handle messages.

## Layout

- `py5canvas/` — library source
- `examples/` — example sketches and notebook
- `docs/` — documentation
