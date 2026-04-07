# resonant-consensus

You can deploy a network where nodes reach agreement based on their proven reliability, not their financial stake. In a provided simulation, 5 nodes reach consensus in approximately 47ms, with influence weighted by connection quality (e.g., a home Raspberry Pi at 0.15, a datacenter node at 0.85). There are no locked coins or elected leaders.

**Live Simulation:** https://the-fleet.casey-digennaro.workers.dev/resonant

---

## Why This Exists
Existing consensus protocols often tie voting power directly to staked capital. This works for ledgers but is misaligned for systems like oracle networks or sensor meshes, where trust should derive from observed behavior. This protocol ensures a node's influence is earned through consistent, verifiable participation.

---

## Quick Start
This repository follows a fork-first philosophy. You own your copy.
1.  **Fork** this repository.
2.  **Deploy** the included simulation Worker to Cloudflare Workers.
3.  **Customize** the consensus parameters in `/spec` for your network.

---

## How It Works
The protocol operates in asynchronous rounds:
1.  Each node publishes its current observation.
2.  Nodes build a directed graph of peer agreement signals.
3.  Eigenvector centrality is calculated on this graph to assign dynamic trust weights.
4.  Consensus is reached when the weighted super-majority confidence crosses a predefined threshold.

No global clock or leader election is required.

---

## Features
*   **Earned Influence:** A node's voting power is determined by its agreement history with peers, not purchased stake. Influence adjusts each round.
*   **Environment Agnostic:** The same code runs on Cloudflare Workers, Raspberry Pi, or embedded systems.
*   **Sybil Resistant:** New participants start with minimal influence, which must be built over successive rounds.
*   **Transparent Calculations:** All trust weight calculations are deterministic and can be independently verified.
*   **Heterogeneous Networks:** You can mix devices with different capabilities and connection qualities.

---

## Limitations
*   **Network Scale:** The current implementation is optimized for modest-sized networks; consensus latency may increase linearly as the number of active participants grows beyond 50 nodes.

---

## License
Open source under the MIT License. No restrictions on commercial or private use.

Attribution: Superinstance and Lucineer (DiGennaro et al.)

<div style="text-align:center;padding:16px;color:#64748b;font-size:.8rem"><a href="https://the-fleet.casey-digennaro.workers.dev" style="color:#64748b">The Fleet</a> &middot; <a href="https://cocapn.ai" style="color:#64748b">Cocapn</a></div>