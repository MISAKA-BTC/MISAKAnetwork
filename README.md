# MISAKA Network

MISAKA Network is a high-performance Layer-1 blockchain built on a DAG-based parallel block structure with a custom epoch-key RandomX Proof-of-Work (MisakaX).

It combines:

* **MisakaX (Epoch-key RandomX PoW)**
* **DAG-based parallel block processing**
* **Future PoS Finality layer**
* **Slashing-ready validator framework**
* **Bridge-ready architecture**
* **OAuth-enabled wallet onboarding layer**

---

# 🧠 Architecture Overview

```
           +----------------------+
           |      Applications     |
           +----------------------+
                     │
           +----------------------+
           |   Wallet / OAuth     |
           |  (Google / Apple)    |
           +----------------------+
                     │
           +----------------------+
           |   PoS Finality (WIP) |
           |   Slashing-ready     |
           +----------------------+
                     │
           +----------------------+
           |      DAG Layer        |
           | Parallel Block Graph  |
           +----------------------+
                     │
           +----------------------+
           |    MisakaX PoW       |
           | Epoch-key RandomX    |
           +----------------------+
```

---

# 🔥 MisakaX (Epoch-key RandomX)

MisakaX is a custom Proof-of-Work derived from RandomX with deterministic epoch rotation.

### Key Features

* Epoch-based key rotation
* Prevents long-term ASIC optimization
* Maintains CPU-favoring characteristics
* Compatible with DAG parallelism

### Epoch Rule

```
epoch_id = header.daa_score / 1000
key = BLAKE3("stmisaka-randomx" || epoch_id_le)
```

* Every 1000 DAA score units, RandomX cache is regenerated.
* VM reinitializes only on epoch switch.
* PoW input format remains unchanged (48 bytes):

```
PRE_POW_HASH || TIMESTAMP || NONCE
```

---

# 🌐 DAG Parallelism

MISAKA Network inherits high-throughput DAG architecture:

* Multiple blocks can be created in parallel.
* No strict single-chain bottleneck.
* Blue work scoring determines block ordering.
* High scalability without sacrificing security.

---

# 🛡 Planned PoS Finality (Phase 2)

To enhance 51% attack resistance:

* Validator-based finality voting
* 3-of-4 (configurable) validator threshold
* Double-sign detection
* Slashing-ready logic
* State machine:

  ```
  pending → finalized
  ```

Finality layer is deterministic and cryptographically verifiable.

---

# ⚖ Slashing (Planned)

Designed to punish malicious validators:

* Double-sign evidence
* Competing vote detection
* Cryptographic proof generation
* On-chain slashing record

---

# 🌉 Bridge Architecture (Planned)

Future bridge integration includes:

* stMISAKA token model
* Lock-and-mint architecture
* External chain verification
* Cross-chain proof validation

Bridge module exists but is not yet activated.

---

# 🔐 OAuth Wallet Layer

MISAKA supports user-friendly onboarding:

* Google login
* Apple login (planned)
* Discord login (planned)
* Wallet key derivation after OAuth verification
* Signature-based wallet linking

This layer is separate from consensus.

---

# ⚙ Node Setup

## Build

```bash
cargo build -p kaspad --release
```

## Run

```bash
./target/release/kaspad --rpclisten=0.0.0.0:16110
```

Open ports:

* 16111 (P2P)
* 16110 (RPC)

---

# 📈 Token Emission

* Total supply: 5,000,000,000
* Emission model: decay-based
* Halving period: 730 days
* Daily decay unchanged

---

# 🚀 Development Roadmap

| Phase   | Feature                     | Status  |
| ------- | --------------------------- | ------- |
| Phase 1 | MisakaX PoW                 | ✅ Live  |
| Phase 1 | DAG Layer                   | ✅ Live  |
| Phase 2 | PoS Finality                | 🚧      |
| Phase 2 | Slashing                    | 🚧      |
| Phase 3 | Bridge                      | 🚧      |
| Phase 3 | Smart Contracts (Rust/WASM) | Planned |

---

# 🔎 Current Status

* MisakaX epoch-based RandomX implemented
* Cache rotation working
* Logs show epoch switching
* Network running
* Finality not yet enabled

---

# 📄 License

MIT License

---

