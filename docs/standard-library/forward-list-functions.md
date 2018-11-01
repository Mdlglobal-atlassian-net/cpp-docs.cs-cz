---
title: '&lt;forward_list –&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: b425461f1428470b04a525efdd9a702ae038a283
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477334"
---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list –&gt; funkce

||
|-|
|[Prohození](#swap)|

## <a name="swap"></a>  Prohození

Vymění prvky dvou seznamů vpřed.

```cpp
void swap(
    forward_list <Type, Allocator>& left,
    forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Objekt typu `forward_list`.|
|*doprava*|Objekt typu `forward_list`.|

### <a name="remarks"></a>Poznámky

Spustí tuto funkci `left.swap(right)`.

## <a name="see-also"></a>Viz také:

[<forward_list>](../standard-library/forward-list.md)<br/>
