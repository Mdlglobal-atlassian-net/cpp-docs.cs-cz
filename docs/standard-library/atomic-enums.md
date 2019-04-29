---
title: '&lt;Atomic&gt; výčty'
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: 03247f6abd01b00fbbed3b33016cd4a12d8a13f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377284"
---
# <a name="ltatomicgt-enums"></a>&lt;Atomic&gt; výčty

## <a name="memory_order_enum"></a>  memory_order – výčet

Poskytuje symbolické názvy pro operace synchronizace v paměťových místech. Tyto operace ovlivní, jak budou přiřazení v jednom vlákně viditelná v jiném.

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

### <a name="enumeration-members"></a>Členy výčtu

|||
|-|-|
|`memory_order_relaxed`|Není požadováno žádné řazení.|
|`memory_order_consume`|Operace načítání funguje jako operace spotřeby na umístění v paměti.|
|`memory_order_acquire`|Operace načítání funguje jako operace získání na umístění v paměti.|
|`memory_order_release`|Operace ukládání funguje jako operace uvolnění na umístění v paměti.|
|`memory_order_acq_rel`|Kombinuje `memory_order_acquire` a `memory_order_release`.|
|`memory_order_seq_cst`|Kombinuje `memory_order_acquire` a `memory_order_release`. Přístupy do paměti, které jsou označeny jako `memory_order_seq_cst` musí být sekvenčně konzistentní.|

## <a name="see-also"></a>Viz také:

[\<Atomic >](../standard-library/atomic.md)<br/>
