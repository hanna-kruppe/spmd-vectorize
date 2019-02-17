# SPMD vectorization

This repository ties together the different components making up the SPMD vectorizer I created in the course of my B.Sc. thesis.
It is target-independent in principle, but has mostly been tested on the [Nyuzi processor][nyuzi-proc].

### Components

- A [fork of LLVM and Clang][nyuzi-toolchain], which mostly just adds the vectorization pass
- A [fork of the Rust compiler][rust-nyuzi], supporting the Nyuzi target and integrating the vectorization pass
- Some [benchmarks][benchmarks] that were used for performance evaluation

The LLVM and Rust forks are built exactly as the upstream projects, with the caveat that the Rust compiler needs to be pointed at a build of the forked LLVM (see `src/bootstrap/config.toml` in the Rust repository).
Running the benchmarks requires a simulator, which can be installed from the [Nyuzi repository][nyuzi-proc].
For the benchmarks written in Rust, cross compilation with the custom toolchain is managed via [Xargo][xargo], so you'll need that as well.

[benchmarks]: https://github.com/rkruppe/spmd-vectorize-benchmarks
[rust-nyuzi]: https://github.com/rkruppe/rust-nyuzi
[nyuzi-toolchain]: https://github.com/rkruppe/NyuziToolchain
[nyuzi-proc]: https://github.com/jbush001/NyuziProcessor/
[xargo]: https://github.com/japaric/xargo
