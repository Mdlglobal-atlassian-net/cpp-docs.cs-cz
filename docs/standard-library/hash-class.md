---
title: hash – třída
ms.date: 11/04/2016
f1_keywords:
- functional/std::hash
- bitset/std::hash
- memory/std::hash
- string/std::hash
- system_error/std::hash
- thread/std::hash
- typeindex/std::hash
- vector/std::hash
- XSTDDEF/std::hash
- xstring/std::hash
helpviewer_keywords:
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
ms.assetid: e1b500c6-a5c8-4f6f-ad33-7ec52eb8e2e4
ms.openlocfilehash: 61446ab6b79496024d44a99fcf5f500bb871bb80
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448822"
---
# <a name="hash-class"></a>hash – třída

Vypočítá kód hodnoty hash pro hodnotu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct hash {
    size_t operator()(Ty val) const;
};
```

## <a name="remarks"></a>Poznámky

Objekt funkce definuje funkci hash, která je vhodná pro mapování hodnot typu *ty* na distribuci hodnot indexu. Člen `operator()` vrátí hodnotu hash pro *Val*, vhodná pro použití s `unordered_map`třídami šablon, `unordered_multimap`, `unordered_set`a `unordered_multiset`. Standardní knihovna poskytuje specializace pro základní typy: *Ty* mohou být jakýkoli skalární typ, včetně typů ukazatelů a výčtových typů. Kromě toho existují specializace pro typy `string`knihoven, `u16string_view` `wstring_view` `string_view` `wstring`, `u16string` `u32string`,,,,, `u32string_view`, `bitset`,, `error_code` `error_condition`, ,`optional` ,,`type_index`, ,`unique_ptr`a. `shared_ptr` `thread` `variant` `vector<bool>`

## <a name="example"></a>Příklad

```cpp
// std__functional__hash.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <unordered_set>

int main()
    {
    std::unordered_set<int, std::hash<int> > c0;
    c0.insert(3);
    std::cout << *c0.find(3) << std::endl;

    return (0);
    }
```

```Output
3
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<funkční >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<unordered_map>](../standard-library/unordered-map.md)\
[unordered_multimap – třída](../standard-library/unordered-multimap-class.md)\
[unordered_multiset – třída](../standard-library/unordered-multiset-class.md)\
[<unordered_set>](../standard-library/unordered-set.md)
