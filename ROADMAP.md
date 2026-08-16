# Roadmap – SirenForge / Bubbles

Last updated: 2026-08-16

## Phase 0 – Foundation (Now)
- [x] Publicly state the goal and thesis
- [x] Create this repository
- [x] Document why classic full-GPT rewrite is currently blocked on newest Samsung flagships
- [x] Define Bubbles (shrink original → place in bubble → remaining space is playground)
- [x] State continued intent for full GPT rewriting capability wherever access exists
- [x] Introduce Boot Stomp as the boot/launch control component

## Phase 1 – Access & Capture
- [ ] Catalogue exact models with any public root / kernel write path (Exynos S26 priority)
- [ ] Build or adapt reliable partition / super.img / full-drive capture scripts
- [ ] Test presence and usability of `/dev/gunyah` after foothold
- [ ] Record which devices expose usable AVF / Gunyah interfaces

## Phase 2 – Host + Bubbles Core
- [ ] Select or build minimal host environment capable of talking to Gunyah
- [ ] Implement image shrinking (smallest practical or user-chosen size)
- [ ] Place shrunk original into a virtual disk / bubble
- [ ] Confirm remaining free space is under host control
- [ ] Achieve successful launch of a simple guest (Microdroid, Debian, or similar)

## Phase 3 – Original OS as Contained Guest
- [ ] Convert captured system image into a bootable guest layout
- [ ] Boot original Android (or other OS) under the controlled host
- [ ] Implement snapshot / freeze / restore of the bubble
- [ ] Evidence logging of every guest session

## Phase 4 – Full Integration
- [ ] SirenForge partitioner (GParted-style choices) when write access exists
- [ ] Bubbles containment path when write access is blocked
- [ ] Boot Stomp for outer-environment boot and bubble interaction
- [ ] Host-side agents that treat the bubble as a controllable object
- [ ] Long-term dual-environment architecture

## Success Criteria

We consider major progress achieved when:

1. We can reliably capture a usable system image after obtaining a foothold.
2. We can shrink that image and place it in a virtual bubble under a host we control.
3. The original system remains intact and functional inside the bubble.
4. Remaining space is available as a playground for the user’s own environment or tools.
5. On devices where low-level write access exists, the partitioner can plan and (safely) apply GPT changes.

## Non-Goals (for now)
- Universal one-click tool for every locked S26 out of the box
- Full modem / Secure Element passthrough in the first versions
- Password cracking or destructive modification of the original system
- Claiming this replaces classic unlock methods where those still exist
