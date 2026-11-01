# deCDN

**[Website](https://decdn.org)** · **[Docs](https://docs.decdn.org)** · **[Network stats](https://stats.decdn.org)** · **[Discord](https://discord.gg/vVbNswKVGX)** · **[X](https://x.com/decdn_)**

A decentralized CDN: nodes bond stake, cache content-addressed blobs, and earn per-MB USDC payments from a shared on-chain pool ([ADR 003](https://github.com/decdn/decdn/blob/main/adr/003-payments.md)). Built in Rust on [iroh](https://github.com/n0-computer/iroh) QUIC.

> **Status: public testnet** on Arbitrum Sepolia ([launch post](https://decdn.org/blog/testnet-is-live/)). Wire, config, and storage formats can change without compatibility shims until mainnet. Try it with a one-line installer, no wallet needed: see the [quickstart](https://github.com/decdn/decdn#readme).

## Repos

- **[decdn](https://github.com/decdn/decdn)**: the core monorepo. Node daemon, `decdn` CLI, client SDK, sponsorship daemon, Solidity contracts, and the [ADRs](https://github.com/decdn/decdn/tree/main/adr) behind the design. Most work happens here.
- **[sdk-typescript](https://github.com/decdn/sdk-typescript)** and **[sdk-python](https://github.com/decdn/sdk-python)**: clients for Node.js, browsers, and Python that talk to a `decdn gateway`.
- **[android-demo](https://github.com/decdn/android-demo)**, **[ios-demo](https://github.com/decdn/ios-demo)**, and **[browser-demo](https://github.com/decdn/browser-demo)**: demo apps that download and verify content from a sponsored pool.
- **[devops](https://github.com/decdn/devops)**: deploy and run a node with Docker Compose, Ansible, cloud-init, or Helm.
- **[stats](https://github.com/decdn/stats)**: the network dashboard at [stats.decdn.org](https://stats.decdn.org).
- **[website](https://github.com/decdn/website)**: [decdn.org](https://decdn.org), the blog, and [docs.decdn.org](https://docs.decdn.org).
- **[iroh-tests](https://github.com/decdn/iroh-tests)**: reproductions of upstream iroh issues found while building deCDN.

## Contributing

Start with the [ADR reading order](https://github.com/decdn/decdn/blob/main/adr/README.md) and [`CONTRIBUTING.md`](https://github.com/decdn/decdn/blob/main/CONTRIBUTING.md). To run a node, see the [operator guide](https://docs.decdn.org/run-a-node/overview).

Questions go in [issues](https://github.com/decdn/decdn/issues) or on [Discord](https://discord.gg/vVbNswKVGX). Report vulnerabilities privately per [`SECURITY.md`](https://github.com/decdn/decdn/blob/main/SECURITY.md).

Code is dual-licensed under [MIT](https://github.com/decdn/decdn/blob/main/LICENSE-MIT) OR [Apache-2.0](https://github.com/decdn/decdn/blob/main/LICENSE-APACHE).
