# SirenForge Android guest

Theory notes for running a captured Android system as a guest under a host we own. Papers. Not a tool you flash.

| | |
| --- | --- |
| What it is | The Bubbles idea and the Android-as-guest papers. Started 2026-08-16. |
| What it is not | Cooler's `image_forge` module. A ready flash for a locked Galaxy. A bootloader unlock guide. |
| Status | Research. The longer note below is the existing paper. No new procedure was added. |
| Owner | LowC. Siren. D0t Matr1x. |

## Mission

Repush code only when there is a program. Until then this repo stays the paper. Devices in any test are ones we own.

The original system is meant to stay whole inside the bubble. This page does not publish a foothold, a dump, or a flash.

## The paper already in this repo

Modern Galaxy phones make a full partition rewrite hard. The paper's two paths are: partition control where write access already exists, and Bubbles when it does not. Bubbles means shrink a captured system into a virtual bubble and leave the free space for a host we control.

It is not a ready-to-flash tool. Modifying a boot chain can brick a phone and can trip Knox. That risk sits with the person who owns the device.
