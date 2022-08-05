# Plots

* Arch or Manjaro : Install `qt4`
  * Pamac: `pamac install qt4`
  * Pacman: `sudo pacman -S qt4`
  * yaourt: `yaourt -S qt4`

# Arpack (DifferentialEquations.jl)

* Arch or Manjaro : Install `arpack` & move `libarpack.so*` to `.julia/packages/Arpack/UiiMc/deps/usr/lib/`

# Sundials.jl (DifferentialEquations.jl)

## Error Message

```
LoadError: InitError: could not load library "/home/<USER>/.julia/artifacts/<SOME_CODES>/lib/libsundials_sunlinsollapackband.so"
libopenblas64_.so: cannot open shared object file: No such file or directory
```

## Solution

```sh
cd /home/<USER>/.julia/artifacts/<SOME_CODES>/lib/
ln -s /usr/lib/julia/libopenblas64_.so $PWD/libopenblas64_.so
```