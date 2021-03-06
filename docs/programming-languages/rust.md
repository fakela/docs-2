---
description: This guide provides an explanation on how to configure Rust projects on Semaphore 2.0. It provides example projects as well that should help you get started.
---

# Rust

This guide will help you get started with a Rust project on Semaphore.
If you’re new to Semaphore, we recommend reading our
_[Guided tour](https://docs.semaphoreci.com/guided-tour/getting-started/)_ first.

## Hello World

``` yaml
# .semaphore/semaphore.yml
version: v1.0
name: Rust example
agent:
  machine:
    type: e1-standard-2
  containers:
    - name: main
      image: semaphoreci/rust:1.35
blocks:
  - name: Hello world
    task:
      jobs:
      - name: Compile and run code
        commands:
          - printf 'fn main() { println!("Hello World!"); }' > hello.rs && rustc hello.rs
          - ./hello
```

## Supported Rust Versions

Semaphore supports all versions of Rust. To run Rust programs you should define
[a Docker-based agent][docker-env] using one of the available Rust images,
or build your own container image that matches your needs.

For more information about pre-built Rust images provided by Semaphore, see
[semaphoreci/rust][rust-docker-image] documentation on Docker Hub.

[docker-env]: https://docs.semaphoreci.com/ci-cd-environment/custom-ci-cd-environment-with-docker/
[rust-docker-image]: https://hub.docker.com/r/semaphoreci/rust
