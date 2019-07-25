---
title: '&lt;hash_set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <hash_set>
- std::<hash_set>
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
ms.openlocfilehash: 559bbff00b8e5204dd4f381abaf9987b4752db48
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452023"
---
# <a name="lthashsetgt"></a>&lt;hash_set&gt;

> [!NOTE]
> Tato hlavička je zastaralá. Alternativou je [< unordered_set >](../standard-library/unordered-set.md).

Definuje třídy šablon kontejnerů hash_set a hash_multiset a jejich podpůrné šablony.

## <a name="syntax"></a>Syntaxe

```cpp
#include <hash_set>
```

## <a name="remarks"></a>Poznámky

### <a name="operators"></a>Operátory

|Verze hash_set|Verze hash_multiset|Popis|
|-----------------------|----------------------------|-----------------|
|[operator! = (hash_set) – operátor](../standard-library/hash-set-operators.md#op_neq)|[operator! = (hash_multiset) – operátor](../standard-library/hash-set-operators.md#op_neq)|Testuje, zda objekt hash_set nebo hash_multiset na levé straně operátoru není roven objektu hash_set nebo hash_multiset na pravé straně.|
|[operator = = (hash_set) – operátor](../standard-library/hash-set-operators.md#op_eq_eq)|[operator = = (hash_multiset) – operátor](../standard-library/hash-set-operators.md#op_eq_eq)|Testuje, zda je objekt hash_set nebo hash_multiset na levé straně operátoru roven objektu hash_set nebo hash_multiset na pravé straně.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|Verze hash_set|Verze hash_multiset|Popis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|Vyměňuje prvky dvou hash_sets nebo hash_multisets.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[hash_compare – třída](../standard-library/hash-compare-class.md)|Popisuje objekt, který může být použit jakýmkoli z asociativních kontejnerů hash – hash_map, hash_multimap, hash_set nebo hash_multiset – jako výchozí `Traits` objekt parametru pro řazení a hash prvků, které obsahují.|
|[hash_set – třída](../standard-library/hash-set-class.md)|Slouží k ukládání a rychlému načítání dat z kolekce, ve které jsou hodnoty prvků, které jsou obsaženy, jedinečné a slouží jako klíčové hodnoty.|
|[hash_multiset – třída](../standard-library/hash-multiset-class.md)|Slouží k ukládání a rychlému načítání dat z kolekce, ve které jsou hodnoty prvků, které jsou obsaženy, jedinečné a slouží jako klíčové hodnoty.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
