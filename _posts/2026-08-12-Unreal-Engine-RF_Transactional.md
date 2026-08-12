---
layout: post
title: "Unreal Engine Object Flags: Understanding RF_Transactional"
date: 2026-08-12
---

# Unreal Engine Object Flags: Understanding RF_Transactional

### 1. What Does RF_Transactional Stand For?
In Unreal Engine C++, object flags control object lifecycles, serialization, and editor behaviors.

* **RF_** = **Runtime Flag** (Bits defined in the `EObjectFlags` enumeration).
* **Transactional** = **Capable of participating in Undo and Redo operations**.

In software engineering, a transaction is an action that can either be committed permanently or completely rolled back using Ctrl+Z.

### 2. Why Do We Need This Flag for Objects?
Unreal Engine constructs millions of transient objects at runtime (projectiles, enemy AI states, particle systems). By default, to save memory and performance, the engine does not track modification history for standard objects.

However, inside the Unreal Editor, designers constantly edit graph nodes, property values, and level assets, expecting Ctrl+Z (Undo) and Ctrl+Y (Redo) to work reliably.

When creating a custom object with the `RF_Transactional` flag:

```cpp
UQuestNode* NewNode = NewObject<UQuestNode>(InParent, InClass, InName, Flags | RF_Transactional);
```

This flag tells Unreal Engine to record all property modifications and lifecycle state changes for this object into the system Undo Buffer.
