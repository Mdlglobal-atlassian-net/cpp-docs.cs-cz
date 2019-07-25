---
title: hash – strukturaC++ (standardní knihovna) | Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- thread/std::hash
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
ms.openlocfilehash: e6d0cea7bfc8cd745e7276f7fc29d493f178fc9b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451952"
---
# <a name="hash-structure-c-standard-library"></a>hash – strukturaC++ (standardní knihovna)

Definuje členskou funkci, která vrací hodnotu, která je jednoznačně určena pomocí `Val`. Členská funkce definuje funkci [hash](../standard-library/hash-class.md) , která je vhodná pro mapování hodnot typu `thread::id` na distribuci hodnot indexu.

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

**Hlavička:** \<> vlákna

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<> vlákna](../standard-library/thread.md)\
[unary_function – struktura](../standard-library/unary-function-struct.md)
