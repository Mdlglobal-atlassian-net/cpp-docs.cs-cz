---
title: '&lt;Atomic&gt; výčty | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: c30e7ca78533b0b4c2a4eb49bd99bd13483d2b8d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="ltatomicgt-enums"></a>&lt;Atomic&gt; výčty

## <a name="memory_order_enum"></a>  memory_order – výčet

Poskytuje symbolické názvy pro operace synchronizace v umístění v paměti. Tyto operace ovlivňují, jak budou zobrazeny v jiném přiřazení v jedno vlákno.

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
|`memory_order_relaxed`|Žádné řazení vyžaduje.|
|`memory_order_consume`|Operace načtení funguje jako spotřebě operace na umístění v paměti.|
|`memory_order_acquire`|Operace načtení funguje jako operace získání umístění v paměti.|
|`memory_order_release`|Operace úložiště funguje jako operace uvolnění umístění v paměti.|
|`memory_order_acq_rel`|Kombinuje `memory_order_acquire` a `memory_order_release`.|
|`memory_order_seq_cst`|Kombinuje `memory_order_acquire` a `memory_order_release`. Paměť přístupů, které jsou označeny jako `memory_order_seq_cst` musí být postupně konzistentní.|

## <a name="see-also"></a>Viz také

[\<Atomic >](../standard-library/atomic.md)<br/>
