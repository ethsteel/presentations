---
title: EEST x Security - EEST Tooling Overview
tags: Talk, Ethereum, Testing, Execution Layer, STEEL
description: EEST Tooling Overview for the Security Team.
slideOptions:
  theme: white
  transition: "slide"
---

<style>
.reveal .slides > section > section {
  text-align:left;
}
p {
  text-align: left;
  font-size: 0.9em;
}
li {
  font-size: 0.9em;
}
td, th {
  font-size: 0.9em;
}
h1, h2, h3, h4, h5, h6 {
  text-align: left;
}
/* Center align only the first slide content */
.reveal .slides > section:first-child h1,
.reveal .slides > section:first-child h2,
.reveal .slides > section:first-child h3,
.reveal .slides > section:first-child h4,
.reveal .slides > section:first-child h5,
.reveal .slides > section:first-child h6 {
  text-align: center;
}
.footer {
  position: fixed;
  bottom: 10px;
  left: 10px;
  right: 10px;
  font-size: 12px;
  color: #666;
  text-align: center;
  z-index: 1000;
}
.columns {
  display: flex;
  align-items: flex-start;
}
.column {
  flex: 1;
  margin: 0 20px;
}
.small-table table {
  font-size: 0.8em;
}
.small-table td, .small-table th {
  padding: 4px 8px;
}
.small-slide {
  font-size: 0.9em;
}
.small-slide p, .small-slide li, .small-slide td, .small-slide th {
  font-size: 0.9em;
}
.small-table table {
  font-size: 0.8em;
}
.small-table td, .small-table th {
  padding: 4px 8px;
}
</style>

### EEST x Security Team: EEST Tooling Overview

<div style="text-align: center">
    2025-08-20
</div>

---

### `consume direct`

| Interface | Components | Best For |
|-----------|------------|----------|
| State Test (`statetest`) | EVM | Rapid EVM development and debugging |
| Block Test (`blocktest`) | EVM, block processing | Fast block validation testing |

**Common**: Environment: None | Scope: Module test, Integration test

---

### `consume rlp`

|  |  |
|--|--|
| Description | Client imports RLP-encoded blocks upon start-up in Hive |
| Components | EVM, block processing, RLP import (sync) |
| Environment | Staging, Hive |
| Scope | System test |
| Best for | Historical sync simulation |

---

### `consume engine`

|  |  |
|--|--|
| Description | Client imports blocks via Engine API `EngineNewPayload` in Hive |
| Components | EVM, block processing, Engine API |
| Environment | Staging, Hive |
| Scope | System test |
| Best for | Post-merge production-like testing |

Soon: `consume enginex` > 10x faster.

---

### `consume sync`

|  |  |
|--|--|
| Description | Client syncs from another client using Engine API in Hive |
| Components | EVM, block processing, Engine API, P2P sync |
| Environment | Staging, Hive |
| Scope | System test |
| Best for | Testing client synchronization capabilities |

---

### `execute remote`

|  |  |
|--|--|
| Description | Tests executed against a client via JSON RPC `eth_sendRawTransaction` on a live network |
| Components | EVM, JSON RPC, mempool, EL-EL/EL-CL interaction (indirectly) |
| Environment | Production |
| Scope | System Test |
| Best for | Real network testing and validation |

---

### `execute hive`

|  |  |
|--|--|
| Description | Tests executed against a client via JSON RPC `eth_sendRawTransaction` in Hive |
| Components | EVM, JSON RPC, mempool |
| Environment | Staging, Hive |
| Scope | System test |
| Best for | Mempool and transaction execution testing |

---

### `execute eth-config`

|  |  |
|--|--|
| Description | Test that the response from the `eth_config` endpoint matches expectations |
| Components | JSON RPC, client config |
| Environment | Production |
| Scope | System Test |

---

### Blobber

<https://github.com/marioevz/blobber>

```mermaid
    graph LR;
        subgraph identifier[" "]
            beaconClient(Beacon Client)
            validatorClient(Validator Client)
            proxy(Blobber)
            BeaconDevP2P(Beacon DevP2P Network)
        end

        validatorClient -->|Attestations Request| proxy
        proxy -->|Attestations Request| beaconClient
        beaconClient -->|Attestations Response| proxy
        proxy -->|Attestations Response| validatorClient

        validatorClient -->|Proposal Request| proxy
        proxy -->|Proposal Request| beaconClient
        beaconClient -->|Proposal Response| proxy
        proxy -.->|Modified/Signed Proposal Response| BeaconDevP2P

        linkStyle 0,1 stroke-width:3px,fill:none,stroke:darkgreen;
        linkStyle 2,3 stroke-width:3px,fill:none,stroke:green;
        linkStyle 4,5 stroke-width:3px,fill:none,stroke:blue;
        linkStyle 6,7 stroke-width:3px,fill:none,stroke:darkblue;

```

---

### eest-fuzz

New repo, relatively unused(?):

- <https://github.com/SamWilsn/eest-fuzz>

---

### Relevant: The Weld ⚔️🔥

- Now, we have two repos:
    - ethereum/execution-specs
    - ethereum/execution-spec-tests

- Q4 2025:
    - EEST will move to ethereum/execution-specs


Aim:
- Huge dev-ex gain for EIP Authors & Testers.
- Will make EEST test coverage of EELS trivial.

---

### Questions

- Do you see any gaps in our work / quick wins?
- How can EEST help facilitate fuzzing?
  - Are the formats adequate?
  - No recent progress in `consume direct`, blocker?
  - Can we help with tooling to fuzz devnets?
- Join EIP hardening sessions?

---

thanks!

---

### EELS and EEST Origins & Growth

<div style="text-align: center">
<img src="https://github.com/ethsteel/presentations/blob/3f2df68762bef84dcb3cefc0b1911c83a3717211/2025-08-18_ef-town-hall/img/timeline_with_histogram.png?raw=true" height="500" alt="STEEL Team Timeline">
</div>

---

### STEEL TEAM Goals

<div class="small-slide">

1. EIP specifications are clear, sufficient and correct.
2. EL clients are adequately tested before hard forks.

<div style="margin-top: 0.5.em;"></div>

**Achieving these goals is a collaborative effort!**

|                      |                           |
| -------------------- | ------------------------- |
| Researchers          | Spec Definition           |
| Client Developers    | Production Implementation |
| Security Researchers | Production Testing        |

</div>

---

### Core Responsibilities: EELS📐

- Maintaining EL specs as executable Python Code.
  - Enabling EIP prototyping.
- Publishing releases of spec snapshots.
- Providing the reference EVM for tests.

---

### Core Responsibilities: EEST🧪

- Python test cases for EIPs / Scale the L1.
- Test vector generation framework.
- Continuous delivery of reference test case releases to clients.
- Module & system test frameworks (Hive simulators) and help debugging fails.

---

### Core Responsibilities: EEST🧪

<img src="https://github.com/ethsteel/presentations/blob/3f2df68762bef84dcb3cefc0b1911c83a3717211/2025-08-18_ef-town-hall/img/eest_releases_timeline_light_hires.png?raw=true" height="460" style="object-fit: contain; max-width: 100%;" alt="EEST Release Timeline">

---

### Links

<div class="small-slide">

Soon: steel.ethereum.foundation

Docs:

- EELS docs, e.g. [MODEXP changes in Osaka](https://ethereum.github.io/execution-specs/diffs/prague/osaka/vm/precompiled_contracts/modexp.py.html)
- [EEST test case documentation](https://ethereum.github.io/execution-spec-tests/main/tests)

Repos and releases:

- [ethereum/execution-specs](https://github.com/ethereum/execution-specs)
- [ethereum/execution-spec-tests](https://github.com/ethereum/execution-spec-tests)
- [EELS releases on PyPI](https://pypi.org/project/ethereum-execution/)
- [EEST releases on Github](https://github.com/ethereum/execution-spec-tests/releases)

</div>

---

Thanks!

---
