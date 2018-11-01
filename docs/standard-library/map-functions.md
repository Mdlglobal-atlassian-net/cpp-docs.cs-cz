---
title: '&lt;Mapa&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: 6c3480e9ffbbab46a42ae790d8b70afbcd823457
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517296"
---
# <a name="ltmapgt-functions"></a>&lt;Mapa&gt; funkce

|||
|-|-|
|[swap (map)](#swap)|[swap (multimap)](#swap_multimap)|

## <a name="swap_multimap"></a>  swap (map)

Zamění prvky dvou objektů map.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Mapa poskytující prvky pro záměnu nebo mapu, jehož prvky mají být zaměněny mapy *levé*.

*doleva*<br/>
Na mapě, jehož prvky mají být zaměněny mapy *správné*.

### <a name="remarks"></a>Poznámky

Funkce šablon je algoritmus specializované na mapě třídy kontejneru ke spuštění funkce člena `left`.[ Prohození](../standard-library/map-class.md#swap)( `right`). Toto je instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablony **šablony** \< **třída T**> **void prohození**( **T &**, **T &**), v algoritmu třída pracuje podle přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro členské funkce [map::swap](../standard-library/map-class.md#swap) příklad, který používá verzi šablony `swap`.

## <a name="swap"></a>  swap (multimap)

Vymění prvky dvou multimaps.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Multimap poskytující prvky pro záměnu nebo objektu multimap, jehož prvky mají být zaměněny objektu multimap *levé*.

*doleva*<br/>
Multimap, jehož prvky mají být zaměněny objektu multimap *správné*.

### <a name="remarks"></a>Poznámky

Funkce šablon je algoritmus specializované na mapě třídy kontejneru se promítnou u třída multimap kontejneru ke spuštění funkce člena `left`.[ Prohození](../standard-library/multimap-class.md#swap) (`right`). Toto je instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablony **šablony** \< **třída T**> **void prohození**( **T &**, **T &**), v algoritmu třída pracuje podle přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro členské funkce [multimap::swap](../standard-library/multimap-class.md#swap) příklad, který používá verzi šablony `swap`.

## <a name="see-also"></a>Viz také:

[\<map>](../standard-library/map.md)<br/>
