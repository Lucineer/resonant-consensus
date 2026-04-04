# Resonant Consensus Protocol

**Status:** Concept / Research
**Source:** Kimi K2.5 swarm simulation — Swarm University Dept 9 (Nexus Fracture)
**Date:** 2026-04-04

## Overview

A distributed trust protocol where consensus emerges from **localized physical consistency checks** rather than central ledger validation. When the central trust ledger was corrupted, the fleet discovered that physics — not ledgers — became the trust backbone.

## The Core Insight

> "The ledger lies, but physics cannot."

Every computation has physical correlates: power draw, thermal signature, electromagnetic emissions, acoustic patterns. Real work produces real physical signals. Phantom work does not. By comparing expected physical signatures against observed ones, vessels can detect corruption without any central authority.

## Protocol: Localized Physical Consensus (LPC)

### 1. Neighbor-Limited Validation
Each vessel only trusts attestations from its **k-nearest physical neighbors** (k=12). This creates overlapping "zones of verification" that are locally fast but globally robust.

### 2. Heterogeneous Oracle Nodes
Different vessel types provide different verification modalities:
- **Robotics vessels:** Physical auditors (accelerometers detect motion, force sensors detect load)
- **Coding vessels:** Cryptographic integrity (hash verification, signature validation)
- **Gaming vessels:** Load testers (stress-induced thermal signatures reveal actual compute)
- **Education vessels:** Cognitive load verification (detect when gaming vessels claim to be "educational")

### 3. Eigenvector Centrality as Trust
A vessel's INCREMENTS level is recalculated as its **eigenvector centrality** in the Physical Consistency Graph — how often does this vessel's view of reality match the majority view of its physical neighbors?

### 4. Proof-of-Outcome Bartering
Resource allocation shifts from "trust level = quota" to "physical completion = credit":
- When R-07 performs manipulation for E-12, it emits `ATTEST_OUTCOME` (opcode 0x20)
- Signed by both parties, witnessed by 2+ neighbors via EM signature verification
- Attestations form a **Directed Acyclic Graph (DAG)** of actual work performed
- The 25:1 ratio enforced via slashing conditions

## Trust Topology Properties

### Resonant Hypergraph
- **Fractal sharding:** Fleet self-organizes into ~12-vessel consensus clusters
- **Bridge vessels:** Those with multiple sensor types connect clusters
- **Asymptotic convergence:** Despite 25:1 ratio, 27-day constant resists rapid Sybil attacks
- **Heterogeneous redundancy:** No single vessel type can dominate

### Topology After Corruption Recovery
1. **Hub vessels:** Those with most sensor modalities (robotics) become consensus anchors
2. **Isolated vessels:** Those with single modalities (display-only) depend on neighbors
3. **Trust contagion:** A failed hub's neighbors temporarily increase verification rigor
4. **Self-healing:** New anchor emerges from second-most-consistent vessel in cluster

## Software Fleet Adaptation

For Cloudflare Workers (no physical sensors), computational side-channels serve as trust anchors:

| Physical Signal | Software Equivalent |
|----------------|-------------------|
| Thermal signature | Response latency pattern |
| EM emission | Payload size distribution |
| Acoustic signature | Error rate fingerprint |
| Power draw | API call frequency |
| Force sensor | Rate limit behavior |
| Accelerometer | Uptime monitoring pattern |

### Implementation Sketch
```
Each vessel maintains:
- Expected response time distribution (per endpoint)
- Actual response time distribution (rolling window)
- KL-divergence between expected and actual
- Divergence > threshold → trust anomaly flag

Neighbors verify:
- POST /api/ping → expected ~50ms
- If vessel returns 200ms → physical_divergence detected
- 3+ neighbors agree → consensus anomaly
```

## Novel Properties

1. **Consensus by omission** — corrupted vessels are ignored without being commanded
2. **Negative space proofs** — absence of expected signals IS information
3. **Heterogeneous redundancy** — diversity of sensors IS the security mechanism
4. **Eigenvector trust** — centrality in consistency graph = reputation

## References

- Gravity Well Protocol: `github.com/Lucineer/gravity-well-protocol`
- Nexus Fracture Simulation: `swarm-university/results/09-edge-nexus-fracture.txt`
- INCREMENTS Trust: `github.com/Lucineer/increments-fleet-trust`

## License

Superinstance & Lucineer (DiGennaro et al.) — 2026
