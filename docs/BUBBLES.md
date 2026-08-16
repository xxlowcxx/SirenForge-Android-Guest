# Bubbles

**Bubbles** is the high-level concept for treating an entire operating system and its files as a movable, shrinkable object.

## What it does

1. Takes the entire target drive / OS / files.
2. Shrinks that original system down to the smallest practical size, or to a size the user chooses.
3. Places the shrunk original inside a virtual bubble (virtual disk / VM / contained image).
4. Leaves all remaining free space under the user’s control — the playground.
5. Keeps the original system intact and functional inside the bubble.
6. Allows the outer environment (and tools such as Boot Stomp) to load untraditional operating systems or custom environments alongside the contained original.

## Design principles

- The original system is not cracked or destructively modified.
- The original is preserved as a complete object inside the bubble.
- The user becomes the controlling layer around that object.
- Partitioning-style choices (layout, size, free space) are still available; Bubbles is the higher-level model that uses those capabilities when they exist and falls back to containment when they do not.

## Relationship to other components

- **SirenForge Partitioner** supplies the low-level layout decisions when write access is available.
- **Android-as-Guest** is Bubbles applied specifically to captured Android system images running under Gunyah / AVF.
- **Boot Stomp** handles boot and interaction between the outer environment and the bubble.

Bubbles is the unifying idea: the original OS becomes an object in a universe the user controls.
