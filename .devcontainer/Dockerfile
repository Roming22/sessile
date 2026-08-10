FROM rust:1-bookworm

ARG TARGET_ARCH=thumbv7em-none-eabihf
ARG LLVM_VERSION=14
# Keep in sync with rmk/rust-toolchain.toml
ARG RUST_TOOLCHAIN=1.96.0

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    clang-${LLVM_VERSION} \
    git \
    libclang-${LLVM_VERSION}-dev \
    liblzma-dev \
    pkg-config \
    && rm -rf /var/lib/apt/lists/*

ENV LIBCLANG_PATH=/usr/lib/llvm-${LLVM_VERSION}/lib

# Install against the pinned toolchain: rmk/rust-toolchain.toml overrides the
# image default, so targets added only to the default are invisible.
RUN rustup toolchain install ${RUST_TOOLCHAIN} \
    && rustup target add --toolchain ${RUST_TOOLCHAIN} ${TARGET_ARCH} \
    && rustup component add --toolchain ${RUST_TOOLCHAIN} rust-src rustfmt llvm-tools \
    && cargo install --locked \
        cargo-binutils \
        cargo-hex-to-uf2 \
        cargo-make \
        flip-link

WORKDIR /workspaces/sessile
