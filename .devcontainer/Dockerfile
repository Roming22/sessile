FROM docker.io/library/rust:latest

RUN rustup target add thumbv7em-none-eabihf \
    && cargo install flip-link probe-rs-tools