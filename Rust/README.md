# OpenBLAS for Rust

## Prerequisites

* `gcc`
* `gfortran`

## Setup OpenBLAS

* Install `OpenBLAS`

```sh
# Clone
git clone https://github.com/xianyi/OpenBLAS

# Make
cd OpenBLAS && make

# Install to /opt/OpenBLAS
sudo make install
```

## Rust build script

* Create `build.rs` in your project
* Write next code to `build.rs`

```rust
fn main() {
    println!("cargo:rustc-link-search=/opt/OpenBLAS/lib");
    pritnln!("cargo:rustc-link-lib=dylib=gfortran");
    println!("cargo:rustc-link-lib=dylib=openblas");
}
```

## **[Important]** Link OpenBLAS lib to Rust lib

* Find your rustlib directory
    * In my way, install `fd` & type command `fd -H rustlib`
    * In my case, the directory is `$HOME/.rustup/toolchains/nightly-x86_64-unknown-linux-gnu/lib/rustlib`
* Follow below codes

```sh
# Replace /path/to/rustlib to your rustlib directory
# Replace /your_target your target (In my case, x86_64-unknown-linux-gnu)
cd /path/to/rustlib/your_target/lib

ln -s /opt/OpenBLAS/lib/libopenblas.so $PWD/libopenblas.so
ln -s /opt/OpenBLAS/lib/libopenblas.so.0 $PWD/libopenblas.so.0
ln -s /opt/OpenBLAS/lib/libopenblas.a $PWD/libopenblas.a
```

## Edit Cargo.toml

* I prefer `cblas` (you can choose `blas` too)

```toml
[dependencies]
cblas = "0.2"
```
