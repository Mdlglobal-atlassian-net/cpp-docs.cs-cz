---
title: '&lt;hash_map&gt;'
ms.date: 01/18/2018
f1_keywords:
- <hash_map>
- std::<hash_map>
helpviewer_keywords:
- hash_map header
ms.openlocfilehash: 6bb2ca0cc14bcc4a9b9df9877902de9181e0a768
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77258143"
---
# <a name="lthash_mapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> Tato hlavička je zastaralá. Alternativou je [\<unordered_map >](unordered-map.md).

Definuje šablony třídy kontejneru hash_map a hash_multimap a jejich podpůrné šablony.

## <a name="syntax"></a>Syntaxe

```cpp
#include <hash_map>
```

### <a name="operators"></a>Operátory

|Verze Hash_map|Verze Hash_multimap|Popis|
|-----------------------|----------------------------|-----------------|
|[operator! = (hash_map) – operátor](hash-map-operators.md#op_neq)|[operator! = (hash_multimap) – operátor](hash-map-operators.md#op_neq_mm)|Testuje, zda hash_map nebo hash_multimap objekt na levé straně operátoru není roven objektu hash_map nebo hash_multimap na pravé straně.|
|[operator = = (hash_map) – operátor](hash-map-operators.md#op_eq_eq)|[operator = = (hash_multimap) – operátor](hash-map-operators.md#op_eq_eq_mm)|Testuje, zda je objekt hash_map nebo hash_multimap na levé straně operátoru roven objektu hash_map nebo hash_multimap na pravé straně.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|Verze Hash_map|Verze Hash_multimap|Popis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Vyměňuje prvky dvou hash_maps nebo hash_multimaps.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[hash_compare – třída](hash-compare-class.md)|Popisuje objekt, který může být použit jakýmkoli z asociativních kontejnerů hash – hash_map, hash_multimap, hash_set nebo hash_multiset – jako výchozí objekt `Traits` parametru pro řazení a hash prvků, které obsahují.|
|[value_compare – třída](value-compare-class.md)|Poskytuje objekt funkce, který může porovnat prvky hash_map porovnáním hodnot jejich klíčů a určením jejich relativního pořadí v hash_map.|
|[hash_map – třída](hash-map-class.md)|Slouží k ukládání a rychlému načítání dat z kolekce, ve které je každý prvek dvojice, která má klíč řazení, jehož hodnota je jedinečná a přidružená hodnota dat.|
|[hash_multimap – třída](hash-multimap-class.md)|Používá se pro ukládání a rychlé načítání dat z kolekce, ve které je každý prvek dvojice, která má klíč řazení, jehož hodnota nemusí být jedinečná a přidružená hodnota dat.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<hash_map >

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také

\ [referenčních souborů hlaviček](cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](cpp-standard-library-reference.md)
