# Crates Memo

- [crates.io](https://crates.io/): The Rust community’s crate registry.
- [docs.rs](https://docs.rs/): The Rust community’s documentation hosting service.
- [lib.rs](https://lib.rs/): A community maintained catalog of Rust crates and programs.
- [Rust Standard Library](https://doc.rust-lang.org/std/): The Rust Standard Library API documentation.

## Quality of Life

- [thiserror](https://lib.rs/crates/thiserror): `#[derive(Error)]` for defining custom error types.
- [anyhow](https://lib.rs/crates/anyhow): Flexible concrete Error type built on `std::error::Error`.
- [simplelog](https://lib.rs/crates/simplelog): Simple and easy-to-use logging facility.
- [fake](https://lib.rs/crates/fake): An easy to use library for generating fake data.

## Ex-Std

- [rand](https://lib.rs/crates/rand): Random number generators and other randomness functionality.
- [chrono](https://lib.rs/crates/chrono): Date and time library.
- [time](https://crates.io/crates/time): Date and time library.
- [log](https://lib.rs/crates/log): A lightweight logging facade.

## Proc Macros

- [syn](https://lib.rs/crates/syn): Parser for Rust source code.
- [quote](https://lib.rs/crates/quote): Quasi-quoting macro `quote!{}`.
- [proc-macro2](https://lib.rs/crates/proc-macro2): A substitute implementation of the compiler’s `proc_macro` API.
- [trybuild](https://lib.rs/crates/trybuild): Test harness for ui tests of compiler diagnostics

## Async

- [tokio](https://lib.rs/crates/tokio) ([website](https://tokio.rs/)): An asynchronous runtime for the Rust programming language.
- [smol](https://lib.rs/crates/smol): A small and fast async runtime.
- [futures](https://lib.rs/crates/futures): Foundations and utilities for asynchronous programming.
- [futures-lite](https://lib.rs/crates/futures-lite): A lightweight async prelude.

## Encoding

- [serde](https://lib.rs/crates/serde) ([website](https://serde.rs/)): A generic serialization/deserialization framework.
- [serde_json](https://lib.rs/crates/serde_json): JSON support for Serde.

## Rocket

- [rocket](https://lib.rs/crates/rocket) ([website](https://rocket.rs/)): Web framework for Rust.
- [rocket_ws](https://lib.rs/crates/rocket_ws): WebSockets support for Rocket.
- [rocket_db_pools](https://lib.rs/crates/rocket_db_pools): Rocket async database pooling support.
- [rocket_cors](https://lib.rs/crates/rocket_cors): Cross-origin resource sharing support for Rocket.
