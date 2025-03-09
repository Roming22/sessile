FROM docker.io/library/rust:latest

RUN cargo install cargo-make flip-link \
    && curl --proto '=https' --tlsv1.2 -LsSf https://github.com/probe-rs/probe-rs/releases/latest/download/probe-rs-tools-installer.sh | sh \
    && apt update \
    && apt install -y npm \
    && apt clean