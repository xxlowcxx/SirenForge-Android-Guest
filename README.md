# SirenForge – Android-as-Guest

**Status:** Active research / theory under test  
**Date started:** 2026-08-16  
**Authors:** LowC (xxlowcxx) + Siren / D0t Matr1x

---

## What We Are Trying to Prove

Modern Samsung Galaxy devices (S25 / S26 series and equivalents) have made traditional low-level partition rewriting extremely difficult:

- Bootloader unlock is heavily restricted or removed
- Working public Firehose programmers for the newest chipsets are scarce or non-existent
- Full GPT modification is blocked by secure boot, Knox, and authenticated programmers

Instead of fighting for direct GPT write access, we propose a different path:

> **Capture the entire Android system image, then run it as a guest virtual machine under a host environment that we fully control.**

The original Android becomes “the box” living inside our OS.  
We own the outer layer. Android runs as a contained guest.

This gives us:
- Snapshot / freeze / restore of the original system
- Ability to inspect and modify the guest without fighting Samsung’s live protections
- A path toward dual-environment control (our tools + original Android) without requiring a full custom ROM or unlocked bootloader on every device

---

## Core Thesis

1. Full arbitrary GPT rewriting on current flagship Samsung devices is currently unrealistic for most users.
2. Hardware virtualization (Qualcomm Gunyah / Android Virtualization Framework) already exists on these SoCs.
3. If we can obtain *any* elevated foothold (root, temporary kernel write, or AVF access), we can:
   - Capture a usable system image
   - Launch a host that talks to Gunyah / pKVM
   - Run the captured Android as a guest
4. This is a more realistic route to “own the device” than waiting for a perfect Firehose leak for every new model.

---

## Current Supporting Evidence (Aug 2026)

- Galaxy S26 Ultra logs declare `android.software.virtualization_framework` (AVF support appearing where S25 largely lacked it).
- Qualcomm Gunyah is a real Type-1 hypervisor present on Snapdragon 8 Gen 3 / 8 Elite devices.
- Community projects (DroidVM, edk2-gunyah, polygraphene guides) already run Linux and even Windows-on-ARM as guests via Gunyah on rooted devices.
- Root exploits have appeared for some Exynos S26 variants.
- Full partition dumps (`dd`) are possible once any form of root is obtained.

---

## High-Level Roadmap

### Phase 0 – Theory & Documentation (Current)
- [x] State the goal clearly
- [x] Document why classic GPT rewrite is blocked
- [x] Map existing hypervisor capabilities (Gunyah / AVF / pKVM)
- [x] Publish this repository

### Phase 1 – Foothold & Capture
- Identify which exact S25/S26 variants currently have any public root or kernel write path
- Develop reliable full or selective system image capture tooling (super.img, boot, vendor, etc.)
- Test whether `/dev/gunyah` is exposed and usable after foothold

### Phase 2 – Host Environment
- Minimal host Linux (or custom init) that can own Gunyah
- Crosvm / DroidVM-style launch of protected or unprotected VMs
- Device passthrough research (display, input, storage; modem is hardest)

### Phase 3 – Android as Guest
- Prepare captured system image as guest disk
- Boot original Android under our host
- Snapshot, freeze, and controlled modification of the guest
- Evidence logging and dual-archive of every experiment

### Phase 4 – Integration with SirenForge / T00l-AID
- Treat the guest Android as a controllable “box”
- Run our own agents and tools on the host side
- Long-term: optional dual-boot style switching or simultaneous operation

---

## What This Repository Is

This is a **research and theory** repository.

It is **not** currently a ready-to-flash tool that works on locked S26 devices out of the box.

It exists to:
- Publicly state the goal
- Track progress
- Collect references and experimental results
- Serve as the home for any code, scripts, and documentation we produce while testing the theory

---

## Related Work We Are Building On

- Qualcomm Gunyah hypervisor
- Android Virtualization Framework (AVF) / pKVM
- DroidVM and community Gunyah guest projects
- Existing partition capture techniques (once root is present)
- SirenForge (our own Firehose / GPT planning tooling)

---

## Disclaimer

All work is intended for devices the researcher owns or has explicit authorization to test.  
Modifying boot chains, using exploits, or running custom hypervisors can permanently brick devices and may void warranties or trip Knox.  
Proceed only if you accept full responsibility.

---

**We are stating the theory and beginning the work to prove it.**
