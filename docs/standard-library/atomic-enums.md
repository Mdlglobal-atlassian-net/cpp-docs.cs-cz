---
title: '&lt;atomové&gt; výčty'
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: f41c5b238f74e85bc18e9ff5c3aa6a0050fe27e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376926"
---
# <a name="ltatomicgt-enums"></a>&lt;atomové&gt; výčty

## <a name="memory_order-enum"></a><a name="memory_order_enum"></a>memory_order výčet

Poskytuje symbolické názvy pro operace synchronizace v umístění v paměti. Tyto operace ovlivňují, jak se přiřazení v jednom vlákně stanou viditelnými v jiném vlákně.

```cpp
typedef enum memory_order {
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst,
} memory_order;
```

### <a name="enumeration-members"></a>Členové výčtu

|||
|-|-|
|`memory_order_relaxed`|Není nutné objednávat.|
|`memory_order_consume`|Operace zatížení funguje jako operace spotřebovávají na umístění paměti.|
|`memory_order_acquire`|Operace zatížení funguje jako operace získání v umístění paměti.|
|`memory_order_release`|Operace úložiště funguje jako operace uvolnění v umístění v paměti.|
|`memory_order_acq_rel`|Kombinuje `memory_order_acquire` a `memory_order_release`.|
|`memory_order_seq_cst`|Kombinuje `memory_order_acquire` a `memory_order_release`. Přístupy k paměti, `memory_order_seq_cst` které jsou označeny jako musí být postupně konzistentní.|

## <a name="see-also"></a>Viz také

[\<atomové>](../standard-library/atomic.md)
