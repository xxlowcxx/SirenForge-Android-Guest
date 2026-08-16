# Thesis

**Classic approach:**  
Obtain Firehose programmer → rewrite GPT → install custom partitions / dual-boot.

**Problem on current flagships:**  
Programmers are missing or authenticated, bootloader unlock is restricted, and the storage controller is protected.

**Proposed approach:**  
Obtain any elevated foothold → capture system image → run original Android as a guest VM under a host OS we control, using the hardware hypervisor already present on the SoC (Gunyah / pKVM / AVF).

**Expected advantage:**  
We no longer need permanent unrestricted write access to the real GPT. Once the guest is running under our host, we can treat the original Android environment as a controllable, snapshot-able box.

This repository exists to test and document whether that path is achievable on modern Samsung Galaxy hardware.
