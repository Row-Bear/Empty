# Remove the existing rustup installation before updating due to:
# https://github.com/gitpod-io/workspace-images/issues/933#issuecomment-1272616892
RUN rustup self uninstall -y
RUN rm -rf .rustup
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y

RUN rustup update stable
RUN rustup target add --toolchain stable wasm32-unknown-unknown
RUN rustup component add --toolchain stable rust-src
RUN rustup default stable

RUN sudo apt-get update && sudo apt-get install -y binaryen
RUN rustup target add wasm32-unknown-unknown
RUN cargo install --locked --version 20.0.0-rc4 soroban-cli