# deCDN

A decentralized CDN where nodes bond stake, cache content-addressed blobs, and earn per-MB USDC payments through off-chain vouchers backed by a shared on-chain pool ([ADR 003](https://github.com/decdn/decdn/blob/main/adr/003-payments.md)). Built in Rust on [iroh](https://github.com/n0-computer/iroh) QUIC. Open source under MIT OR Apache-2.0.

> **Status: early / pre-launch.** Running toward a PoC on an L2. No tagged release yet, and APIs, wire formats, and economics are still in flux. The [ADRs](https://github.com/decdn/decdn/tree/main/adr) are the source of truth for current thinking.

## The repos

- **[decdn/decdn](https://github.com/decdn/decdn)**: the core Rust monorepo. A Cargo workspace with the `decdn-node` daemon and `decdn` CLI, plus crates for the protocol, cache, client, incentive, and reputation layers. It also holds the Solidity contracts and the ADRs behind the design. Most work happens here.
- **[decdn/devops](https://github.com/decdn/devops)**: the official DevOps repo for deploying a deCDN node.
- **[decdn/sponsor](https://github.com/decdn/sponsor)**: sponsored testnet on-ramp. A captcha-gated gateway grants new clients a spending allowance so they can fetch paid content without setting up a wallet first.
- **[decdn/stats](https://github.com/decdn/stats)**: network status dashboard built from on-chain settlement data.
- **[decdn/website](https://github.com/decdn/website)**: Next.js landing page, live at [decdn.org](https://decdn.org).

## For developers

- **Design first.** Every subsystem is tracked in numbered ADRs. Start with [`adr/README.md`](https://github.com/decdn/decdn/blob/main/adr/README.md) for the reading order and [`adr/architecture.md`](https://github.com/decdn/decdn/blob/main/adr/architecture.md) for the overview.
- **Rust 2024 edition, MSRV 1.95.** Tests run under `cargo nextest`. Contributions must pass `cargo fmt`, `cargo clippy`, and `cargo deny check`. See [`CONTRIBUTING.md`](https://github.com/decdn/decdn/blob/main/CONTRIBUTING.md) for environment setup.
- **Strict anti-panic policy.** Clippy denies `unwrap_used`, `expect_used`, `panic`, and `indexing_slicing` across the whole workspace. New contributors run into this most often.
- **Docs.** User and operator docs are at [docs.decdn.org](https://docs.decdn.org).

## Getting in touch

Open an issue on the relevant repo, and use [decdn/decdn](https://github.com/decdn/decdn/issues) for protocol and node questions. Report security vulnerabilities privately as described in [`SECURITY.md`](https://github.com/decdn/decdn/blob/main/SECURITY.md). There's no public chat or mailing list yet.

## License

Core code is dual-licensed under [MIT](https://github.com/decdn/decdn/blob/main/LICENSE-MIT) OR [Apache-2.0](https://github.com/decdn/decdn/blob/main/LICENSE-APACHE).
