---
title: '&lt;hash_map –&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: 12ceb799ccf0944b8f0e8d48975da25c39f22505
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100947"
---
# <a name="lthashmapgt-functions"></a>&lt;hash_map –&gt; funkce

|||
|-|-|
|[Prohození](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap_hash_map"></a>  swap (hash_map)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vymění prvky dvou hash_maps.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Hash_map –, jehož prvky mají být zaměněny mapy *levé*.

*doleva*<br/>
Hash_map –, jehož prvky mají být zaměněny mapy *správné*.

### <a name="remarks"></a>Poznámky

Funkce šablon je algoritmus specializované na hash_map – třídy kontejnerů ke spuštění funkce člena `left.` [prohození](../standard-library/basic-ios-class.md#swap)*(pravém*). Toto je instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablony **šablony \<třída T > void odkládacího souboru (T &, T &)**, v algoritmu souboru hlaviček, funguje tak, že přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

## <a name="swap"></a>  Prohození

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vymění prvky dvou hash_multimaps.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Hash_multimap –, jehož prvky mají být zaměněny mapy *levé*.

*doleva*<br/>
Hash_multimap –, jehož prvky mají být zaměněny mapy *správné*.

### <a name="remarks"></a>Poznámky

Funkce šablon je algoritmus specializované na hash_multimap – třídy kontejnerů ke spuštění funkce člena `left.` [prohození](../standard-library/hash-multimap-class.md#swap)*(pravém*`)`. Toto je instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablony **šablony \<třída T > void odkládacího souboru (T &, T &)**, v algoritmu souboru hlaviček, funguje tak, že přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

## <a name="see-also"></a>Viz také:

[<hash_map>](../standard-library/hash-map.md)<br/>
