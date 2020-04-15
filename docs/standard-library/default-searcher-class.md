---
title: default_searcher třída
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 2c8b93b83b271f787c993f789e1a68f84a60f016
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368928"
---
# <a name="default_searcher-class"></a>default_searcher třída

A `default_searcher` je typ objektu funkce pro operace, které hledají posloupnost zadanou v konstruktoru objektu. Hledání se provádí v rámci jiné sekvence poskytované operátoru volání funkce objektu. Vyvolá `default_searcher` [std::search](algorithm-functions.md#search) provést hledání.

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
| **Konstruktor** | |
| [default_searcher](#default-searcher-constructor) | |
| **Operátory** | |
| [operátor()](#operator-call) | |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a>konstruktor default_searcher

Vytvoří objekt `default_searcher` funkce pomocí sekvence hledat a rovnosti predikátu.

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
Počáteční prvek sekvence hledat.

*pat_last*\
Konec sekvence hledat.

*pred*\
Volitelné porovnání rovnosti predikát pro sekvenční prvky. Pokud není zadán typ porovnání rovnosti, `std::equal_to`výchozí je .

### <a name="remarks"></a>Poznámky

Vyvolá všechny výjimky vyvolána konstruktorkopie *BinaryPredicate* nebo *ForwardIterator* typy.

Tato třída je nová v jazyce C++17. C ++ 20 udělal `constexpr`konstruktor .

## <a name="operator"></a><a name="operator-call"></a>operátor()

Operátor volání operátoru funkce. Hledá v posloupnosti `[first, last)` argumentů posloupnost zadanou konstruktoru.

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

*První*\
Počáteční prvek sekvence hledat v rámci.

*Poslední*\
Konec sekvence k prohledání uvnitř.

### <a name="remarks"></a>Poznámky

Vrátí pár iterátorů. Počáteční iterátor *i* je účinným výsledkem:

`std::search( first, last, pat_first, pat_last, pred )`.

Druhý iterátor dvojice je *poslední,* pokud *i** je *poslední*. V opačném případě je to efektivní výsledek:

`std::next( i, std::distance( pat_first, pat_last ))`.

Tato třída je nová v jazyce C++17. C++20 provedl operátor `constexpr`volání .

## <a name="see-also"></a>Viz také

[\<funkční>](functional.md)\
[funkce algoritmu](algorithm-functions.md)\
[std::hledat](algorithm-functions.md#search)
