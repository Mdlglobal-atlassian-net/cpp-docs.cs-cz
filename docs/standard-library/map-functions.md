---
title: '&lt;Mapa&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: e7876b37bfc006eaecf2f1e36273c5ae8689dad4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243293"
---
# <a name="ltmapgt-functions"></a>&lt;Mapa&gt; funkce

## <a name="swap_multimap"></a> swap (map)

Zamění prvky dvou objektů map.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

*doprava*\
Mapa poskytující prvky pro záměnu nebo mapu, jehož prvky mají být zaměněny mapy *levé*.

*doleva*\
Na mapě, jehož prvky mají být zaměněny mapy *správné*.

### <a name="remarks"></a>Poznámky

Funkce šablon je algoritmus specializované na mapě třídy kontejneru ke spuštění funkce člena `left`.[ Prohození](../standard-library/map-class.md#swap)( `right`). Toto je instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablony **šablony** \< **třída T**> **void prohození**( **T &** , **T &** ), v algoritmu třída pracuje podle přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro členské funkce [map::swap](../standard-library/map-class.md#swap) příklad, který používá verzi šablony `swap`.

## <a name="swap"></a> swap (multimap)

Vymění prvky dvou multimaps.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

*doprava*\
Multimap poskytující prvky pro záměnu nebo objektu multimap, jehož prvky mají být zaměněny objektu multimap *levé*.

*doleva*\
Multimap, jehož prvky mají být zaměněny objektu multimap *správné*.

### <a name="remarks"></a>Poznámky

Funkce šablon je algoritmus specializované na mapě třídy kontejneru se promítnou u třída multimap kontejneru ke spuštění funkce člena `left`.[ Prohození](../standard-library/multimap-class.md#swap) (`right`). Toto je instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablony **šablony** \< **třída T**> **void prohození**( **T &** , **T &** ), v algoritmu třída pracuje podle přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro členské funkce [multimap::swap](../standard-library/multimap-class.md#swap) příklad, který používá verzi šablony `swap`.
