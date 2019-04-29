---
title: unchecked_array_iterator – třída
ms.date: 11/04/2016
f1_keywords:
- stdext::unchecked_array_iterator
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
ms.openlocfilehash: 9b3db474bedca50922334bd4dbd09c71d4e6e987
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399340"
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator – třída

`unchecked_array_iterator` Třída umožňuje zabalit pole nebo ukazatel do nekontrolovaného iterátoru. Použijte tuto třídu jako obálku (pomocí [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator) funkce) pro nezpracované ukazatele nebo pole jako cílený způsob, jak spravovat Nezkontrolovaná upozornění ukazatele namísto globálního umlčení těchto upozornění. Pokud je to možné, upřednostněte kontrolovanou verzi této třídy, [checked_array_iterator](../standard-library/checked-array-iterator-class.md).

> [!NOTE]
> Tato třída je rozšířením společnosti Microsoft pro standardní knihovnu jazyka C++. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Iterator>
class unchecked_array_iterator;
```

## <a name="remarks"></a>Poznámky

Tato třída je definována v [stdext](../standard-library/stdext-namespace.md) oboru názvů.

Toto je nekontrolovaná verze [třídy checked_array_iterator](../standard-library/checked-array-iterator-class.md) a podporuje všechna stejná přetížení a členy. Další informace o funkci kontrolovaného iterátoru s příklady kódu naleznete v tématu [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterátor >

**Namespace:** stdext

## <a name="see-also"></a>Viz také:

[\<iterator>](../standard-library/iterator.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
