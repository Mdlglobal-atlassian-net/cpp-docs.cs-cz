---
title: '&lt;hash_map –&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
caps.latest.revision: 9
manager: ghogen
ms.openlocfilehash: d54cf0181a80ccb763cfe76f8eb89ade5a56b7d4
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="lthashmapgt-functions"></a>&lt;hash_map –&gt; funkce

|||
|-|-|
|[Swap](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap_hash_map"></a>  swap (hash_map)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Elementy dvě hash_maps výměny.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Hash_map –, jehož elementy jsou k výměně s těmi, která mapy `left`.

`left` Hash_map –, jehož elementy jsou k výměně s těmi, která mapy `right`.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializuje na hash_map – třída kontejneru pro spuštění funkce člen `left.` [swap](../standard-library/basic-ios-class.md#swap)*(vpravo*). Toto je instance částečné řazení šablon funkce kompilátorem. Když funkce šablon jsou přetížené tak, že na shodu šabloně se volání funkce není jedinečný, kompilátor vybere nejvíc specializovanou verzi funkce šablony. Obecné verzi funkce šablony **šablony \<třída T > void odkládacího souboru (T & T &)**, v algoritmu soubor hlaviček, funguje tak, že přiřazení a je pomalé operace. Specializovanou verzi v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s interního vyjádření třídy kontejneru.

## <a name="swap"></a>  Swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Elementy dvě hash_multimaps výměny.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Hash_multimap, jehož elementy jsou k výměně s těmi, která mapy `left`.

`left` Hash_multimap, jehož elementy jsou k výměně s těmi, která mapy `right`.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializuje na hash_multimap – třída kontejneru pro spuštění funkce člen `left.` [swap](../standard-library/hash-multimap-class.md#swap)*(vpravo*`)`. Toto je instance částečné řazení šablon funkce kompilátorem. Když funkce šablon jsou přetížené tak, že na shodu šabloně se volání funkce není jedinečný, kompilátor vybere nejvíc specializovanou verzi funkce šablony. Obecné verzi funkce šablony **šablony \<třída T > void odkládacího souboru (T & T &)**, v algoritmu soubor hlaviček, funguje tak, že přiřazení a je pomalé operace. Specializovanou verzi v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s interního vyjádření třídy kontejneru.

## <a name="see-also"></a>Viz také

[<hash_map>](../standard-library/hash-map.md)<br/>
