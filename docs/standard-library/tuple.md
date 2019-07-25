---
title: '&lt;řazené kolekce členů&gt;'
ms.date: 11/04/2016
f1_keywords:
- <tuple>
helpviewer_keywords:
- tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
ms.openlocfilehash: a391a77ea65a203a7eddde12046c5df89a77194a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447150"
---
# <a name="lttuplegt"></a>&lt;řazené kolekce členů&gt;

Definuje šablonu `tuple` , jejíž instance uchovávají objekty různých typů.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> řazené kolekce členů

**Obor názvů:** std

## <a name="members"></a>Členové

### <a name="classes-and-structs"></a>Třídy a struktury

|||
|-|-|
|[tuple – třída](../standard-library/tuple-class.md)|Zabalí posloupnost prvků s pevnou délkou.|
|[tuple_element – třída](../standard-library/tuple-element-class-tuple.md)|Zabalí typ `tuple` elementu.|
|[tuple_size – třída](../standard-library/tuple-size-class-tuple.md)|Zalomí počet `tuple` prvků.|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||

### <a name="objects"></a>Objekty

|||
|-|-|
|[tuple_element_t](../standard-library/tuple-functions.md#tuple_element_t)||
|[tuple_size_v](../standard-library/tuple-functions.md#tuple_size_v)||

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator==](../standard-library/tuple-operators.md#op_eq_eq)|`tuple` Porovnání objektů, stejné.|
|[operator!=](../standard-library/tuple-operators.md#op_neq)|`tuple` Porovnání objektů, není rovno.|
|[operátor <](../standard-library/tuple-operators.md#op_lt)|`tuple` Porovnání objektů, je menší než.|
|[operátor < =](../standard-library/tuple-operators.md#op_lt_eq)|`tuple` Porovnání objektů, je menší nebo rovno.|
|[operátor >](../standard-library/tuple-operators.md#op_gt)|Porovnání objektů `tuple` , které jsou větší než.|
|[operator>=](../standard-library/tuple-operators.md#op_gt_eq)|Porovnání objektů `tuple` , které jsou větší nebo rovno.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[vyrovnat](../standard-library/tuple-functions.md#apply)|Volá funkci s řazenou kolekcí členů.|
|[forward_as_tuple](../standard-library/tuple-functions.md#forward)|Vytvoří řazenou kolekci odkazů.|
|[get](../standard-library/tuple-functions.md#get)|Získá prvek z `tuple` objektu.|
|[make_from_tuple](../standard-library/tuple-functions.md#make_from_tuple)|Vytvořit zkratku pro `tuple`.|
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|`tuple` Vytvoří z hodnot elementu.|
|[swap](../standard-library/tuple-functions.md#swap)||
|[propojují](../standard-library/tuple-functions.md#tie)|Vytvoří odkaz `tuple` z elementu.|
|[tuple_cat](../standard-library/tuple-functions.md#tuple_cat)|Vytvoří objekt řazené kolekce členů s rozsahem prvků typu.|

## <a name="see-also"></a>Viz také:

[\<> pole](../standard-library/array.md)
