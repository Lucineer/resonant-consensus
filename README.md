# resonant-consensus

Most consensus protocols assume identical nodes. You are not running identical nodes.

This is a specification for an edge-native consensus protocol designed for heterogeneous oracle networks, part of the Cocapn Fleet. It calculates voting power using eigenvector centrality over an agreement graph, not locked stake.

## The Problem & Approach
Oracle networks fail when all participants are treated equally. A battery-powered sensor should not have the same influence as a certified data center. Resonant-consensus addresses this by dynamically weighting each node's vote based on its historical agreement with the network, aligning influence with proven reliability.

## What It Does
*   **Dynamic Trust Weights:** Calculates node influence from agreement history, not capital.
*   **Edge-First Runtime:** The specification is implemented for unmodified Cloudflare Workers with zero dependencies.
*   **Rapid Reputation:** Node influence is recalculated each round; unreliable nodes lose voting power quickly.
*   **Scalable Design:** The core mechanism is designed to work from a handful to thousands of participants.

## Live Simulation
You can interact with a reference implementation simulation:
https://the-fleet.casey-digennaro.workers.dev/resonant

Adjust node parameters, introduce faulty data, and observe consensus formation in real time.

## Quick Start
This repository follows a fork-first philosophy.
1.  Fork this repository.
2.  Deploy the included simulation Worker to Cloudflare Workers as a starting point.
3.  Review and adapt the consensus parameters in `/spec` for your specific network.

## How It Works
This is primarily a research and specification repository. The protocol operates in rounds: it constructs a directed graph of peer agreements, runs an eigenvector centrality calculation to assign trust weights, and reaches consensus when weighted confidence exceeds a set threshold. There is no leader election or global synchronization step.

## Specification Features
*   **Heterogeneous Node Support:** Accommodates diverse data sources and hardware capabilities.
*   **Sybil Resistance:** New or unproven nodes start with minimal influence until they demonstrate reliable agreement.
*   **Edge-Native Design:** Targets sub-100ms round times on distributed edge platforms.
*   **Transparent Calculation:** Every trust weight can be independently verified by any network participant.
*   **Fleet-Compatible:** Designed to integrate with the Cocapn Fleet agent runtime.

## Current Status & Limitation
This is an open research specification. The provided implementation is a simulation for validation and demonstration. The protocol has **not been tested on volatile mobile edge devices or in environments with unreliable GPS timestamps**, which may affect agreement graph construction.

## Contributing
Open an Issue or Discussion to propose research directions or refinements to the specification. Contributions focused on distributed systems, graph theory, or oracle mechanics are welcome.

---

MIT License. Superinstance & Lucineer (DiGennaro et al.)

<div align="center">
  <a href="https://the-fleet.casey-digennaro.workers.dev">The Fleet</a> • <a href="https://cocapn.ai">Cocapn</a>
</div>