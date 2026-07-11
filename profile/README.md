# deCDN

A decentralized CDN where nodes stake, cache content-addressed blobs, and earn per-MB payments over off-chain USDC channels. Built in Rust on [iroh](https://github.com/n0-computer/iroh) QUIC.

> **Status: early / pre-launch.** Running toward a PoC on an L2. APIs, wire formats, and economics are still in flux.

## The repos

- **[decdn/website](https://github.com/decdn/website)** — Next.js landing page. Public, live at [decdn.org](https://decdn.org).
- **[decdn/devops](https://github.com/decdn/devops)** — the official DevOps repo for deploying a deCDN node. Public.
- **decdn/decdn** — core Rust monorepo: a Cargo workspace with `protocol`, `cache`, `gossip`, `node`, `incentive`, and `reputation` crates, the Solidity contracts, and the ADRs that drive the design. Most work happens here. Not public yet — still cooking; it'll open (MIT OR Apache-2.0) ahead of the public testnet.

## Under the hood

Once the core repo is public you'll find:

- **Design-first architecture.** Every subsystem is tracked in numbered ADRs — they are the source of truth for current thinking, ahead of the code.
- **Rust 2024 edition, MSRV 1.95.** Tests run under `cargo nextest`; contributions pass `cargo fmt`, `cargo clippy`, and `cargo deny check`.
- **Strict anti-panic policy.** Clippy denies `unwrap_used`, `expect_used`, `panic`, and `indexing_slicing` workspace-wide.
- **Devcontainer included.** A VS Code devcontainer ships the toolchain preconfigured.

## Following along

The best place to track progress today is [decdn.org](https://decdn.org). The core protocol code and its ADRs will open ahead of the public testnet.

## Getting in touch

Open an issue on [decdn/website](https://github.com/decdn/website/issues). No public chat or mailing list yet.

## License

Core code will be released dual-licensed under MIT OR Apache-2.0.
