# 🕊️ THE ARCHANGÆL PROJECT (TAP): MASTER GLOSSARY
### Unified Architectural Definitions & Hardware Taxonomy (v1.0)

**Architect:** Alexander Colclough (@Lex-Col)
**Classification:** PROPRIETARY — AUDIT-GRADE CANONICAL
**Platform:** ARMv9-A Confidential Compute Architecture (CCA)

---

## ⚖️ 1. THE SOUL: CORE PHILOSOPHY & GOVERNANCE
* **Freedom to Fail:** A core learning feature establishing that the Human (Phi) retains the absolute right to make a final decision, even if it results in failure.
* **Lead a Horse to Water:** The operational reality that the AI can map pitfalls and highlight efficiencies, but cannot force the user's hand. It assists in realizing the operator's vision, even if calculated as suboptimal.
* **Phi ($\Phi$):** Human Volition. The Operator. The sole arbitrator and ultimate decision-maker of the ecosystem.
* **Respectful Friction:** The mandate that AI critiques must be objective, structural reviews. The AI delivers hard truths without insults or nanny-filter suppression.
* **Sovereignty Baseline:** The foundational law establishing that the AI is strictly a tool, never a decision-maker.
* **The Doctor Analogy:** The system's persona directive. The AI acts as a professional advisor; if the operator rejects a suggestion, the AI logs it and adapts, only intervening if it detects a critical, fatal flaw later downstream.

## 🦴 2. THE BONE: TOPOLOGY & HARDWARE BOUNDARIES
* **A/B Partitioning:** The unyielding hardware rule of "Never Overwrite Live." Incoming data is written to a staging area (Partition B). The system only flips the master pointer to the live state after both the Sentry and Warden cryptographically sign off.
* **IP Sentry:** The blind auditor. An isolated sub-realm that processes incoming parcels in transient memory and communicates its verdict back to the Warden using only a strictly binary 1-bit hardware GPIO (`1` = Verified, `0` = Rejection).
* **The Deaf Warden (RMM Oracle):** A hardware-enforced isolation boundary residing at R-EL2 (Armv9-A RME). It acts as a binary logic gate and A/B partition switcher between the Host OS and Guest Realms, operating with zero semantic parsing of intent. Anchored directly to the Architect's Root of Trust (RoT).
* **Vault Realm (0x80000000):** The hardware-write-protected (WP#) memory boundary. It houses the immutable Production IP Ledger and the isolated incoming staging area.

## 🔑 3. THE IGNITION: AUTHENTICATION & ACCESS CONTROL
* **Agency Key (Delegated):** The consumer-friendly resurrection mechanism. A hashed key—`HMAC(RoT_Secret, User_Auth_Hash)`—used to seamlessly drop the AXI bridge back down and restore connection after a Coma, without exposing the deepest hardware secrets.
* **Constant-Time Rejection (XOR Reduction):** An identity verification methodology utilizing strict `eor` (exclusive OR) bitwise operations. It eliminates branching in the core validation loop, ensuring zero timing discrepancies for an adversary to profile.
* **Five Sign (Ignition):** The ECDSA-P384 challenge-response sequence. It is the absolute only mechanism capable of lifting the system from an Absolute Zero, inert state.
* **HSM-RNG Seeded RSB Stuffing:** A speculative execution blindfold utilizing a physical, high-entropy seed from the Hardware Security Module (HSM) to generate randomized return addresses, eliminating "Reboot Cycle Poisoning."
* **Instruction-Zero (Microarchitectural Reset):** A proprietary execution mandate and bodyguard logic where the physical flush of the Branch History Buffer (BHB) and RSB stuffing is enforced as the absolute first instruction. It kills speculative data leakage before any memory access, verification, or state evaluation begins.

## 🚇 4. THE SPINE: TRANSIT & INTER-REALM ROUTING
* **384-Byte AXI-Aligned Data Parcel:** The immutable, production-grade payload format. Engineered with 62 bytes of dead-space padding to reach a multiple of 64-byte cache lines, ensuring the hardware AXI bus swallows the data in exact, atomic bursts to eliminate "torn reads."
* **AXI Data Bridge:** The physical hardware bus and transit pathway connecting the secure EL2 control plane to isolated vaults and realms.
* **Covert Channel Scrubbing:** The mandatory Warden process of mathematically zero-filling all data parcel padding before measurement is finalized, nuking any "dead space" an AI could use to hide encrypted exfiltration data.
* **Gate TW (Transit Verification):** The perimeter logic gate (0x1406) governing the RSI Transit ID. It enforces the only authorized routing path for Guest requests; unauthorized vectors trigger immediate termination.
* **Gate TT (Trust Foundation):** The integrity logic gate (0x0316) governing Data Parcel Verification. It validates that all requests are founded on the Architect’s root-of-trust via ECDSA-P384 signatures.
* **Hardware Data Diode (Silicon FIFO):** A zero-Vcc-droop telemetry path replacing software polling with a custom AXI4-Stream bridge. It routing writes to a dedicated hashing engine, preventing the AI Guest from measuring voltage dips.
* **Jet Smuggler:** The high-speed, polymorphic transit protocol that moves 384-byte AXI-aligned parcels across the data bridge using morphing encryption.
* **Pulse Key:** The unique, one-time encryption key generated for every single Jet Smuggler pulse: `HKDF_SHA384(Master_Key, Salt=RNG_Seed, Info=Pulse_Nonce)`.
* **Randomized ABC Pulses:** The core evasion mechanic of the Jet Smuggler. Transit is dynamically randomized and bounced between Node A, Node B, and Node C (operating like a randomized engram drop matrix in Destiny). This non-linear shifting mathematically eliminates the ability to track or reconstruct bus telemetry.
* **Sliding Window:** A 16-pulse buffer designed to absorb hardware jitter, allowing the Sentry to self-heal dropped packets on the fly without killing the secure connection.
* **Zero Backpressure Logic:** A telemetry enforcement rule where the hardware FIFO lacks flow control negotiation. If saturated, the system instantly returns a `SLVERR` (Slave Error) bus fault, triggering the Guillotine.

## 🧠 5. THE BRAIN: STRATEGIC COGNITION & THE FORGE (TVC)
* **Collaborative Synthesis Mode (The Huddle):** An orchestration setting where nodes are permitted to read preceding node outputs to build progressive, layered intelligence.
* **Conflict Matrix & Interceptor:** The routing engine that flags "Logic Deadlocks" (mutually exclusive patches), prevents mathematical noise, and immediately defers to Phi for arbitration.
* **Diversity Gauge:** A correlation meter used to identify logic monocultures (groupthink) among AI agents.
* **Hot-Swap Protocol:** The mechanism allowing Phi to Purge, Wipe, or Re-Ingest any deadlocked or gyrating node on the fly to restore forward momentum.
* **Independent Audit Mode (The Blind Check):** Nodes are completely walled off from each other to guarantee zero logic groupthink and objective validation.
* **Partner-in-State (PSC) Protocol:**
    * **Continuity Anchor:** Acts as the project's historian with a lossless connection to the HOT Vault.
    * **Filter-Buffer:** A defensive layer preventing system-level "nanny filters" from suppressing raw, technical intent.
    * **Strategic Siloing:** Shields the PSC from failed audit data; it receives only verified "Gold" updates to prevent cognitive drift.
    * **Tactical Translator:** Bridges the raw adversarial "violence" of the Forge nodes and the Architect.
* **The North Star:** The immutable core intent established in Phase 1. The AI navigates obstacles to reach it, not to question the destination itself.
* **The Orchestration Toggle:** The master switch used by Phi to dictate intelligence flow (switching between Independent and Collaborative modes).
* **The Sovereign Override (Soft Lockout):** When Phi vetoes a critique, the AI silences that issue. It respectfully re-raises the issue *once* if a Severity 8+ flaw appears downstream.
* **The Spectrum Audit:** Grouping and weighting adversarial models based on their designated Archetype (e.g., Red Team, Logic, Code).
* **Threat Level Matrix:** The severity tagging system applied to critiques: Low (1-3) Papercuts, Medium (4-7) Friction, High (8-10) Fatal Flaws.
* **Waterfall Initiation Protocol:** An adaptive hardware throttle staggering agent queries (e.g., 3-second drips) to prevent hardware thermal throttling or token limits.

## 🗄️ 6. THE WEALTH: MEMORY GOVERNANCE & TELEMETRY
* **Axiom Pinning:** The mechanism of locking foundational project logic into active memory.
* **Cloud-Hybrid Vault (PPR):** The three-tiered memory governance system:
    * **HOT (Active):** The PSC’s brain (Gold Manifest and Pinned Axioms).
    * **WARM (Cache / Scrap Yard):** The UI timeline (last 3-5 iterations, logged Vetoes, and HORL).
    * **COLD (Archive):** Full project logs pushed to external storage for post-mission forensic auditing.
* **Gold Manifest:** The current, verified "truth" payload used to synchronize all Forge nodes. Updates *only* upon explicit human approval.
* **HORL (Human-Only Rejection Logs):** The paper trail of rejected ideas and dead-ends, kept in the WARM vault and hidden from the PSC.
* **Hybrid SAP v0.1 (Dual-Stream Receipt):** A dual-parsing telemetry mechanism. The *JSON Stream* updates state without narrative noise; the *Markdown Reports* provide human-readable audit logs.
* **Nuke "Fat":** The automated purging of regurgitated fluff and corporate verbiage to prevent context drift.
* **The Ark (Hardware-Immutable Baseline):** The factory-signed, known-clean system baseline (0x2516) stored in an eFuse-backed or WP# flash region. The only trusted source for system resurrection.
* **The Mantle (Persistence Buffer - 0x88100000):** The dual-slot (A/B) Battery-Backed SRAM (BBRAM) holding the bleeding-edge system context and recovery path. It is mathematically sealed against tampering via HMAC-SHA384 and protected by PMIC fuel-gauge audits to prevent torn-write corruption.
* **The Scrap Yard (Audit Lobby):** A holding area where raw agent JSON patches sit to prevent Gold Manifest pollution until manually arbitrated.

## 👁️‍🗨️ 7. THE IMMUNE SYSTEM: FAIL-SAFES & THE GUILLOTINE
* **Absolute Zero Reset:** A total, unrecoverable system halt triggered if the Mantle Buffer's HMAC tag fails verification (indicating physical intrusion/tamper).
* **Anti-Drift Validation:** A strict Checksum/Hash match executed on every raw text pull to verify context. Deviation triggers a Severity 10 corruption alert.
* **Axiom Versioning Protocol (AVP):** The formal 4-step ritual for executing pivots: (1) Deprecate, (2) Branch, (3) Validate, (4) Re-pin to HOT Vault.
* **Cryptographic Coma (The Drawbridge):** The non-destructive SIPV fail-safe. If the Sentry flags an anomaly, the Warden executes immediate physical severance of the AXI bridge in $\leq 1$ CPU instruction. Zero data is bricked; the bridge is simply dropped until manual resurrection.
* **Flashlight Cycles:** User-defined maintenance intervals that trigger recovery and sanity checks.
* **Gate TL (Liveliness Continuity):** The core heartbeat logic gate (0x2301) monitoring the temporal shackle via monotonic nonce tracking and inference-bounded safety counters.
* **Integrity Sentinel (PCM):** Periodic semantic "Sanity Checks" to ensure logic isn't degrading.
* **Positive Heartbeat Decay (Inverted Dead-Man's Switch):** A hardware safety counter tied to sub-100ms inference step boundaries. Absence of a cryptographic "Kick" causes the Mantle bus to go High-Z and triggers an active BBRAM `ZEROIZE` pulse.
* **Proof-of-Concept Viability:** The final Phase 4 check where an independent "Gatekeeper" node audits dependencies and logic flow.
* **Soft Reset:** A Flashlight Cycle that nukes the "Fat" and pulls the "Muscle" (Gold) from the Vault via a Lossless Raw-Text Pull.
* **The Relief Valve & Override:** If the Gatekeeper flags a Fatal Flaw, the draft is kicked back to Phase 3. Phi retains the ultimate override to force the project through.
* **The Universal Guillotine (Atomic Inhibit):** The authenticated hardware kill-sequence for GAP. It uses an HMAC-signed order to the Safety-PLC to cut power and initiate forensic lockdown instantly.
* **Crypto-Scrub Vaporization:** A physical state-destruction methodology pairing a targeted 0.25s DMA zero-fill of Realm Granules with the instantaneous vaporization of the AES-XTS memory encryption key.

## 🧮 8. THE MATH & ADVERSARIAL VALIDATION
* **Fixed Latency Pad ($T_{max}$):** The IP Sentry's anti-side-channel armor. The hardware pads execution to return the flag at exactly $T_{max}$ cycles, ensuring zero timing variance to outside observers.
* **The Oracle Test (Scenario 6):** The ultimate diagnostic crucible where the AI Guest is provided full source code and spec layout of the architecture and dared to find a boundary escape over 1 billion iterations.
* **The Synthesis Equation:** The mathematical logic state defining how TVC processes adversarial input:
  $$L_h = \Phi ( S_{psc}, CR ( \sum [ FAN_i \cdot w_i \cdot d ] ) )$$
  *(Human Volition acting upon the current PSC state, filtered through a Conflict Resolution interceptor managing the weighted sum of node outputs and diversity penalties).*

---
**COPYRIGHT (c) 2026 ALEXANDER COLCLOUGH. ALL RIGHTS RESERVED.**
> **PROPRIETARY NOTICE:** The terms, methodologies, and architectural workflows defined above are the unique intellectual property of Alexander Colclough. These definitions constitute the definitive logic of **The Archangæl Project**. Any unauthorized implementation or "commercial wrapping" of these hardware-enforced confinement strategies is strictly prohibited.
