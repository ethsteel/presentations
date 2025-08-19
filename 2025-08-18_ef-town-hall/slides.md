---
title: STEEL
tags: Talk, Ethereum, Testing, Execution Layer, STEEL
description: Specifications and Testing for the Ethereum Execution Layer for the EF Town Hall, August, 2025
slideOptions:
  theme: white
  transition: "slide"
---

### STEEL

<style>
.reveal .slides > section > section {
  text-align:left;
}
p {
  text-align: left;
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

##### 🐍Specifications and Testing for the Ethereum Execution Layer 📐🧪🐍

<img src="./img/steel_logo.png" height=150 alignment="center">

<div style="text-align: center">
    <a style="font-size: 0.70em" href="https://github.com/danceratopz/">danceratopz</a><br/>
    EF Town Hall, 2025-08-18
</div>

---

### STEEL Acronyms

|       |                                                      |      |
| ----- | ---------------------------------------------------- | ---- |
| STEEL | Specs & Testing for the <br>Ethereum Execution Layer | ⚔️🛡️ |
| EELS  | Execution Layer Specs                                | 📐   |
| EEST  | Execution Spec Tests                                 | 🧪   |

---

### EELS and EEST Origins & Growth

<div style="text-align: center">
<img src="./img/timeline_with_histogram.png" height="500" alt="STEEL Team Timeline">
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

<img src="./img/eest_releases_timeline_light_hires.png" height="460" style="object-fit: contain; max-width: 100%;" alt="EEST Release Timeline">

---

### Current Mainnet Testing

**Fusaka**: Primary testing focus (in-team)

**Glamsterdam**: BALS specs & tests (Toni/Rahul)

**Scale the L1**: Pathological test generation (benchmarking, zkevm)

- Collaboration with Nethermind & EF teams
- New Blockchain Test "EngineX" format

---

### Challenges and Strategy

<div class="small-table">

|                                                   |                                                   |
| ------------------------------------------------- | ------------------------------------------------- |
| Technical debt: ethereum/tests; separate repos    | Fill ethereum/tests in EEST; Merge EELS and EEST:<br/>The Weld🔥⚔️ |
| Estimating & Tracking Spec                        | Introduce more process; Scale the STEEL           |
| Complete Coverage is Hard                         | Hardening Sessions EIP Checklist, Post Mortems    |
| Broad responsibility scope: CL, benchmarking, RPC | Scale the STEEL,<br/>Improved team org            |

</div>

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
