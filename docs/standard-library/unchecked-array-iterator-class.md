---
title: unchecked_array_iterator – třída
ms.date: 11/04/2016
f1_keywords:
- stdext::unchecked_array_iterator
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
ms.openlocfilehash: 5344a108f32b694b9dafac78dbb8eb7064cdf4cc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455010"
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator – třída

`unchecked_array_iterator` Třída umožňuje zabalit pole nebo ukazatel do nekontrolovaného iterátoru. Tuto třídu můžete použít jako obálku (pomocí funkce [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator) ) pro nezpracované ukazatele nebo pole jako cílový způsob, jak spravovat nezaškrtnutá upozornění na ukazatele namísto globálně tlumiče těchto upozornění. Pokud je to možné, preferovat kontrolované verze této třídy, [checked_array_iterator](../standard-library/checked-array-iterator-class.md).

> [!NOTE]
> Tato třída je rozšířením společnosti Microsoft pro C++ standardní knihovnu. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Iterator>
class unchecked_array_iterator;
```

## <a name="remarks"></a>Poznámky

Tato třída je definována v oboru názvů [stdext](../standard-library/stdext-namespace.md) .

Toto je nekontrolovaná verze [třídy checked_array_iterator](../standard-library/checked-array-iterator-class.md) a podporuje všechna stejná přetížení a členy. Další informace o funkci kontrolovaného iterátoru s příklady kódu najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

## <a name="requirements"></a>Požadavky

**Hlavička:** \<iterátor >

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také:

[\<iterátor >](../standard-library/iterator.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
