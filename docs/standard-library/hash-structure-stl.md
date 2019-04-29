---
title: hash – struktura (standardní knihovna C++) | Dokumentace Microsoftu
ms.date: 11/04/2016
f1_keywords:
- thread/std::hash
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
ms.openlocfilehash: bb230d401d5061f4951f8007f93c3a28ce3dab03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405011"
---
# <a name="hash-structure-c-standard-library"></a>hash – struktura (standardní knihovna C++)

Definuje členskou funkci, která vrací hodnotu, která jednoznačně určuje `Val`. Definuje členskou funkci [hash](../standard-library/hash-class.md) funkce, která je vhodná pro mapování hodnot typu `thread::id` k distribuci hodnot indexu.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct hash<thread::id> :
    public unary_function<thread::id, size_t>
{
    size_t operator()(thread::id Val) const;

};
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vlákna >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<vlákna >](../standard-library/thread.md)<br/>
[unary_function – struktura](../standard-library/unary-function-struct.md)<br/>
