---
title: '&lt;Nástroj&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <utility>
dev_langs:
- C++
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84464f485d39f1146f55fb6b5b1970cf1c9321df
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858130"
---
# <a name="ltutilitygt"></a>&lt;Nástroj&gt;

Definuje typy standardní knihovna C++, funkce a operátory, které pomáhají vytvářet a spravovat páry objekty, které jsou užitečné, kdykoli potřebovat dva objekty zpracovány, jako by šlo o jednu.

## <a name="syntax"></a>Syntaxe

```cpp
#include <utility>

```

## <a name="remarks"></a>Poznámky

Páry se často používá standardní knihovny C++. Jako argumenty a návratové hodnoty pro různé funkce i jako typy elementů pro kontejnery, jako jsou požadována [map – třída](../standard-library/map-class.md) a [multimap – třída](../standard-library/multimap-class.md). \<Nástroj > hlavička automaticky zahrnuta v \<mapy > při správě jejich klíč/hodnota pár zadejte elementy.

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|Třídu, která zabalí typ `pair` elementu.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Třídu, která zabalí `pair` počet elementu.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[Předat dál](../standard-library/utility-functions.md#forward)|Zachovává typu odkazu (buď `lvalue` nebo `rvalue`) argumentu z se po ideální předávání skryt.|
|[get](../standard-library/utility-functions.md#get)|Funkci, která se získá element z `pair` objektu.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Podpůrná funkce šablony použitý k vytvoření objekty typu `pair`, kde jsou typy součást založené na datové typy předány jako parametry.|
|[Přesunutí](../standard-library/utility-functions.md#move)|Vrátí předaný argument jako `rvalue` odkaz.|
|[Swap](../standard-library/utility-functions.md#swap)|Výměny dva elementy `pair` objekty.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|Testy, pokud objekt dvojice na levé straně operátoru není stejný jako dvojice objekt na pravé straně.|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|Testy, pokud objekt dvojice na levé straně operátoru rovná objekt dvojice na pravé straně.|
|[operátor <](../standard-library/utility-operators.md#op_lt)|Testy, pokud je dvojice objekt na levé straně operátoru je menší než pár objekt na pravé straně.|
|[Operátor\<=](../standard-library/utility-operators.md#op_gt_eq)|Testy, pokud je dvojice objekt na levé straně operátoru je menší než nebo rovno objekt dvojice na pravé straně.|
|[operátor >](../standard-library/utility-operators.md#op_gt)|Testy, pokud objekt dvojice na levé straně operátoru je větší než pár objekt na pravé straně.|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|Testy, pokud objekt dvojice na levé straně operátoru je větší než nebo rovno objekt dvojice na pravé straně.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[Identity](../standard-library/identity-structure.md)||
|[dvojice](../standard-library/pair-structure.md)|Typ, který poskytuje schopnost dva objekty považovat za jeden objekt.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
