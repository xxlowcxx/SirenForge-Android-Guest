# Roadmap – SirenForge Android-as-Guest

Last updated: 2026-08-16

## Phase 0 – Foundation (Now)
- [x] Publicly state the goal and thesis
- [x] Create this repository
- [x] Document why classic full-GPT rewrite is currently blocked on S25/S26
- [x] Summarize Gunyah / AVF / DroidVM landscape

## Phase 1 – Access & Capture
- [ ] Catalogue exact models with any public root / kernel write path (Exynos S26 priority)
- [ ] Build or adapt reliable partition / super.img capture scripts
- [ ] Test presence and usability of `/dev/gunyah` after foothold
- [ ] Record which devices expose usable AVF / Gunyah interfaces

## Phase 2 – Minimal Host
- [ ] Select or build minimal host environment capable of talking to Gunyah
- [ ] Achieve successful launch of a simple guest (Microdroid or Debian) via crosvm
- [ ] Measure performance and stability
- [ ] Begin device passthrough experiments (display + input first)

## Phase 3 – Android Guest
- [ ] Convert captured system image into a bootable guest disk layout
- [ ] Boot original Android under controlled host
- [ ] Implement snapshot / freeze / restore
- [ ] Evidence logging of every guest session

## Phase 4 – Siren Integration
- [ ] Host-side agent control of the guest
- [ ] Dual-archive of captures and experiment logs
- [ ] Long-term architecture for “host owns the phone, Android is the box”

## Success Criteria (Proof of Theory)
We consider the core theory proven when:

1. We can reliably capture a usable system image from a target device after obtaining a foothold.
2. We can boot that image (or a significant portion of it) as a guest under a host we control via Gunyah/AVF.
3. The host retains the ability to snapshot, inspect, or replace the guest without needing continuous low-level Firehose access.

## Non-Goals (for now)
- Universal one-click tool for every locked S26 out of the box
- Full modem / Secure Element passthrough in the first versions
- Claiming this replaces classic unlock methods where those still exist
