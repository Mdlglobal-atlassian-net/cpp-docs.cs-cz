---
title: hash – třída
ms.date: 11/04/2016
f1_keywords:
- functional/std::hash
- bitset/std::hash
- memory/std::hash
- string/std::hash
- system_error/std::hash
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
ms.openlocfilehash: aa51e56197ba79afbe2bd2597596c52b23a4f65b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446576"
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

Objekt funkce definuje funkci hash, která je vhodná pro mapování hodnot typu *ty* na distribuci hodnot indexu. Členský `operator()` vrátí hodnotu hash pro *Val*, která je vhodná pro použití se šablonami tříd `unordered_map`, `unordered_multimap`, `unordered_set`a `unordered_multiset`. Standardní knihovna poskytuje specializace pro základní typy: *ty* můžou být jakýkoli skalární typ, včetně typů ukazatelů a výčtových typů. Kromě toho existují specializace pro typy knihoven `string`, `wstring`, `u16string`, `u32string`, `string_view`, `wstring_view`, `u16string_view`, `u32string_view`, `bitset`, `error_code`, `error_condition`, `optional`, `shared_ptr`, `thread`, `type_index`, `unique_ptr`, `variant`a `vector<bool>`.

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

**Záhlaví:** \<funkční >

**Obor názvů:** std

## <a name="see-also"></a>Viz také

[< unordered_map >](../standard-library/unordered-map.md)\
[unordered_multimap\ třídy](../standard-library/unordered-multimap-class.md)
[unordered_multiset\ třídy](../standard-library/unordered-multiset-class.md)
[<unordered_set>](../standard-library/unordered-set.md)
