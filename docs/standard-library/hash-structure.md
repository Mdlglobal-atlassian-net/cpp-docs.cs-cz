---
title: hash – struktura
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::hash
ms.assetid: e5a41202-ef3b-45d0-b3a7-4c2dbdc0487a
ms.openlocfilehash: ef620867a5c31c7bd2030803edd6eaea6bbb5726
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243713"
---
# <a name="hash-structure"></a>hash – struktura

Třída šablony definuje svou metodu jako vracející `val.hash_code()`. Metoda definuje hashovací funkci, která se používá k mapování hodnot typu [type_index –](../standard-library/type-index-class.md) k distribuci hodnot indexu.

## <a name="syntax"></a>Syntaxe

```cpp
template <> struct hash<type_index>
: public unary_function<type_index, size_t>
{ // hashes a typeinfo object
    size_t operator()(type_index val) const;
};
```

## <a name="specialized-types"></a>Speciální typy

### <a name="system_error"></a> \<system_error – >

```cpp
template <class T> struct hash;
template <> struct hash<error_code>;
template <> struct hash<error_condition>;
```

## <a name="see-also"></a>Viz také:

[\<typeindex>](../standard-library/typeindex.md)<br/>
