---
title: Výčty oboru názvů Concurrency (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: a4feb2f98fc288fa79c0f9d81e4ed882027eddf8
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419299"
---
# <a name="concurrency-namespace-enums-amp"></a>Výčty oboru názvů Concurrency (AMP)

|||
|-|-|
|[Výčet access_type](#access_type)|[Výčet queuing_mode](#queuing_mode)|

## <a name="access_type"></a>Výčet access_type

Typ výčtu, který slouží k označení různých typů přístupu k datům.

```cpp
enum access_type;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`access_type_auto`|Automaticky zvolit nejlepší `access_type` akcelerátoru.|
|`access_type_none`|Personál. Přidělení je dostupné jenom v akcelerátoru a ne na procesoru.|
|`access_type_read`|Sdíleného. Přidělení je dostupné v akcelerátoru a je čitelné na CPU.|
|`access_type_read_write`|Sdíleného. Přidělení je přístupné v akcelerátoru a je zapisovatelné na CPU.|
|`access_type_write`|Sdíleného. Přidělení je přístupné v akcelerátoru a je čitelné i zapisovatelné v procesoru.|

## <a name="queuing_mode"></a>Výčet queuing_mode

Určuje režimy služby Řízení front, které jsou podporovány v akcelerátoru.

```cpp
enum queuing_mode;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`queuing_mode_immediate`|Režim řazení do fronty, který určuje, že všechny příkazy, například [Parallel_for_each funkceC++ (amp)](concurrency-namespace-functions-amp.md#parallel_for_each), jsou odesílány do odpovídajícího zařízení akcelerátoru, jakmile se vrátí volajícímu.|
|`queuing_mode_automatic`|Režim služby Řízení front, který určuje, že se příkazy zařadí do fronty příkazů, které odpovídají objektu [accelerator_view](accelerator-view-class.md) . Příkazy se odesílají do zařízení, když se zavolá [accelerator_view:: flush](accelerator-view-class.md#flush) .|

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
