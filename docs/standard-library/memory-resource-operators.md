---
title: '&lt;memory_resource&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- memory_resource/std::operator!=
- memory_resource/std::operator==
helpviewer_keywords:
- std::operator!= (memory_resource)
- std::operator== (memory_resource)
ms.openlocfilehash: dd7dc3e65fe58663285433f9cbc9b64cf2b81cda
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268024"
---
# <a name="ltmemoryresourcegt-operators"></a>&lt;memory_resource&gt; operátory

## <a name="op_neq"></a> Operator! =

Testuje, zda je objekt memory_resource na levé straně operátoru není roven objektu memory_resource na pravé straně.

```cpp
template <class T1, class T2>
    bool operator!=(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```

## <a name="op_eq_eq"></a> Operator ==

Testuje, zda objekt memory_resource na levé straně operátoru roven objektu memory_resource na pravé straně.

```cpp
template <class T1, class T2>
    bool operator==(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```
