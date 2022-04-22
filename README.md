# wasm32-gsl

How to cross-compile and install [GSL](https://www.gnu.org/software/gsl/) for Emscripten.

## 1. Set up Emscripten

[Download, install, and activate Emscripten](https://emscripten.org/docs/getting_started/downloads.html)

On macOS, Emscripten is available through Homebrew.

## 2. Get the GSL code

Clone the GSL repository or download the code.

```bash
git clone git://git.savannah.gnu.org/gsl.git
```

## 3. Compile GSL with Emscripten

From an [answer on Stack Overflow](https://stackoverflow.com/a/67169806/1418500).

More info at [emscripten.org](https://emscripten.org/docs/compiling/Building-Projects.html#building-projects).

```bash
autoreconf -i -v
emconfigure ./configure --prefix=/usr/local/wasm32
emmake make LDFLAGS=-all-static
```

## 4. Install Emscripten

```bash
sudo emmake make install
```

## 5. Compile and run the example

The example in this project is copied from a GSL example.

Set up the Meson build, compile the example, and run the example.

```bash
meson --cross wasm32.ini build
ninja -C build
node build/newton.js
```

The output will be

```bash
using newton method
iter        root        err   err(est)
    1  3.0000000 +0.7639320 -2.0000000
    2  2.3333333 +0.0972654 -0.6666667
    3  2.2380952 +0.0020273 -0.0952381
Converged:
    4  2.2360689 +0.0000009 -0.0020263
```
