---
title: '&lt;seznam&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268060"
---
# <a name="ltlistgt-functions"></a>&lt;seznam&gt; funkce

## <a name="swap"></a> Prohození

Vymění prvky dvou seznamů.

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `list`.

*doprava*\
Objekt typu `list`.

### <a name="remarks"></a>Poznámky

Spustí tuto funkci `left.swap(right)`.
