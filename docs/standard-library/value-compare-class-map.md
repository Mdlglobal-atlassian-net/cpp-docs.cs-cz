---
title: value_compare – třída (&lt;mapa&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
ms.openlocfilehash: 1f872edce6f0114be7c90a8108ba248fd793a989
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447580"
---
# <a name="value_compare-class-ltmapgt"></a>value_compare – třída (&lt;mapa&gt;)

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

Kritérium porovnání poskytované `value_compare` mezi `value_types` celých prvků obsažených v mapě je vyvolaných porovnáním mezi klíči příslušných prvků konstrukcí pomocné třídy. Operátor členské funkce používá objekt `comp` typu `key_compare` uložený v objektu Function, který poskytuje `value_compare` pro porovnání komponent pro seřazení klíčů dvou prvků.

Pro sady a množiny, které jsou jednoduché kontejnery, kde jsou klíčové hodnoty stejné jako hodnoty prvků, `value_compare` je ekvivalentem `key_compare`; u map a s více mapami nejsou, protože hodnota typu `pair` prvky není shodná s hodnotou klíče elementu.

## <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `value_compare`, naleznete v tématu příklad pro [value_comp](../standard-library/map-class.md#value_comp) .

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<mapování >

**Obor názvů:** std

## <a name="see-also"></a>Viz také

[Binary_function struktura](../standard-library/binary-function-struct.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
