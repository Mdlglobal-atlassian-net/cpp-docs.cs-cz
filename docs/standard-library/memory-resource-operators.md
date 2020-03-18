---
title: operátory &lt;memory_resource&gt;
ms.date: 11/04/2016
f1_keywords:
- memory_resource/std::operator!=
- memory_resource/std::operator==
helpviewer_keywords:
- std::operator!= (memory_resource)
- std::operator== (memory_resource)
ms.openlocfilehash: dd7dc3e65fe58663285433f9cbc9b64cf2b81cda
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419908"
---
# <a name="ltmemory_resourcegt-operators"></a>operátory &lt;memory_resource&gt;

## <a name="op_neq"></a>! = – operátor

Testuje, zda memory_resource objekt na levé straně operátoru není roven objektu memory_resource na pravé straně.

```cpp
template <class T1, class T2>
    bool operator!=(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt memory_resource na levé straně operátoru roven objektu memory_resource na pravé straně.

```cpp
template <class T1, class T2>
    bool operator==(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```
