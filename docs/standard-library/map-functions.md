---
title: '&lt;Mapa&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: 3c6cb7d0308e4bafc531fe0baf0c5d666228c3ec
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966365"
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

*správné* mapy poskytující prvky pro záměnu nebo mapu, jehož prvky mají být zaměněny mapy *levé*.

*levé* mapy, jehož prvky mají být zaměněny mapy *správné*.

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

*správné* multimap poskytující prvky pro záměnu nebo objektu multimap, jehož prvky mají být zaměněny objektu multimap *levé*.

*levé* multimap, jehož prvky mají být zaměněny objektu multimap *správné*.

### <a name="remarks"></a>Poznámky

Funkce šablon je algoritmus specializované na mapě třídy kontejneru se promítnou u třída multimap kontejneru ke spuštění funkce člena `left`.[ Prohození](../standard-library/multimap-class.md#swap) (`right`). Toto je instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablony **šablony** \< **třída T**> **void prohození**( **T &**, **T &**), v algoritmu třída pracuje podle přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro členské funkce [multimap::swap](../standard-library/multimap-class.md#swap) příklad, který používá verzi šablony `swap`.

## <a name="see-also"></a>Viz také:

[\<map>](../standard-library/map.md)<br/>
