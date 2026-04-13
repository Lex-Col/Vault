# 🔒 THE SOVEREIGN IP VAULT (SIPV): MASTER GLOSSARY
### In-Depth Architectural Definitions & Hardware Taxonomy (v1.0)

**Architect:** Alexander Colclough (@Lex-Col)
**Classification:** PROPRIETARY — AUDIT-GRADE CANONICAL

---

## 🏗️ 1. TOPOLOGY & HARDWARE ZONES

* **A/B Partitioning:** The unyielding hardware rule of "Never Overwrite Live." Incoming data is written to a staging area (Partition B). The system only flips the master pointer to the live state after both the Sentry and Warden cryptographically sign off.
* **AXI Data Bridge:** The physical hardware bus and transit pathway connecting the secure EL2 control plane to the isolated vault.
* **Mantle Buffer (0x88100000):** The physical Battery-Backed RAM (BBRAM) holding the recovery path. It maintains Slot A (Live) and Slot B (Staging) and is mathematically sealed against tampering via HMAC-SHA384.
* **Vault Realm (0x80000000):** The hardware-write-protected (WP#) memory boundary. It houses the immutable Production IP Ledger and the isolated incoming staging area.
* **Warden Realm:** The Secure EL2 Control Plane. It operates as the ultimate hardware gatekeeper and A/B partition switcher, anchored directly to the Architect's Root of Trust (RoT).

## 🔑 2. AUTHENTICATION & ACCESS

* **Agency Key (Delegated):** The consumer-friendly resurrection mechanism. A hashed key—`HMAC(RoT_Secret, User_Auth_Hash)`—used to seamlessly drop the AXI bridge back down and restore connection after a Coma, without exposing the deepest hardware secrets.
* **Five Sign (Ignition):** The ECDSA-P384 challenge-response sequence. It is the absolute only mechanism capable of lifting the system from an Absolute Zero, inert state.
* **Instruction-Zero (BHB Flush/RSB Stuffing):** The bodyguard logic executed simultaneously with the Five Sign. It flushes the Branch History Buffer and stuffs the Return Stack Buffer to kill speculative data leakage before cryptographic verification even begins.

## 🚇 3. TRANSIT & THE JET SMUGGLER

* **Jet Smuggler:** The high-speed, polymorphic transit protocol that moves 384-byte AXI-aligned parcels across the data bridge using morphing encryption.
* **Randomized ABC Pulses:** The core evasion mechanic of the Jet Smuggler. Transit isn't a straight line; the physical routing is dynamically randomized and bounced between **Node A, Node B, and Node C** (operating like a randomized engram drop matrix in Destiny). This non-linear shifting mathematically eliminates the ability of an external interceptor to track or reconstruct the bus telemetry.
* **Pulse Key:** The unique, one-time encryption key generated for every single pulse: `HKDF_SHA384(Master_Key, Salt=RNG_Seed, Info=Pulse_Nonce)`.
* **Sliding Window:** A 16-pulse buffer designed to absorb hardware jitter. It allows the Sentry to self-heal dropped packets on the fly without killing the entire secure connection.

## 👁️‍🗨️ 4. VERIFICATION & FAIL-SAFES

* **Absolute Zero Reset:** A total, unrecoverable system halt triggered if the Mantle Buffer's HMAC tag fails verification (a critical "Tamper" event indicating physical intrusion).
* **Cryptographic Coma (The Drawbridge):** The non-destructive fail-safe reaction. If a heartbeat times out (>100ms) or the Sentry flags an anomaly, the Warden executes an immediate physical severance of the AXI bridge in $\leq 1$ CPU instruction. The Host OS continues running, but the Vault is entirely severed and isolated until manually resurrected via the Agency Key. Zero data is bricked; the bridge is simply dropped.
* **Fixed Latency Pad ($T_{max}$):** The IP Sentry's anti-side-channel armor. Whether verification takes 2ms or 10ms, the hardware pads the execution to return the flag at exactly $T_{max}$ cycles, ensuring zero timing variance to outside observers.
* **IP Sentry:** The blind auditor. An isolated sub-realm that processes incoming parcels in transient memory and communicates its verdict back to the Warden using only a strictly binary 1-bit hardware GPIO (`1` = Verified, `0` = Rejection).

---
**Copyright © 2026 Alexander Colclough (@Lex-Col). ALL RIGHTS RESERVED.**
