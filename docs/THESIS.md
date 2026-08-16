# Thesis

**Classic approach:**  
Obtain Firehose programmer → rewrite GPT → install custom partitions / dual-boot.

**Problem on current flagships:**  
Programmers are missing or authenticated, bootloader unlock is restricted, and the storage controller is protected.

**We still want the classic capability.**  
Full GPT rewriting (shrink, create, rearrange) remains a hard goal on any device where low-level write access can be obtained. Our partitioner is designed to give the same class of choices as GParted.

**Proposed complementary approach – Bubbles:**  
Obtain any elevated foothold → capture the entire original system → shrink it to minimum or custom size → place it inside a virtual bubble under a host environment we control.

The original OS stays intact and untouched inside the bubble.  
All remaining space becomes the user’s playground.  
From the outer environment the user can load untraditional operating systems and tools without destroying the original.

**Android-as-Guest** is the specific application of this model to modern locked Android devices using Gunyah / AVF / pKVM.

**Boot Stomp** is the component that controls how the outer environment boots and how it interacts with the contained original system.

This repository exists to state these goals clearly and to test whether both the direct GPT path and the Bubbles containment path can be made real.
