---
title: '&lt;hash_map &gt;'
ms.date: 01/18/2018
f1_keywords:
- <hash_map>
- std::<hash_map>
helpviewer_keywords:
- hash_map header
ms.openlocfilehash: e586a933c2a80b7e611bcd4b4714e300eb21a0ad
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689576"
---
# <a name="lthash_mapgt"></a>&lt;hash_map &gt;

> [!NOTE]
> Tato hlavička je zastaralá. Alternativa je [\<unordered_map >](unordered-map.md).

Definuje šablony tříd kontejneru hash_map a hash_multimap a jejich podpůrné šablony.

## <a name="syntax"></a>Syntaxe

```
#include <hash_map>
```

### <a name="operators"></a>Operátory

|Verze hash_map|Verze hash_multimap|Popis|
|-----------------------|----------------------------|-----------------|
|[operator! = (hash_map) – operátor](hash-map-operators.md#op_neq)|[operator! = (hash_multimap) – operátor](hash-map-operators.md#op_neq_mm)|Testuje, zda objekt hash_map nebo hash_multimap na levé straně operátoru není roven objektu hash_map nebo hash_multimap na pravé straně.|
|[operator = = (hash_map) – operátor](hash-map-operators.md#op_eq_eq)|[operator = = (hash_multimap) – operátor](hash-map-operators.md#op_eq_eq_mm)|Testuje, zda je objekt hash_map nebo hash_multimap na levé straně operátoru roven objektu hash_map nebo hash_multimap na pravé straně.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|Verze hash_map|Verze hash_multimap|Popis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Vyměňuje prvky dvou hash_maps nebo hash_multimaps.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[hash_compare – třída](hash-compare-class.md)|Popisuje objekt, který může být použit jakýmkoli z asociativních kontejnerů hash – hash_map, hash_multimap, hash_set nebo hash_multiset – jako výchozí objekt parametru `Traits` pro řazení a hash prvků, které obsahují.|
|[value_compare – třída](value-compare-class.md)|Poskytuje objekt funkce, který může porovnat prvky hash_map porovnáním hodnot jejich klíčů a určením jejich relativního pořadí v hash_map.|
|[hash_map – třída](hash-map-class.md)|Slouží k ukládání a rychlému načítání dat z kolekce, ve které je každý prvek dvojice, která má klíč řazení, jehož hodnota je jedinečná a přidružená hodnota dat.|
|[hash_multimap – třída](hash-multimap-class.md)|Používá se pro ukládání a rychlé načítání dat z kolekce, ve které je každý prvek dvojice, která má klíč řazení, jehož hodnota nemusí být jedinečná a přidružená hodnota dat.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<hash_map >

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](thread-safety-in-the-cpp-standard-library.md) \
[Standardní knihovna C++ – referenční dokumentace](cpp-standard-library-reference.md)
