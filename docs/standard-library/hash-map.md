---
title: '&lt;hash_map –&gt; | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 01/18/2018
ms.technology:
- cpp-standard-libraries
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
ms.workload:
- cplusplus
ms.openlocfilehash: caae1a52c36c5d21e55e90a821b280f2face7ede
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959771"
---
# <a name="lthashmapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> Tato hlavička je zastaralý. Alternativou je [ \<unordered_map >](unordered-map.md).

Definuje kontejner šablony třídy hash_map a hash_multimap – a jejich podpůrných šablon.

## <a name="syntax"></a>Syntaxe

> #<a name="include-hashmap"></a>Zahrnout < hash_map >

### <a name="operators"></a>Operátory

|Hash_map – verze|Hash_multimap – verze|Popis|
|-----------------------|----------------------------|-----------------|
|[Operator! = (hash_map)](hash-map-operators.md#op_neq)|[Operator!=(hash_multimap)](hash-map-operators.md#op_neq_mm)|Testuje, zda je objekt hash_map nebo hash_multimap na levé straně operátoru není roven objektu hash_map nebo hash_multimap na pravé straně.|
|[Operator == (hash_map)](hash-map-operators.md#op_eq_eq)|[Operator == (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|Testuje, zda hash_map nebo hash_multimap objekt na levé straně operátoru roven objektu hash_map nebo hash_multimap na pravé straně.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|Hash_map – verze|Hash_multimap – verze|Popis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Vymění prvky dvou hash_maps nebo hash_multimaps.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[hash_compare – třída](hash-compare-class.md)|Popisuje objekt, který můžete použít některou z hodnot hash asociativní kontejnery – hash_map – hash_multimap, hash_set, nebo hash_multiset – jako výchozí `Traits` parametr objektu pořadí a hodnoty hash, který obsahují elementy.|
|[value_compare – třída](value-compare-class.md)|Poskytuje objekt funkce, který může porovnat elementy hash_map porovnáním hodnot jejich klíče pro určení jejich relativního pořadí v hash_map –.|
|[hash_map – třída](hash-map-class.md)|Používá pro ukládání a rychlé načítání dat z kolekce, ve kterém je každý prvek pár, který má klíč řazení, jehož hodnota je jedinečný a přidružená data hodnotu.|
|[hash_multimap – třída](hash-multimap-class.md)|Používá pro ukládání a rychlé načítání dat z kolekce, ve kterém je každý prvek pár, který má klíč řazení, jehož hodnota nemusí být jedinečný a přidružená data hodnotu.|

## <a name="requirements"></a>Požadavky

**Header:** \<hash_map>

**Namespace:** stdext

## <a name="see-also"></a>Viz také:

[Hlavičkové soubory odkaz](cpp-standard-library-header-files.md)
[bezpečnost vlákna ve standardní knihovně C++](thread-safety-in-the-cpp-standard-library.md)
[C++ standardní knihovna – referenční dokumentace](cpp-standard-library-reference.md)
