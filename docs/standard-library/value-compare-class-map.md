---
title: value_compare – třída&lt;(&gt;map)
ms.date: 11/04/2016
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
- value_compare
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
ms.openlocfilehash: d098e947aec1ea543f29c168a632d1f4c9412e82
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448329"
---
# <a name="valuecompare-class-ltmapgt"></a>value_compare – třída&lt;(&gt;map)

Poskytuje objekt funkce, který může porovnat prvky mapy porovnáním hodnot jejich klíčů a určením jejich relativního pořadí v mapě.

## <a name="syntax"></a>Syntaxe

```cpp
class value_compare : public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(const value_type& left, const value_type& right) const;
    value_compare(key_compare pred) : comp(pred);
protected:
    key_compare comp;
};
```

## <a name="remarks"></a>Poznámky

Kritérium porovnání, které `value_compare` je zadáno mezi `value_types` celými prvky obsaženými v mapě, je vyvolaným porovnáním mezi klíči příslušných prvků konstrukcí pomocné třídy. Operátor členské funkce používá objekt `comp` typu `key_compare` uložený v objektu Function, `value_compare` který poskytuje k porovnání komponent pro seřazení klíčů dvou prvků.

Pro sady a množiny, které jsou jednoduché kontejnery, kde jsou klíčové hodnoty identické s hodnotami prvků, `value_compare` je `key_compare`ekvivalentní hodnotě; pro mapy a pro více map nejsou, protože hodnota elementů Type `pair` není shodná s hodnotou hodnota klíče elementu

## <a name="example"></a>Příklad

Příklad, jak [](../standard-library/map-class.md#value_comp) deklarovat a používat `value_compare`, naleznete v části příklad pro value_comp.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<mapování >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[binary_function – struktura](../standard-library/binary-function-struct.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
