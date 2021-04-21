<div align="center">
    <img src="./.images/cargo-contract-color-clipped.svg" alt="ink!" height="170" />

[![GitLab Status](https://gitlab.parity.io/parity/cargo-contract/badges/master/pipeline.svg)](https://gitlab.parity.io/parity/cargo-contract/pipelines)
[![Latest Version](https://img.shields.io/crates/v/cargo-contract.svg)](https://crates.io/crates/cargo-contract)
[![GitHub license](https://img.shields.io/github/license/paritytech/cargo-contract)](LICENSE) 
[![Matrix][k1]][k2]
[![Discord][l1]][l2]

[k1]: https://img.shields.io/badge/matrix-chat-brightgreen.svg?style=flat
[k2]: https://riot.im/app/#/room/#ink:matrix.parity.io
[l1]: https://img.shields.io/discord/722223075629727774?style=flat-square&label=discord
[l2]: https://discord.gg/ztCASQE

<p align="center">

> <img src="./.images/ink-squid.svg" alt="squink, the ink! mascot" style="vertical-align: middle" align="left" height="60" />`cargo-contract` is a CLI tool which helps you develop smart contracts in Parity's <a href="https://github.com/paritytech/ink">ink!</a>.<br/><br/>ink! is a Rust [eDSL](https://wiki.haskell.org/Embedded_domain_specific_language) which allows you to write smart contracts for blockchains built on the [Substrate](https://github.com/paritytech/substrate) framework.
</p>
</div>

<br/>


## Installation

`rust-src` is a prerequisite: `rustup component add rust-src`.

`binaryen` is a prerequisite as well, we use it for optimizing the contract Wasm. 

Install [`binaryen`](https://github.com/WebAssembly/binaryen#tools) with a version >= 99.
Many package managers have it available nowadays:

* [Debian/Ubuntu](https://tracker.debian.org/pkg/binaryen): `apt-get install binaryen`
* [Homebrew](https://formulae.brew.sh/formula/binaryen): `brew install binaryen`
* [Arch Linux](https://archlinux.org/packages/community/x86_64/binaryen/): `pacman -S binaryen`
* Windows: [binary releases are available](https://github.com/WebAssembly/binaryen/releases)
  
After you've installed the package execute `cargo install --force cargo-contract`.

## Usage

```
cargo-contract 0.11.1
Utilities to develop Wasm smart contracts

USAGE:
    cargo contract <SUBCOMMAND>

OPTIONS:
    -h, --help       Prints help information
    -V, --version    Prints version information

SUBCOMMANDS:
    new                  Setup and create a new smart contract project
    build                Compiles the contract, generates metadata, bundles
                         both together in a `<name>.contract` file
    generate-metadata    Command has been deprecated, use `cargo contract build` instead
    check                Check that the code builds as Wasm; does not output any
                         `<name>.contract` artifact to the `target/` directory
    test                 Test the smart contract off-chain
    deploy               Upload the smart contract code to the chain
    instantiate          Instantiate a deployed smart contract
    help                 Prints this message or the help of the given subcommand(s)
```

## `build` requires the `nightly` toolchain

`cargo contract build` must be run using the `nightly` toolchain. If you have 
[`rustup`](https://github.com/rust-lang/rustup) installed, the simplest way to do so is `cargo +nightly contract build`.
To avoid having to add `+nightly` you can also create a `rust-toolchain` file in your local directory containing 
`nightly`. Read more about how to [specify the rustup toolchain](https://github.com/rust-lang/rustup#override-precedence).

### Note 

The latest version of `cargo-contract` supports all nightlies after `2020-07-30`, because of a change in the directory
structure of the `rust-src` component. 

## Features

The `deploy` and `instantiate` subcommands are **disabled by default**, since they are not fully stable yet and increase the build time.

If you want to try them, you need to enable the `extrinsics` feature:

`cargo install --git https://github.com/paritytech/cargo-contract cargo-contract --features extrinsics --force`

Once they are stable and the compilation time is acceptable, we will consider removing the `extrinsics` feature.

## License

The entire code within this repository is licensed under the [GPLv3](LICENSE). Please [contact us](https://www.parity.io/contact/) if you have questions about the licensing of our products.

