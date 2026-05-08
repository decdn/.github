# deCDN

A decentralized CDN where nodes stake, cache content-addressed blobs, and earn per-MB payments over off-chain USDC channels. Built in Rust on [iroh](https://github.com/n0-computer/iroh) QUIC.

> **Status: early / pre-launch.** Running toward a PoC on an L2. APIs, wire formats, and economics are still in flux — the [ADRs](https://github.com/decdn/decdn/tree/main/adr) are the source of truth for current thinking.

## The repos

- **[decdn/decdn](https://github.com/decdn/decdn)** — core Rust monorepo. Cargo workspace with `protocol`, `cache`, `gossip`, `node`, `incentive`, and `reputation` crates, plus the Solidity contracts. Most work happens here. (Not public yet, still cooking)
- **[decdn/website](https://github.com/decdn/website)** — Next.js landing page.

## For developers

- **Design-first.** Architecture is tracked in ADRs under [`decdn/adr/`](https://github.com/decdn/decdn/tree/main/adr). Start with `architecture.md`, then follow the numbered ADRs for whichever subsystem interests you.
- **Toolchain.** Rust 2024 edition, MSRV 1.85. Tests run under `cargo nextest`. Contributions should pass `cargo fmt`, `cargo clippy`, and `cargo deny check`.
- **Devcontainer recommended.** The core repo ships a VS Code devcontainer with the toolchain preconfigured — see `CONTRIBUTING.md` in `decdn/decdn`.
- **Anti-panic policy.** Clippy denies `unwrap_used`, `expect_used`, `panic`, and `indexing_slicing` workspace-wide. New contributors trip this most often.

## Getting in touch

Open an issue on the relevant repo. No public chat or mailing list yet.

## License

Core code is dual-licensed under MIT OR Apache-2.0.
