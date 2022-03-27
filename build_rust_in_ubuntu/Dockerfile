FROM ubuntu:latest

# RUN apt update
RUN apt-get update
RUN apt update

# for install Rust
RUN apt install -y curl

# install gcc for install Rust
RUN apt install -y build-essential
RUN gcc --version

# install Rust
ENV RUST_VERSION stable
RUN curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh -s -- -y --default-toolchain ${RUST_VERSION}

# # setup PATH
ENV PATH="/root/.cargo/bin:$PATH"

# decide working directory
WORKDIR /usr/app

# copy files in the current directory to directory in the built container.
COPY ./ /usr/app

# check whether installed or not.
RUN cargo --version
RUN rustc --version
RUN rustdoc --version
RUN rustup --version

# In case without Cargo project: Start -----------------------

# compile Rust file.
RUN rustc main.rs -o main

# execute compiled Rust file.
# RUN ./main

# In case without Cargo project: End -----------------------

# In case with Cargo project: Start -----------------------

# install rust-lldb
# RUN apt install -y lldb
# RUN lldb --version

# debug with rust-lldb
# RUN rust-lldb
# RUN rust-lldb ./main

# # setup Cargo project
RUN cargo new hello --bin
WORKDIR /usr/app/hello
RUN cargo build

# compile file in Cargo project for product
# RUN cargo build --release

# execute in Cargo project
# RUN cargo run

# In case with Cargo project: End -----------------------
