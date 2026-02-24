<h1 align="center">Game of Life</h1>

<p align="center">
  A clone of John Conway's Game of Life written in C and powered by SDL 2.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/language-C23-blue?style=flat-square&logo=c" alt="Language: C23" />
  <img src="https://img.shields.io/badge/graphics-SDL2-red?style=flat-square" alt="SDL2" />
  <img src="https://img.shields.io/badge/build-CMake-064F8C?style=flat-square&logo=cmake" alt="Build: CMake" />
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="License: MIT" />
  <img src="https://img.shields.io/badge/platform-Linux-FCC624?style=flat-square&logo=linux&logoColor=black" alt="Platform: Linux" />
</p>

<p align="center">
  <img src="https://github.com/DigitalCyan/game-of-life/blob/main/demo/gosper.gif?raw=true" />
</p>

---

## About

The Game of Life is a cellular automaton devised by mathematician John Conway (rest in peace) that
demonstrates how complex emergent behavior can arise from four simple rules:

1. Any live cell with **fewer than two** live neighbours dies — underpopulation.
2. Any live cell with **two or three** live neighbours survives to the next generation.
3. Any live cell with **more than three** live neighbours dies — overpopulation.
4. Any dead cell with **exactly three** live neighbours becomes alive — reproduction.

Despite these minimal rules the automaton is Turing-complete and capable of producing infinitely
varied patterns, including gliders, oscillators, and self-replicating structures.

---

## Features

- Real-time simulation rendered with SDL 2
- Interactive: place and erase cells with the mouse
- Configurable grid size, cell size, and simulation speed
- Lightweight — a single compiled binary plus an `assets/` folder

---

## Limitations

Unlike the theoretical original, this implementation runs on a **finite grid**. The world wraps at
its edges rather than extending infinitely. The grid dimensions are set at compile time via
`config.h` (see [Configuration](#configuration)).

---

## Dependencies

| Dependency | Purpose |
|---|---|
| SDL 2 | Window, rendering, input |
| SDL 2 TTF | Font/text rendering |

### Build-time only

| Tool | Purpose |
|---|---|
| GCC | C compiler |
| CMake | Build system generator |
| Make | Build executor |

---

## Satisfying Dependencies

**Debian / Ubuntu (apt):**
```shell
sudo apt install libsdl2-dev libsdl2-ttf-dev libsdl2-ttf-2.0-0 make cmake gcc
```

**Arch Linux (pacman):**
```shell
sudo pacman -S sdl2 sdl2_ttf cmake make gcc
```

**Fedora (dnf):**
```shell
sudo dnf install SDL2-devel SDL2_ttf-devel cmake make gcc
```

For other distributions, the packages are widely available under similar names.

---

## Building

```shell
git clone https://github.com/DigitalCyan/game-of-life --recurse-submodules
cd game-of-life
cmake -S . -B build && make --directory=build && cp -vr assets/ build/
```

The compiled binary and the `assets/` directory must live in the same folder — the binary looks
for assets relative to its own location.

---

## Configuration

Edit `src/include/config.h` before compiling to tune the simulation:

```c
#define WORLD_EDGE_SIZE 64   // Grid is WORLD_EDGE_SIZE × WORLD_EDGE_SIZE cells
#define CELL_SIZE       16   // Pixel size of each cell
#define THINK_DELAY     50   // Milliseconds between simulation ticks
```

> **Note:** `WINDOW_SIZE` is computed automatically from the values above — don't touch it.

---

## License

Distributed under the [MIT License](LICENSE). © 2023 DigitalCyan
