# Changelog

All notable changes to Signet will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

For release instructions and versioning procedures, see [`docs/RELEASING.md`](docs/RELEASING.md).

---

## Deployed Contract Registry

| Network | Contract | Contract ID | Deployed Date | Verification |
| --- | --- | --- | --- | --- |
| **Stellar Testnet** | `identity-registry` | `CDLZFC3SYJYDZT7K67VZ75HPJVIEUVNIXF47ZG2FB2RMQQVU2HHGCYSC` | 2026-07-09 | Active (Soroban RPC) |
| **Stellar Mainnet** | `identity-registry` | *Pending deployment* | *TBD* | — |

---

## [Unreleased]

### Added
- Area-based code review assignments via `.github/CODEOWNERS` ([#231](https://github.com/blockchain-maxis/signet/issues/231)).
- CI concurrency group to cancel superseded in-progress workflow runs on push ([#229](https://github.com/blockchain-maxis/signet/issues/229)).
- Release procedure documentation and versioning policy in `docs/RELEASING.md` ([#227](https://github.com/blockchain-maxis/signet/issues/227)).
- Identity Registry migration runbook in `docs/CONTRACT_MIGRATION.md` ([#308](https://github.com/blockchain-maxis/signet/pull/308)).
- Multi-device and per-address session revocation with Upstash Redis backend support ([#307](https://github.com/blockchain-maxis/signet/pull/307)).
- Contract error drift checker `scripts/check-contract-errors.mjs` guarding Rust contract error codes against UI translation sync ([#238](https://github.com/blockchain-maxis/signet/pull/238)).
- Live testnet E2E seam test for claim → resolve → profile flow ([#240](https://github.com/blockchain-maxis/signet/pull/240)).

### Changed
- Public SDK type surface stabilized ahead of `@signet/sdk@0.1.0` release ([#310](https://github.com/blockchain-maxis/signet/pull/310)).
- Health route `/api/health` now reports nonce and rate-limit store status dynamically ([#309](https://github.com/blockchain-maxis/signet/pull/309)).
- Connect wallet badge dynamically renders the active configured network from `NEXT_PUBLIC_STELLAR_NETWORK` ([#168](https://github.com/blockchain-maxis/signet/issues/168)).

### Fixed
- Added static `/handles` route to sitemap indexing ([#222](https://github.com/blockchain-maxis/signet/issues/222)).
- Smoke tests now rely on semantic heading selectors instead of brittle copy assertions ([#219](https://github.com/blockchain-maxis/signet/issues/219)).
- Extended contract instance TTL on read paths to prevent storage archival of active registries ([#242](https://github.com/blockchain-maxis/signet/pull/242)).

---

## [0.1.0] - 2026-08-28

### Added
- Initial release of Signet developer career record platform.
- **Identity Registry Contract** (`packages/contracts/identity-registry`):
  - On-chain handle claim, transfer, and release methods with owner authorization (`require_auth`).
  - Read-path TTL extension for bound records and contract instance.
  - Comprehensive unit test suite and property-based invariant testing.
- **Web Application** (`apps/web`):
  - Landing page, how-it-works guide, and public `/p/{handle}` profiles.
  - Discovery directory at `/handles` reading direct Soroban events.
  - Stellar Wallets Kit wallet connection and SEP-10 Sign-In With Stellar (SIWS) authentication.
  - tRPC API endpoints for profile queries, handle resolution, and health reporting.
- **Indexer Worker** (`apps/indexer`):
  - Horizon polling worker for deployment and operation indexing into PostgreSQL.
  - Attestation event parser for on-chain identity binding events.
- **TypeScript SDK** (`@signet/sdk`):
  - Read-only client for querying profiles, resolved handles, and platform health.
