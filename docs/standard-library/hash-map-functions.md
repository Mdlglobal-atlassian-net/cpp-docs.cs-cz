---
title: '&lt;funkce&gt; hash_map'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: efaa960d91c69d2157896adb4612c5dd36f00cff
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448735"
---
# <a name="lthashmapgt-functions"></a>&lt;funkce&gt; hash_map

|||
|-|-|
|[swap](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap_hash_map"></a>swap (hash_map)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_map třída](../standard-library/unordered-map-class.md).

Vyměňuje prvky dvou hash_maps.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Hash_map, jehož prvky mají být vyměňovány pomocí rozvržení *vlevo*.

*zbývá*\
Hash_map, jehož prvky mají být vyměňovány s právy mapy .

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializovaný na třídu kontejneru hash_map ke spuštění `left.`překlopení členské funkce [](../standard-library/basic-ios-class.md#swap) *(Right*). Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejvíce specializované verze funkce šablony. Obecná verze funkce šablony, **Třída \<šablony T > void swap (t &, t &)** , v souboru hlaviček algoritmu funguje podle přiřazení a je pomalé operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s interní reprezentace třídy kontejneru.

## <a name="swap"></a>adresu

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vyměňuje prvky dvou hash_multimaps.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Hash_multimap, jehož prvky mají být vyměňovány pomocí rozvržení *vlevo*.

*zbývá*\
Hash_multimap, jehož prvky mají být vyměňovány s právy mapy .

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializovaný na třídu kontejneru `left.`hash_multimap ke spuštění překlopení členské funkce [](../standard-library/hash-multimap-class.md#swap) *(Right*`)`. Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejvíce specializované verze funkce šablony. Obecná verze funkce šablony, **Třída \<šablony T > void swap (t &, t &)** , v souboru hlaviček algoritmu funguje podle přiřazení a je pomalé operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s interní reprezentace třídy kontejneru.

## <a name="see-also"></a>Viz také:

[<hash_map>](../standard-library/hash-map.md)
