# GLOSSARY: THE LATTICE GATES (PILLAR 3: TGL HARDWARE)
### Arcangel Project // Axiom OS PPA Documentation

**Architect:** Alexander Colclough (@Lex-Col)
**System Status:** Sovereign // Zero-Friction Determinism
**Classification:** Triune Gate Lattice Hardware Instantiations

---

## I. TEMPORAL GATE (TW_GATE)
* **TW_GATE:** The first hardware instantiation in the Lattice, functioning as the primary temporal warden.
* **skew_limit (2'd2):** The strict 2-picosecond threshold parameter hardcoded into the gate; signals exceeding this limit are rejected.
* **hardware_mute:** An output line (tgl_muted) that permanently disables system consensus if the temporal gate detects critical failure.

---

## II. NONLINEAR GATE (TT_CRUCIBLE)
* **TT_CRUCIBLE:** The second hardware instantiation, responsible for nonlinear consistency audits on the sharded payload.
* **sbox_parallel (6'd64):** The hardware parameter defining 64 parallel substitution boxes deployed to audit the optical signal.
* **harmonic_null (8'h00):** The exact baseline value (hardware zero) required for the signal to pass the Crucible's validation check.

---

## III. TRINITY GATE (TL_WARDEN)
* **TL_WARDEN:** The final hardware gate instantiation in the Lattice that serves as the ultimate arbiter before consensus.
* **ceremony_beats (6'd36):** The required 36-beat temporal ceremony that the signal must complete perfectly to unlock the gate.
* **byte_alignment (16'd777):** The strict 777-byte physical resonance signature required for the light to penetrate the final warden.

---

## IV. STATE MONITORING
* **gate_status [2:0]:** A 3-bit hardware registry tracking the pass/fail state of the TW, TT, and TL gates respectively.
* **gate_passed:** The internal boolean signal emitted by each individual gate upon successful signal traversal.

---

## V. LEGAL & INTELLECTUAL PROPERTY NOTICE
**Copyright © 2026 Alexander Colclough (@Lex-Col). All Rights Reserved.**
The Pillar 3 Lattice Gates architecture, including the TW_GATE 2ps skew limit, TT_CRUCIBLE harmonic null checks, and TL_WARDEN 36-beat ceremony logic, is the exclusive intellectual property of Alexander Colclough. Unauthorized duplication or reverse-engineering is strictly prohibited.
