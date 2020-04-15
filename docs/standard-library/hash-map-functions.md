---
title: '&lt;hash_map&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: 7cb2e46f19bd30e3eb313cde867c6a055cb8bca5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370613"
---
# <a name="lthash_mapgt-functions"></a>&lt;hash_map&gt; funkce

|||
|-|-|
|[Swap](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap-hash_map"></a><a name="swap_hash_map"></a>swap (hash_map)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vyměňuje prvky dvou hash_maps.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Hash_map jejichž prvky mají být vyměněny s prvky na mapě *vlevo*.

*Vlevo*\
hash_map jejichž prvky mají být vyměněny s prvky mapy *vpravo*.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializovaný na třídu kontejneru `left.`hash_map ke spuštění [odkládací](../standard-library/basic-ios-class.md#swap)funkce*člena (vpravo).* Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejspecializovanější verzi funkce šablony. Obecná verze funkce šablony, ** \<třída šablony T> void swap (T&, T&)**, v souboru hlavičky algoritmu funguje podle přiřazení a je to pomalá operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s vnitřní reprezentací třídy kontejneru.

## <a name="swap"></a><a name="swap"></a>Swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vyměňuje prvky dvou hash_multimaps.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
hash_multimap jejichž prvky mají být vyměněny s prvky na mapě *vlevo*.

*Vlevo*\
hash_multimap jejichž prvky mají být vyměněny s prvky mapy *vpravo*.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializovaný na třídu kontejneru `left.`hash_multimap pro spuštění [odkládací](../standard-library/hash-multimap-class.md#swap)funkce člena *(vpravo*`)`. Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejspecializovanější verzi funkce šablony. Obecná verze funkce šablony, ** \<třída šablony T> void swap (T&, T&)**, v souboru hlavičky algoritmu funguje podle přiřazení a je to pomalá operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s vnitřní reprezentací třídy kontejneru.

## <a name="see-also"></a>Viz také

[<hash_map>](../standard-library/hash-map.md)
