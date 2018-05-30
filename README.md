# Rust on AWS Lambda

This repository contains multiple crates that make it possible to run programs written in Rust directly as functions in AWS Lambda, while keeping a low footprint with regards to memory consumption, bundle size, and start-up speed.

## Usage

### Install

Because this project is still in an early (but functional!) stage, it has not yet been published to the `crates` registry. You will therefore need to depend directly on the Github repository. Add the following to the `[dependencies]` section in your `Cargo.toml` file.

```toml
aws_lambda_runtime = { git = "https://github.com/srijs/rust-aws-lambda" }
```

### Create

The `aws_lamba_runtime` crate provides a runtime environment which will listen for messages from the lambda environment, and call a function every time the lambda is invoked. This function can be async, as the runtime itself is based on top of `futures` and `tokio`.

```rust
extern crate aws_lambda_runtime as lambda;

fn main() {
    // start the runtime, and return a greeting every time we are invoked
    lambda::start(|()| Ok("Hello ƛ!"))
}

```

### Deploy

TBD
