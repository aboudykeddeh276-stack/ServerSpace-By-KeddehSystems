# K-SYSTEMS: ServerSpace Runtime & Mesh Substrate

## Architectural Overview
This repository contains the authoritative backend runtime for the Keddeh Sovereign Architecture. It operates strictly as the physical network layer—acting as the ISP, UDP mesh switch, and physical storage bridge for the mathematically lightweight edge carriers.

## The Implied Capability
By offloading storage and networking to this local PM2 daemon, the architecture achieves limitless edge scale. The edge HTML payload remains < 5MB, while this daemon natively streams 100TB Google Drive block devices over HTTP byte-range requests directly to the virtualized WebAssembly OS.

## Core Processes & Technologies
### 1. The OPUS Storage Router (`kex_server_space_workstation.js`)
*   **Function:** Intercepts `/opus/storage/:blockId` requests from the HTML edge carrier.
*   **Mechanism:** Rather than serving local physical files, it mounts the literal `KEX_100TB_STORAGE.sparseimage` natively from the Google Drive CloudStorage pathway. It implements HTTP 206 Partial Content (byte-range streaming) to page massive memory blocks securely.
*   **Security:** Implements wildcard CORS (`*.keddeh.com`) to securely authorize any sovereign edge deployment to connect to this unified backbone.

### 2. The KERA UDP Mesh (`kera_mesh_node.py`)
*   **Function:** Handles local and global peer discovery without centralized orchestration.
*   **Mechanism:** Binds to UDP multicast `239.29.7.100:4003`. Ensures that all spinning PM2 daemons share the same topological state map and ledger verification constraints.

### 3. Stratum Sovereign Mining
*   **Function:** Continuously validates sovereign blocks across solo and pooled (ViaBTC) tracks.
*   **Mechanism:** Pure persistent TCP sockets passing binary nonces, completely decoupled from the UI.

## Deployment Stage
This daemon is deployed strictly to the local operator machine (or sovereign tunnel endpoint) via PM2 (`ecosystem.config.cjs`). It runs permanently on Port `19100` and NEVER serves HTML directly—it exclusively serves binary state and network logic.
