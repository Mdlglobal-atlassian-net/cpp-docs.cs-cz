---
title: '&lt;nové&gt; – definice TypeDef'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 80123bc35422984ef92bdba6da45052d3461b1d7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245161"
---
# <a name="ltnewgt-typedefs"></a>&lt;nové&gt; – definice TypeDef

## <a name="hardware_constructive_interference_size"></a> hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Poznámky

Toto číslo je maximální doporučená velikost souvislé paměti obsazena dva objekty přistupuje souběžných vláken s dočasné umístění. Musí být alespoň `alignof(max_align_t)`.

### <a name="example"></a>Příklad

```cpp
struct together { 
    atomic<int> dog;
    int puppy;
};

struct kennel {
    // Other data members...
    alignas(sizeof(together)) together pack;
    // Other data members...
};

static_assert(sizeof(together) <= hardware_constructive_interference_size);
```

## <a name="hardware_destructive_interference_size"></a> hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Poznámky

Toto číslo je minimální doporučené odsazení mezi dvěma objekty současně přistupuje, aby se zabránilo snížení výkonu další z důvodu kolize zavedených v implementaci. Musí být alespoň `alignof(max_align_t)`.

### <a name="example"></a>Příklad

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a> new_handler

Typu odkazuje na funkci vhodný pro použití jako novou obslužnou rutinu.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Poznámky

Tento typ obslužné rutiny funkce je volána **operátor new** nebo `operator new[]` když nemohou vyhovět požadavku další úložiště.

### <a name="example"></a>Příklad

Zobrazit [set_new_handler](../standard-library/new-functions.md#set_new_handler) příklad použití `new_handler` jako návratovou hodnotu.
