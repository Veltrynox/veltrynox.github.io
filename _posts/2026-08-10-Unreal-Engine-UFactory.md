---
layout: post
title: "Custom Assets in Unreal Engine: Understanding UFactory"
date: 2026-08-10
---

# Custom Assets in Unreal Engine: Understanding UFactory

### What is UFactory and Why Do We Need It?
When building custom tools in Unreal Engine, you usually start by writing a C++ data class for your system. For example, if you are making a Quest System, you might create a `UQuestGraph` class. In Unreal Engine, `UObject` is the base C++ class for objects managed by the engine's memory and reflection system.

However, simply writing a C++ class inheriting from `UObject` only defines how your data exists in code. By default, Unreal Editor has no idea how to let designers create a new instance of your `UQuestGraph` asset when they right-click in the Content Browser.

This is where `UFactory` comes in. A `UFactory` is a dedicated Unreal Engine class that teaches the editor how to construct new asset instances in memory or import files from disk.

### Key Responsibilities of UFactory:
* **Asset Binding:** Tells Unreal Engine which C++ class the factory creates (`SupportedClass`).
* **Content Browser Integration:** Adds your asset option to the right-click context menu (`bCreateNew = true`).
* **Allocation:** Allocates the object in memory when created (`FactoryCreateNew()`).
* **Auto-Opening Editor:** Opens your custom editor window immediately after asset creation (`bEditAfterNew = true`).

### Editor Architecture and Class Interaction
![QuestGraph Editor Class Interaction Diagram]({{ '/assets/media/UE_UFactory.png' | relative_url }})

Looking at the diagram above:
* **UFactory (Yellow):** Handles object allocation in memory when requested by the Content Browser.
* **FAssetTypeActions_Base (Green):** Controls visual styling, thumbnail color tinting, category placement, and double-click opening behavior.
* **IModuleInterface (Blue):** Registers the asset type actions with `IAssetTools` when the editor module loads (`StartupModule()`) and unregisters them on shutdown (`ShutdownModule()`).

### Code Example: Implementing QuestGraphFactory

```cpp
// QuestGraphFactory.h
#pragma once

#include "CoreMinimal.h"
#include "Factories/Factory.h"
#include "QuestGraphFactory.generated.h"

UCLASS()
class QUESTEDITOR_API UQuestGraphFactory : public UFactory
{
	GENERATED_BODY()

public:
	UQuestGraphFactory();
	virtual UObject* FactoryCreateNew(UClass* InClass, UObject* InParent, FName InName, EObjectFlags Flags, UObject* Context, FFeedbackContext* Warn) override;
};
```

```cpp
// QuestGraphFactory.cpp
#include "QuestGraphFactory.h"
#include "Quest/QuestGraph.h"

UQuestGraphFactory::UQuestGraphFactory()
{
	SupportedClass = UQuestGraph::StaticClass();
	bCreateNew = true;
	bEditAfterNew = true;
}

UObject* UQuestGraphFactory::FactoryCreateNew(UClass* InClass, UObject* InParent, FName InName, EObjectFlags Flags, UObject* Context, FFeedbackContext* Warn)
{
	return NewObject<UQuestGraph>(InParent, InClass, InName, Flags);
}
```
