---
title: '&lt;&gt; funkcí map'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: e7876b37bfc006eaecf2f1e36273c5ae8689dad4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883954"
---
# <a name="ltmapgt-functions"></a>&lt;&gt; funkcí map

## <a name="swap_multimap"></a>swap (map)

Zamění prvky dvou objektů map.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Mapa poskytující prvky, které mají být zaměněny, nebo mapa, jejíž prvky mají být vyměňovány pomocí těch z mapy *vlevo*.

*levý*\
Mapa, jejíž prvky mají být vyměňovány s *právy*mapy.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializovaný na mapě třídy kontejneru, aby bylo možné spustit členskou funkci `left`. [swap](../standard-library/map-class.md#swap)(`right`). Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejvíce specializované verze funkce šablony. Obecná verze funkce šablony, **template** \< **Class t**> **void swap**( **t &** , **t &** ), ve třídě algoritmu funguje podle přiřazení a jedná se o pomalou operaci. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s interní reprezentace třídy kontejneru.

### <a name="example"></a>Příklad

Viz příklad kódu pro mapu členské funkce [:: swap](../standard-library/map-class.md#swap) pro příklad, který používá verzi šablony `swap`.

## <a name="swap"></a>swap (multimap)

Vyměňuje prvky dvou více map.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Multimap poskytuje prvky, které mají být měněny, nebo multimap, jejichž prvky mají být vyměňovány s multimap *doleva*.

*levý*\
Multimap, jehož prvky mají být vyměňovány pomocí multimap *práva*.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializovaný na mapě třídy kontejneru, který se má spustit u třídy kontejneru multimap, aby se spustila členská funkce `left`. [swap](../standard-library/multimap-class.md#swap) (`right`). Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejvíce specializované verze funkce šablony. Obecná verze funkce šablony, **template** \< **Class t**> **void swap**( **t &** , **t &** ), ve třídě algoritmu funguje podle přiřazení a jedná se o pomalou operaci. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s interní reprezentace třídy kontejneru.

### <a name="example"></a>Příklad

Viz příklad kódu pro členskou funkci [multimap:: swap](../standard-library/multimap-class.md#swap) pro příklad, který používá verzi šablony `swap`.
