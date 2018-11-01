---
title: '&lt;hash_set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <hash_set>
- std::<hash_set>
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
ms.openlocfilehash: a9ed3cf90c4650683eac1c198a8b57614e96d759
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449458"
---
# <a name="lthashsetgt"></a>&lt;hash_set&gt;

> [!NOTE]
> Tato hlavička je zastaralý. Alternativou je [< unordered_set >](../standard-library/unordered-set.md).

Definuje kontejner šablony třídy hash_set a hash_multiset – a jejich podpůrných šablon.

## <a name="syntax"></a>Syntaxe

```cpp
#include <hash_set>

```

## <a name="remarks"></a>Poznámky

### <a name="operators"></a>Operátory

|Hash_set – verze|Hash_multiset – verze|Popis|
|-----------------------|----------------------------|-----------------|
|[Operator! = (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[Operator! = (hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|Testuje, zda je objekt hash_set nebo hash_multiset na levé straně operátoru není roven objektu hash_set nebo hash_multiset na pravé straně.|
|[Operator == (hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[Operator == (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|Testuje, zda hash_set nebo hash_multiset objekt na levé straně operátoru roven objektu hash_set nebo hash_multiset na pravé straně.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|Hash_set – verze|Hash_multiset – verze|Popis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|Vymění prvky dvou hash_sets nebo hash_multisets.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[hash_compare – třída](../standard-library/hash-compare-class.md)|Popisuje objekt, který můžete použít některou z hodnot hash asociativní kontejnery – hash_map – hash_multimap, hash_set, nebo hash_multiset – jako výchozí `Traits` parametr objektu pořadí a hodnoty hash, který obsahují elementy.|
|[hash_set – třída](../standard-library/hash-set-class.md)|Používá pro ukládání a rychlé načítání dat z kolekce, ve kterém hodnoty elementů obsažených jsou jedinečné a slouží jako klíčové hodnoty.|
|[hash_multiset – třída](../standard-library/hash-multiset-class.md)|Používá pro ukládání a rychlé načítání dat z kolekce, ve kterém hodnoty elementů obsažených jsou jedinečné a slouží jako klíčové hodnoty.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
