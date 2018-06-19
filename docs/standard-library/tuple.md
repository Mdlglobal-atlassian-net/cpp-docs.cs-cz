---
title: '&lt;řazené kolekce členů&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <tuple>
dev_langs:
- C++
helpviewer_keywords:
- tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ba25328b86a51e34cba60bd55b63ce2eab696d6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864581"
---
# <a name="lttuplegt"></a>&lt;řazené kolekce členů&gt;

Definuje šablonu `tuple` jejichž instance uložení objektů různých typů.

## <a name="syntax"></a>Syntaxe

```cpp
#include <tuple>
```

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[řazené kolekce členů](../standard-library/tuple-class.md)|Zabalí pevnou délkou pořadí elementů.|
|[tuple_element – třída](../standard-library/tuple-element-class-tuple.md)|Zabalí typ `tuple` elementu.|
|[tuple_size – třída](../standard-library/tuple-size-class-tuple.md)|Zabalí `tuple` počet elementu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator==](../standard-library/tuple-operators.md#op_eq_eq)|Porovnání `tuple` objekty stejné|
|[operator!=](../standard-library/tuple-operators.md#op_neq)|Porovnání `tuple` objekty, není rovno|
|[operátor <](../standard-library/tuple-operators.md#op_lt)|Porovnání `tuple` objekty, menší než|
|[Operator < =](../standard-library/tuple-operators.md#op_lt_eq)|Porovnání `tuple` objekty, menší nebo rovno|
|[operátor >](../standard-library/tuple-operators.md#op_gt)|Porovnání `tuple` objekty, které jsou větší než|
|[operator>=](../standard-library/tuple-operators.md#op_gt_eq)|Porovnání `tuple` objekty, větší než nebo rovno|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[get](../standard-library/tuple-functions.md#get)|Získá element z `tuple` objektu.|
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|Díky `tuple` z hodnot elementu.|
|[Tie –](../standard-library/tuple-functions.md#tie)|Díky `tuple` z elementu odkazy.|

## <a name="see-also"></a>Viz také

[\<pole >](../standard-library/array.md)<br/>
