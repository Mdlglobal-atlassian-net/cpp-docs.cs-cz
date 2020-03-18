---
title: value_compare – třída
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: d64d51869ca8db1ed42e9d33691f59da4473d8d0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447564"
---
# <a name="value_compare-class"></a>value_compare – třída

Poskytuje objekt funkce, který může porovnat prvky hash_map porovnáním hodnot jejich klíčů a určením jejich relativního pořadí v hash_map.

## <a name="syntax"></a>Syntaxe

```cpp
class value_compare
    : std::public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(
        const value_type& left,
        const value_type& right) const
    {
        return (comp(left.first, right.first));
    }

protected:
    value_compare(const key_compare& c) : comp (c) { }
    key_compare comp;
};
```

## <a name="remarks"></a>Poznámky

Kritéria porovnání poskytnutá value_compare mezi `value_types` celých prvků obsažených v hash_map jsou vynásobena porovnáním mezi klíči příslušných prvků konstrukcí pomocné třídy. Operátor členské funkce používá objekt `comp` typu `key_compare` uložený v objektu Function, který poskytuje value_compare pro porovnání komponent pro seřazení klíčů dvou prvků.

Pro hash_sets a hash_multisets, což jsou jednoduché kontejnery, kde jsou klíčové hodnoty stejné jako hodnoty prvků, value_compare je ekvivalentem `key_compare`; pro hash_maps a hash_multimaps nejsou, protože hodnota typu `pair` prvky není shodná s hodnotou klíče elementu.

## <a name="example"></a>Příklad

Příklad, jak deklarovat a používat value_compare, naleznete v příkladu pro [hash_map:: value_comp](../standard-library/hash-map-class.md#value_comp) .

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<hash_map >

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také

[Binary_function struktura](../standard-library/binary-function-struct.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
