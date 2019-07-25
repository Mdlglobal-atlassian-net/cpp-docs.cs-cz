---
title: value_compare – třída
ms.date: 11/04/2016
f1_keywords:
- value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: 0e057a6229c903402a51b34a8f4e844e80ace187
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452372"
---
# <a name="valuecompare-class"></a>value_compare – třída

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

Kritéria porovnání poskytnutá value_compare mezi `value_types` celými prvky obsaženými v hash_map jsou vynásobeny porovnáním mezi klíči příslušných prvků konstrukcí pomocné třídy. Operátor členské funkce používá objekt `comp` typu `key_compare` uložený v objektu Function, který poskytuje value_compare k porovnání komponent pro seřazení klíčů dvou prvků.

Pro hash_sets a hash_multisets, což jsou jednoduché kontejnery, kde jsou klíčové hodnoty identické s hodnotami elementu, value_compare je ekvivalentní k `key_compare`; pro hash_maps a hash_multimaps nejsou, protože hodnota typu `pair` elementy nejsou totožné s hodnotou klíče elementu.

## <a name="example"></a>Příklad

Příklad, jak deklarovat a používat value_compare, naleznete v příkladu pro [hash_map:: value_comp](../standard-library/hash-map-class.md#value_comp) .

## <a name="requirements"></a>Požadavky

**Header:** \<hash_map>

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také:

[binary_function – struktura](../standard-library/binary-function-struct.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
