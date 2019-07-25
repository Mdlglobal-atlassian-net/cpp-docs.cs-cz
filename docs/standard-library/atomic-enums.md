---
title: '&lt;atomické&gt; výčty'
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: 14b816177593a9f6dade60e36676a37f724fc209
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457595"
---
# <a name="ltatomicgt-enums"></a>&lt;atomické&gt; výčty

## <a name="memory_order_enum"></a>Výčet memory_order

Poskytuje symbolické názvy pro operace synchronizace v umístěních paměti. Tyto operace mají vliv na to, jak se přiřazení v jednom vlákně budou zobrazovat v jiném.

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
|`memory_order_relaxed`|Není vyžadováno žádné řazení.|
|`memory_order_consume`|Operace načítání funguje jako operace spotřeby v umístění v paměti.|
|`memory_order_acquire`|Operace načítání funguje jako operace získání v umístění v paměti.|
|`memory_order_release`|Operace úložiště funguje jako operace vydání v umístění v paměti.|
|`memory_order_acq_rel`|Kombinuje `memory_order_acquire` a `memory_order_release`.|
|`memory_order_seq_cst`|Kombinuje `memory_order_acquire` a `memory_order_release`. Přístup k paměti, která jsou označena jako `memory_order_seq_cst` , musí být postupně konzistentní.|

## <a name="see-also"></a>Viz také:

[\<atomická >](../standard-library/atomic.md)
