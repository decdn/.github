# deCDN

A decentralized CDN where nodes bond stake, cache content-addressed blobs, and earn per-MB USDC payments through off-chain vouchers backed by a shared on-chain pool ([ADR 003](https://github.com/decdn/decdn/blob/main/adr/003-payments.md)). Built in Rust on [iroh](https://github.com/n0-computer/iroh) QUIC. Open source under MIT OR Apache-2.0.

> **Status: public testnet.** The network runs on Arbitrum Sepolia; production targets Arbitrum One. Signed binaries, crates, and container images for both the `decdn-node` daemon and the `decdn` CLI ship with each [release](https://github.com/decdn/decdn/releases/latest), starting with v0.0.1. Wire, ABI, config, and storage formats change without compatibility shims until mainnet, and many ADRs are still Draft. The [ADRs](https://github.com/decdn/decdn/tree/main/adr) are the source of truth for current thinking.

## The repos

- **[decdn/decdn](https://github.com/decdn/decdn)**: the core Rust monorepo. A Cargo workspace with the `decdn-node` daemon and `decdn` CLI, plus crates for the protocol, cache, client, incentive, and reputation layers. It also holds the Solidity contracts and the ADRs behind the design. Most work happens here.
- **[decdn/devops](https://github.com/decdn/devops)**: deploy and operate a deCDN node with Ansible, cloud-init, Docker Compose, or a Helm chart, plus the Grafana dashboards and alert rules for monitoring one. Hardened and localhost-only by default.
- **[decdn/sponsord](https://github.com/decdn/sponsord)**: sponsored downloads. A publisher funds a USDC payment pool, and their users download through a one-line installer and a captcha, with no wallet, keys, or tokens to manage.
- **[decdn/stats](https://github.com/decdn/stats)**: network status dashboard read from on-chain state on Arbitrum Sepolia, live at [stats.decdn.org](https://stats.decdn.org).
- **[decdn/website](https://github.com/decdn/website)**: Next.js landing page, live at [decdn.org](https://decdn.org). Also holds the source for [docs.decdn.org](https://docs.decdn.org).
- **[decdn/iroh-tests](https://github.com/decdn/iroh-tests)**: reproductions for issues found in iroh, iroh-blobs, noq, and bao-tree while building deCDN, with the workaround each one needed.

## For developers

- **Design first.** Every subsystem is tracked in numbered ADRs. Start with [`adr/README.md`](https://github.com/decdn/decdn/blob/main/adr/README.md) for the reading order and [`adr/architecture.md`](https://github.com/decdn/decdn/blob/main/adr/architecture.md) for the overview.
- **Rust 2024 edition, MSRV 1.99.** Tests run under `cargo nextest`. Contributions must pass `cargo fmt`, `cargo clippy`, and `cargo deny check`. See [`CONTRIBUTING.md`](https://github.com/decdn/decdn/blob/main/CONTRIBUTING.md) for environment setup.
- **Strict anti-panic policy.** Clippy denies `unwrap_used`, `expect_used`, `panic`, and `indexing_slicing` across the whole workspace. New contributors run into this most often.
- **Docs.** User and operator docs are at [docs.decdn.org](https://docs.decdn.org). To run a node, start with the [operator guide](https://docs.decdn.org/run-a-node/overview).

## Getting in touch

Open an issue on the relevant repo, and use [decdn/decdn](https://github.com/decdn/decdn/issues) for protocol and node questions. Report security vulnerabilities privately as described in [`SECURITY.md`](https://github.com/decdn/decdn/blob/main/SECURITY.md). For chat, join the [Discord](https://discord.gg/vVbNswKVGX).

## License

Core code is dual-licensed under [MIT](https://github.com/decdn/decdn/blob/main/LICENSE-MIT) OR [Apache-2.0](https://github.com/decdn/decdn/blob/main/LICENSE-APACHE).
