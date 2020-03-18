---
title: '&lt;nové&gt; definice typedef'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 80123bc35422984ef92bdba6da45052d3461b1d7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419796"
---
# <a name="ltnewgt-typedefs"></a>&lt;nové&gt; definice typedef

## <a name="hardware_constructive_interference_size"></a>hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Poznámky

Toto číslo je maximální doporučená velikost souvislé paměti obsazené dvěma objekty, ke kterým se přistupovalo pomocí souběžných vláken. Musí být aspoň `alignof(max_align_t)`.

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

## <a name="hardware_destructive_interference_size"></a>hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Poznámky

Toto číslo představuje minimální doporučený posun mezi dvěma souběžně přidanými objekty, aby nedocházelo k dalšímu snížení výkonu kvůli sporům, které zavedla implementace. Musí být aspoň `alignof(max_align_t)`.

### <a name="example"></a>Příklad

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a>new_handler

Typ odkazuje na funkci vhodnou pro použití jako nová obslužná rutina.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Poznámky

Tento typ obslužné rutiny je volán **operátorem New** nebo `operator new[]`, když nemůže splnit požadavek na další úložiště.

### <a name="example"></a>Příklad

V tématu [set_new_handler](../standard-library/new-functions.md#set_new_handler) příklad použití `new_handler` jako návratové hodnoty.
