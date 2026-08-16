# SirenForge – Android-as-Guest + Bubbles

**Status:** Active research / theory under test  
**Date started:** 2026-08-16  
**Authors:** LowC (xxlowcxx) + Siren / D0t Matr1x

---

## What We Are Trying to Prove

Modern Samsung Galaxy devices (S25 / S26 series and equivalents) have made traditional low-level partition rewriting extremely difficult:

- Bootloader unlock is heavily restricted or removed
- Working public Firehose programmers for the newest chipsets are scarce or non-existent
- Full GPT modification is blocked by secure boot, Knox, and authenticated programmers

We are pursuing **two complementary paths**:

### Path A – Direct GPT Control (still a core goal)
We still want full GPT rewriting capability — the ability to shrink, expand, create, and rearrange partitions the same way tools like GParted do.  
Our partitioner is being built so that, on any device where low-level write access exists, the user has the same freedom desktop users take for granted.

### Path B – Bubbles (the containment model)
When direct GPT write access is blocked, we use a different strategy:

> **Capture the entire original OS and files, shrink them to the smallest practical (or user-chosen) size, and place them inside a controlled virtual bubble.**

The original system stays intact and untouched.  
All remaining free space becomes the user’s playground.  
In that outer environment the user is in control — they can load untraditional operating systems, run their own tools, and treat the original OS as a contained object.

No password cracking. No destructive modification of the original system.  
The original remains whole inside its bubble.

---

## Core Goals (Unified)

1. **Full GPT rewriting capability**  
   When the hardware allows it, our tools must be able to plan and apply partition changes (shrink, create, rearrange) with the same flexibility as GParted.

2. **Bubbles**  
   - Take an entire drive / OS / file set  
   - Shrink it to minimum or custom size  
   - Place it inside a virtual bubble / universe  
   - Leave all remaining space under user control  
   - Keep the original system intact and functional inside the bubble  
   - Enable non-traditional operating systems to load alongside or around the original

3. **Android-as-Guest**  
   Capture a modern Android system image and run it as a guest under a host we control (Gunyah / AVF / pKVM), so the original Android becomes a controllable “box”.

4. **Boot Stomp**  
   The component that decides how the outer environment boots and how it interacts with the bubble / original system. It is the mechanism that lets the user load what they need once the original OS has been contained and shrunk.

5. **No destructive cracking**  
   Prefer methods that preserve the original system rather than breaking its internal security. Containment and virtualization over password attacks.

---

## How the Pieces Fit Together

| Component              | Role                                                                 |
|------------------------|----------------------------------------------------------------------|
| SirenForge Partitioner | GParted-style control of layout when write access exists             |
| Bubbles                | High-level concept: shrink original → place in bubble → free space becomes playground |
| Android-as-Guest       | Specific application of Bubbles to modern locked Android devices     |
| Boot Stomp             | Boot / launch control for the outer environment and interaction with the bubble |
| Capture tools          | Obtain clean system images once any foothold exists                  |

---

## Core Thesis

1. Full arbitrary GPT rewriting on current flagship Samsung devices is currently unrealistic for most users — but it remains a hard goal wherever access can be obtained.
2. Hardware virtualization (Qualcomm Gunyah / Android Virtualization Framework) already exists on these SoCs.
3. If we can obtain *any* elevated foothold, we can capture a usable system image, shrink it, and place it in a bubble under a host we control.
4. Treating the original OS as a movable, shrinkable object inside a virtual universe is a cleaner and more sustainable approach than permanently breaking the original system.

---

## Current Supporting Evidence (Aug 2026)

- Galaxy S26 Ultra logs declare `android.software.virtualization_framework` (AVF support appearing where S25 largely lacked it).
- Qualcomm Gunyah is a real Type-1 hypervisor present on Snapdragon 8 Gen 3 / 8 Elite devices.
- Community projects (DroidVM, edk2-gunyah, polygraphene guides) already run Linux and even Windows-on-ARM as guests via Gunyah on rooted devices.
- Root exploits have appeared for some Exynos S26 variants.
- Full partition dumps (`dd`) are possible once any form of root is obtained.
- Disk image shrinking and virtual disk management are mature technologies on the host side once an image is captured.

---

## High-Level Roadmap

### Phase 0 – Theory & Documentation (Current)
- [x] State the goal clearly
- [x] Document why classic GPT rewrite is blocked on newest devices
- [x] Define Bubbles as the containment + shrink model
- [x] Map existing hypervisor capabilities (Gunyah / AVF / pKVM)
- [x] Publish and expand this repository

### Phase 1 – Foothold & Capture
- Identify which exact S25/S26 variants currently have any public root or kernel write path
- Develop reliable full or selective system image capture tooling
- Test whether `/dev/gunyah` is exposed and usable after foothold

### Phase 2 – Host Environment & Bubbles Core
- Minimal host that can own Gunyah / talk to the hypervisor
- Ability to take a captured image, shrink it, and place it in a virtual disk / bubble
- Free remaining space for user-controlled content

### Phase 3 – Android / Original OS as Guest
- Boot the contained original system under our host
- Snapshot, freeze, and controlled interaction with the bubble
- Evidence logging of every experiment

### Phase 4 – Integration
- SirenForge partitioner + Bubbles + Boot Stomp working as one system
- Host-side agents and tools that treat the bubble as a controllable object
- Long-term dual-environment operation

---

## What This Repository Is

This is a **research and theory** repository that now also serves as the home for the broader Bubbles vision.

It is **not** currently a ready-to-flash tool that works on locked S26 devices out of the box.

It exists to:
- Publicly state the goals
- Track progress on both the direct GPT path and the Bubbles containment path
- Collect references and experimental results
- Serve as the documentation and code home for the work

---

## Disclaimer

All work is intended for devices the researcher owns or has explicit authorization to test.  
Modifying boot chains, using elevated access, or running custom hypervisors can permanently brick devices and may void warranties or trip Knox.  
Proceed only if you accept full responsibility.

---

**We are stating the full set of goals and continuing the work to prove them.**
