---
title: seznam &lt;&gt; funkcí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420062"
---
# <a name="ltlistgt-functions"></a>funkce seznamu &lt;&gt;

## <a name="swap"></a>adresu

Vyměňuje prvky dvou seznamů.

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `list`.

*pravé*\
Objekt typu `list`.

### <a name="remarks"></a>Poznámky

Tato funkce šablony provádí `left.swap(right)`.
