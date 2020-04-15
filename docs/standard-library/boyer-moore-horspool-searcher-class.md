---
title: boyer_moore_horspool_searcher třída
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_horspool_searcher
helpviewer_keywords:
- std::boyer_moore_horspool_searcher [C++]
ms.openlocfilehash: 4d404b414ad632e02be5f4e9fad0e22cefb86ce2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366779"
---
# <a name="boyer_moore_horspool_searcher-class"></a>boyer_moore_horspool_searcher třída

Třída `boyer_moore_horspool_searcher` je typ objektu funkce, který používá algoritmus Boyer-Moore-Horspool k hledání sekvence zadané v konstruktoru objektu. Hledání se provádí v rámci jiné sekvence poskytované operátoru volání funkce objektu. Tato třída je předána jako parametr jednomu z přetížení [std::search](algorithm-functions.md#search).

## <a name="syntax"></a>Syntaxe

```cpp
template <
    class RandomAccessIterator,
    class Hash = hash<typename iterator_traits<RandomAccessIterator>::value_type>,
    class BinaryPredicate = equal_to<>>
class boyer_moore_horspool_searcher
{
    boyer_moore_horspool_searcher(
        RandomAccessIterator pat_first,
        RandomAccessIterator pat_last,
        Hash hf = Hash(),
        BinaryPredicate pred = BinaryPredicate());

    template <class RandomAccessIterator2>
    pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
        RandomAccessIterator2 first,
        RandomAccessIterator2 last) const;
};
```

## <a name="members"></a>Členové

| | |
| - | - |
| **Konstruktor** | |
| [boyer_moore_horspool_searcher](#boyer-moore-horspool-searcher-constructor) | |
| **Operátory** | |
| [operátor()](#operator-call) | |

## <a name="boyer_moore_horspool_searcher-constructor"></a><a name="boyer-moore-horspool-searcher-constructor"></a>konstruktor boyer_moore_horspool_searcher

Vytvoří objekt `boyer_moore_horspool_searcher` funkce pomocí sekvence k hledání, objekt funkce hash a predikát rovnosti.

```cpp
boyer_moore_horspool_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Parametry

*pat_first*\
Počáteční prvek sekvence hledat.

*pat_last*\
Konec sekvence hledat.

*Hf*\
Volatelný objekt, který slouží k hash sekvenční prvky.

*pred*\
Volitelné porovnání rovnosti predikát pro sekvenční prvky. Pokud není zadán typ porovnání rovnosti, `std::equal_to`výchozí je .

### <a name="remarks"></a>Poznámky

Vyvolá jakoukoli výjimku vyvolanou konstruktorem kopie *typů BinaryPredicate*, *Hash*nebo *RandomAccessIterator* nebo operátoru volání *BinaryPredicate* nebo *Hash*.

Tato třída je nová v jazyce C++17.

## <a name="operator"></a><a name="operator-call"></a>operátor()

Operátor volání objektu funkce. Hledá v posloupnosti `[first, last)` argumentů posloupnost zadanou konstruktoru.

```cpp
template <class ForwardIterator2>   // C++17
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>Parametry

*První*\
Počáteční prvek sekvence hledat v rámci.

*Poslední*\
Konec sekvence k prohledání uvnitř.

### <a name="remarks"></a>Poznámky

Pokud je `[pat_first, pat_last)` vzorek hledání `make_pair(first, first)`prázdný, vrátí . Pokud vyhledávací vzor není nalezen, `make_pair(last, last)`vrátí . V opačném případě vrátí dvojici iterátorů na začátek `[first, last)` a konec `[pat_first, pat_last)` sekvence, která se rovná podle predikátu *pred*.

Tato třída je nová v jazyce C++17.

## <a name="see-also"></a>Viz také

[\<funkční>](functional.md)\
[funkce algoritmu](algorithm-functions.md)\
[boyer_moore_searcher třída](boyer-moore-searcher-class.md)\
[std::hledat](algorithm-functions.md#search)
