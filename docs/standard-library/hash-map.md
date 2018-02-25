---
title: "&lt;hash_map –&gt; | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <hash_map>
- std::<hash_map>
dev_langs:
- C++
helpviewer_keywords:
- hash_map header
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c50716912b42aace87b1132672331c86d9eae162
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="lthashmapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> Tuto hlavičku je zastaralé. Alternativou je [ \<unordered_map >](unordered-map.md).

Definuje hash_map – kontejner šablony třídy a hash_multimap a jejich podpůrné šablony.

## <a name="syntax"></a>Syntaxe

> #<a name="include-hashmap"></a>include <hash_map>

### <a name="operators"></a>Operátory

|Hash_map – verze|Hash_multimap – verze|Popis|
|-----------------------|----------------------------|-----------------|
|[Operator! = (hash_map)](hash-map-operators.md#op_neq)|[operator!=(hash_multimap)](hash-map-operators.md#op_neq_mm)|Testy, pokud hash_map nebo hash_multimap objekt na levé straně operátor není rovno hash_map nebo hash_multimap objekt na pravé straně.|
|[operator== (hash_map)](hash-map-operators.md#op_eq_eq)|[operator== (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|Testy, pokud hash_map nebo hash_multimap objekt na levé straně operátoru rovná hash_map nebo hash_multimap objekt na pravé straně.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|Hash_map – verze|Hash_multimap – verze|Popis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Elementy dva hash_maps nebo hash_multimaps výměny.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[hash_compare – třída](hash-compare-class.md)|Popisuje objekt, který můžete použít žádné kontejnery asociativní hash – hash_map, hash_multimap, hash_set, nebo hash_multiset – ve výchozím nastavení **vlastnosti** parametr objekt pořadí a hodnoty hash elementy obsahují.|
|[value_compare – třída](value-compare-class.md)|Poskytuje objekt funkce, který můžete porovnat elementy hash_map srovnáním jejich klíčů určit jejich relativní pořadí v hash_map.|
|[hash_map – třída](hash-map-class.md)|Používá pro ukládání a rychlé načítání dat z kolekce, ve kterém je každý prvek pár, který má klíč řazení, jehož hodnota je jedinečný a hodnotu přidružená data.|
|[hash_multimap – třída](hash-multimap-class.md)|Používá pro ukládání a rychlé načítání dat z kolekce, ve kterém je každý prvek pár, který má klíč řazení, jehož hodnota nemusí být jedinečný a hodnotu přidružená data.|

## <a name="requirements"></a>Požadavky

**Header:** \<hash_map>

**Namespace:** stdext –

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](cpp-standard-library-header-files.md)  
[Bezpečný přístup z více vláken ve standardní knihovně C++](thread-safety-in-the-cpp-standard-library.md)  
[Standardní knihovna C++ – referenční dokumentace](cpp-standard-library-reference.md)  
