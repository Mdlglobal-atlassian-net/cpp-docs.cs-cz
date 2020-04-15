---
title: Výčty oboru názvů Concurrency (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: 2467db27ad36dfcda31dfb5bb45067ada5470d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376323"
---
# <a name="concurrency-namespace-enums-amp"></a>Výčty oboru názvů Concurrency (AMP)

|||
|-|-|
|[access_type výčet](#access_type)|[queuing_mode výčet](#queuing_mode)|

## <a name="access_type-enumeration"></a><a name="access_type"></a>access_type výčet

Typ výčtu používaný k označení různých typů přístupu k datům.

```cpp
enum access_type;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`access_type_auto`|Automaticky zvolte `access_type` to nejlepší pro akcelerátor.|
|`access_type_none`|Vyhrazené. Přidělení je přístupné pouze na akcelerátoru a nikoli na procesoru.|
|`access_type_read`|Sdílené. Přidělení je přístupné na akcelerátoru a je čitelné na procesoru.|
|`access_type_read_write`|Sdílené. Přidělení je přístupné na akcelerátoru a je zapisovatelné na procesoru.|
|`access_type_write`|Sdílené. Přidělení je přístupné na akcelerátoru a je čitelné i zapisovatelné na procesoru.|

## <a name="queuing_mode-enumeration"></a><a name="queuing_mode"></a>queuing_mode výčet

Určuje režimy řazení do fronty, které jsou podporovány v akcelerátoru.

```cpp
enum queuing_mode;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`queuing_mode_immediate`|Režim řazení do fronty, který určuje, že všechny příkazy, například [parallel_for_each funkce (C++ AMP),](concurrency-namespace-functions-amp.md#parallel_for_each)jsou odesílány do odpovídajícíakcelerátoru zařízení, jakmile se vrátí k volajícímu.|
|`queuing_mode_automatic`|Režim řazení do fronty, který určuje, že příkazy budou zařazeny do fronty příkazů, která odpovídá [accelerator_view](accelerator-view-class.md) objektu. Příkazy jsou odesílány do zařízení, když je volána [accelerator_view::flush.](accelerator-view-class.md#flush)|

## <a name="see-also"></a>Viz také

[Obor názvů souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
