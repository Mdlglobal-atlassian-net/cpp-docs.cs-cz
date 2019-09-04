---
title: default_searcher – třída
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: f2b1fe83b5223bbb60e9e32149c101e6379f93c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "68268000"
---
# <a name="default_searcher-class"></a>default_searcher – třída

A `default_searcher` je typ objektu funkce pro operace, které hledají sekvenci určenou v konstruktoru objektu. Hledání je provedeno v jiné sekvenci poskytnuté operátoru volání funkce objektu. Vyvolá hledání [std:: Search](algorithm-functions.md#search) a provede hledání. `default_searcher`

## <a name="syntax"></a>Syntaxe

```cpp
template <class ForwardIterator, class BinaryPredicate = equal_to<>>
class default_searcher
{
    default_searcher(
        ForwardIterator pat_first,
        ForwardIterator pat_last,
        BinaryPredicate pred = BinaryPredicate());

    template <class ForwardIterator2>
    pair<ForwardIterator2, ForwardIterator2> operator()(
        ForwardIterator2 first,
        ForwardIterator2 last) const;
};
```

## <a name="members"></a>Členové

| | |
| - | - |
| **BeginRequestEventArgs** | |
| [default_searcher](#default-searcher-constructor) | |
| **Operátory** | |
| [operator()](#operator-call) | |

## <a name="default-searcher-constructor"></a>konstruktor default_searcher

Vytvoří objekt funkce pomocí sekvence hledání a predikátu rovnosti. `default_searcher`

```cpp
default_searcher(                   // C++17
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());

constexpr default_searcher(         // C++20
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Parametry

*pat_first*\
Počáteční prvek sekvence, která se má vyhledat

*pat_last*\
Konec sekvence, která se má vyhledat

*čekání*\
Volitelný predikát porovnání rovnosti pro elementy Sequence. Pokud není zadán typ porovnání rovnosti, je `std::equal_to`výchozí hodnota.

### <a name="remarks"></a>Poznámky

Vyvolá jakoukoli výjimku vyvolanou kopírovacím konstruktorem typů *BinaryPredicate* nebo *ForwardIterator* .

Tato třída je v C++ 17 novinkou. C++ 20 vytvořil konstruktor `constexpr`.

## <a name="operator-call"></a>operator () – operátor

Operátor volání operátoru funkce. Vyhledá v rámci sekvence `[first, last)` argumentů sekvenci určenou konstruktoru.

```cpp
template <class ForwardIterator2>   // C++17
pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;

template <class ForwardIterator2>   // C++20
constexpr pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;
```

### <a name="parameters"></a>Parametry

*první*\
Počáteční prvek sekvence, v níž se má hledat

*posledního*\
Konec sekvence, v níž se má hledat

### <a name="remarks"></a>Poznámky

Vrátí pár iterátorů. Počáteční *iterátor je* platným výsledkem:

`std::search( first, last, pat_first, pat_last, pred )`.

Druhý iterátor páru je *Poslední* *v případě, že se*jedná o *Poslední*. V opačném případě je to efektivní výsledek:

`std::next( i, std::distance( pat_first, pat_last ))`.

Tato třída je v C++ 17 novinkou. C++ 20 vytvořil operátor `constexpr`volání.

## <a name="see-also"></a>Viz také:

[\<funkční >](functional.md)\
[funkce algoritmu](algorithm-functions.md)\
[std:: Search](algorithm-functions.md#search)
