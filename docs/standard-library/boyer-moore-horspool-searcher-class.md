---
title: boyer_moore_horspool_searcher – třída
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_horspool_searcher
helpviewer_keywords:
- std::boyer_moore_horspool_searcher [C++]
ms.openlocfilehash: c7d24fee4a47fc588b00e527594682f1c4aadf76
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957164"
---
# <a name="boyer_moore_horspool_searcher-class"></a>boyer_moore_horspool_searcher – třída

`boyer_moore_horspool_searcher` Třída je typ objektu funkce, který používá algoritmus Boyer-Moore-Horspool pro hledání sekvence zadané v konstruktoru objektu. Hledání je provedeno v jiné sekvenci poskytnuté operátoru volání funkce objektu. Tato třída je předána jako parametr jednomu z přetížení [std:: Search](algorithm-functions.md#search).

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
| **BeginRequestEventArgs** | |
| [boyer_moore_horspool_searcher](#boyer-moore-horspool-searcher-constructor) | |
| **Operátory** | |
| [operator()](#operator-call) | |

## <a name="boyer-moore-horspool-searcher-constructor"></a>konstruktor boyer_moore_horspool_searcher

Vytvoří objekt funkce pomocí sekvence pro hledání, objektu funkce hash a predikátu rovnosti. `boyer_moore_horspool_searcher`

```cpp
boyer_moore_horspool_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Parametry

*pat_first*\
Počáteční prvek sekvence, která se má vyhledat

*pat_last*\
Konec sekvence, která se má vyhledat

*HF*\
Objekt, který se používá k hashování elementů sekvence.

*čekání*\
Volitelný predikát porovnání rovnosti pro elementy Sequence. Pokud není zadán typ porovnání rovnosti, je `std::equal_to`výchozí hodnota.

### <a name="remarks"></a>Poznámky

Vyvolá jakoukoli výjimku vyvolanou kopírovacím konstruktorem typů *BinaryPredicate*, *hash*nebo *RandomAccessIterator* nebo operátor volání třídy *BinaryPredicate* nebo *hash*.

Tato třída je v C++ 17 novinkou.

## <a name="operator-call"></a>operator () – operátor

Operátor volání objektu Function. Vyhledá v rámci sekvence `[first, last)` argumentů sekvenci určenou konstruktoru.

```cpp
template <class ForwardIterator2>   // C++17
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>Parametry

*první*\
Počáteční prvek sekvence, v níž se má hledat

*posledního*\
Konec sekvence, v níž se má hledat

### <a name="remarks"></a>Poznámky

Pokud je vzor `[pat_first, pat_last)` hledání prázdný, vrátí `make_pair(first, first)`. Pokud se vyhledávací vzor nenajde, vrátí `make_pair(last, last)`. V opačném případě vrátí dvojici iterátorů na začátek a konec sekvence `[first, last)` , která se `[pat_first, pat_last)` rovná podle predikátu *před*.

Tato třída je v C++ 17 novinkou.

## <a name="see-also"></a>Viz také:

[\<funkční >](functional.md)\
[funkce algoritmu](algorithm-functions.md)\
[boyer_moore_searcher – třída](boyer-moore-searcher-class.md)\
[std:: Search](algorithm-functions.md#search)
