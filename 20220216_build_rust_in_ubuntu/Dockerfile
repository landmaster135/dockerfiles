FROM ubuntu:latest

# RUN apt update
RUN apt update

# for install Rust
RUN apt install -y curl

# decide working directory
WORKDIR /usr/app

# install gcc for install Rust
RUN apt install build-essential
RUN gcc --version

# install Rust
RUN curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
RUN export PATH="$HOME/.cargo/bin:$PATH"

# copy files in the current directory to directory in the built container.
COPY ./ /usr/app


# In case without Cargo project: Start -----------------------

# compile Rust file.
RUN rustc main.rs -o main

# execute compiled Rust file.
RUN ./main

# In case without Cargo project: End -----------------------


# In case with Cargo project: Start -----------------------

# check whether installed or not.
RUN cargo --version
RUN rustc --version
RUN rustdoc --version
RUN rustup --version

# debug with rust-lldb
# RUN apt install lldb
# RUN lldb --version
# RUN rust-lldb

# setup Cargo project
RUN cargo new hello --bin
RUN cd hello
RUN cargo build

# compile file in Cargo project for product
# RUN cargo build --release

# execute in Cargo project
# RUN cargo run

# In case with Cargo project: End -----------------------
