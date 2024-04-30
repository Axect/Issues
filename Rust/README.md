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

* Add next line to your `.bashrc` or `.zshrc`

```sh
export LD_LIBRARY_PATH=/opt/OpenBLAS/lib/:$LD_LIBRARY_PATH
```

## Rust build script

* Create `build.rs` in your project
* Write next code to `build.rs`

```rust
fn main() {
    println!("cargo:rustc-link-search=/opt/OpenBLAS/lib");
    println!("cargo:rustc-link-lib=dylib=gfortran");
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

* I prefer `blas` (you can choose `cblas` too, but there are some bugs)

```toml
[dependencies]
blas = "0.20"
```

# Invalid H5_VERSION

## Error message

```sh
--- stderr
thread 'main' panicked at /home/[your_name]/.cargo/registry/src/[directory]/hdf5-sys-0.8.1/build.rs:200:21:
Invalid H5_VERSION: "1.14.3"
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
warning: build failed, waiting for other jobs to finish...
```

## Solution

- Fix `build.rs`

  ```rust
  let re = Regex::new(r"^(1)\.(8|10|12)\.(\d\d?)(_\d+)?(-patch\d+)?$").ok()?;
  ```

  ```rust
  let re = Regex::new(r"^(1)\.(8|10|12|14)\.(\d\d?)(_\d+)?(-patch\d+)?$").ok()?;
  ```

- Cargo clean

  ```sh
  cargo clean
  ```

- Re-build

  ```sh
  cargo build
  ```
