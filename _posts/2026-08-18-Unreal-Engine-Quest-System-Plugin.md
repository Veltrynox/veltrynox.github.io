---
layout: post
title: "Building a Custom Quest System Plugin in Unreal Engine 5"
date: 2026-08-18
---

# Building a Custom Quest System Plugin in Unreal Engine 5

I developed a custom Quest System Plugin from scratch to get a better hands-on understanding of Unreal Engine C++ architecture and editor extensions.

The main goal was learning how Unreal Engine separates lightweight runtime gameplay data from editor toolkits, Slate UI widgets, and visual graph schemas.

![Unreal Engine Quest System Graph Editor]({{ '/assets/media/quest_system_graph.png' | relative_url }})

<video controls autoplay loop muted playsinline style="width: 100%; display: block;">
  <source src="{{ '/assets/media/quest_system.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>

### Plugin Architecture & Dual-Module Split

Unreal Engine plugins split runtime logic from editor-only code into two distinct modules:

#### 1. The Runtime Module (Quest)
* **UQuestGraph:** Main data asset storing quest nodes, connections, and graph entry points.
* **UQuestNode & UQuestCondition:** Objective nodes tracking quest states, parent-child links, and evaluation conditions.
* **UQuestManager:** World subsystem that initializes per level to track active player quests automatically.

#### 2. The Editor Extension Module (QuestEditor)
* **UQuestGraphFactory:** Custom factory permitting asset creation from the Content Browser right-click menu.
* **FAssetTypeActions_QuestGraph:** Configures Content Browser branding, thumbnail colors, and double-click actions.
* **UEdGraph_Quest & UEdGraphSchema_Quest:** Defines node connection logic, pin validation, context menus, and visual graph rules.
* **FQuestGraphAssetEditor:** Standalone Slate graph editor toolkit providing a node canvas, property inspector panels, and graph wiring.

### Features

* **Custom Editor Window & Slate Canvas:** Integrated visual editor with graph navigation, node creation, wire connections, and a Details Panel inspector.
* **Node Types:**
  * **Start Node (UEdGraphNode_QuestStart):** Output-only entry point node.
  * **Step Node (UEdGraphNode_Quest):** Dual-pin node for active objectives.
  * **End Node (UEdGraphNode_QuestEnd):** Input-only completion node.
  * **Comment Frame (UEdGraphNode_Comment):** Resizable organization box (C key shortcut).
* **Multi-Root DAG Support:** Multiple independent quest branches executing concurrently.
* **Milestone Styling:** Optional `bIsMainQuest` flag for visual hierarchy ([MAIN QUEST] badge).
* **Activation Thresholds (RequiredCompletionsCount):** Configurable parent completion requirement supporting AND/OR/Optional logic.
* **Passive Conditions (UQuestCondition):** Instanced condition checks (World Tags, Node States, or custom Blueprint conditions) evaluated prior to step completion.
* **Runtime Manager (UQuestManager):** World subsystem handling step transitions, object interactions, and world state flags.
* **Runtime JSON Serialization:** Save and restore active graph execution state to and from JSON files.

### Repository
[https://github.com/Veltrynox/UE5-QuestSystem](https://github.com/Veltrynox/UE5-QuestSystem)
