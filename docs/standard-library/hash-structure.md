---
title: hash – struktura
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::hash
ms.assetid: e5a41202-ef3b-45d0-b3a7-4c2dbdc0487a
ms.openlocfilehash: ba05d70692b2f85c1a14f319fb1e92dcadc0ccce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158778"
---
# <a name="hash-structure"></a>hash – struktura

Třída šablony definuje svou metodu jako vracející `val.hash_code()`. Metoda definuje hashovací funkci, která se používá k mapování hodnot typu [type_index –](../standard-library/type-index-class.md) k distribuci hodnot indexu.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct hash<type_index>
: public unary_function<type_index, size_t>
{ // hashes a typeinfo object
    size_t operator()(type_index val) const;

};
```

## <a name="see-also"></a>Viz také:

[\<typeindex>](../standard-library/typeindex.md)<br/>
