---
title: '&lt;Variant&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 7a812ccc3c8cb2a660c01ad2b17ea75b5d5c9542
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267886"
---
# <a name="ltvariantgt"></a>&lt;Variant&gt;

Objekt variant uchovává a spravuje hodnotu. Pokud varianty obsahuje hodnotu, typ hodnoty musí být jeden z typů argumentů šablony zadaný typ variant. Tyto argumenty šablony jsou volány alternativy.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<typ variant >

**Namespace:** std

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator==](../standard-library/forward-list-operators.md#op_eq_eq)|Testuje, zda variant objekt na levé straně operátoru rovná varianty objekt na pravé straně.|
|[operator!=](../standard-library/forward-list-operators.md#op_neq)|Testuje, zda objektu variant na levé straně operátoru není roven objektu variant na pravé straně.|
|[Operator <](../standard-library/forward-list-operators.md#op_lt)|Testuje, zda je variant objekt na levé straně operátoru menší než objektu variant na pravé straně.|
|[Operator < =](../standard-library/forward-list-operators.md#op_lt_eq)|Testuje, zda je varianty objekt na levé straně operátoru je menší než nebo rovná varianty objektu na pravé straně.|
|[Operator >](../standard-library/forward-list-operators.md#op_gt)|Testuje, zda je variant objekt na levé straně operátoru větší než objektu variant na pravé straně.|
|[operator>=](../standard-library/forward-list-operators.md#op_lt_eq)|Testuje, zda objektu variant na levé straně operátoru větší než nebo rovná varianty objektu na pravé straně.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[get](../standard-library/variant-functions.md#get)|Získá typ variant objektu.|
|[get_if](../standard-library/variant-functions.md#get_if)|Získá typ variant objektu, pokud existuje.|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|Vrátí **true** pokud existuje hodnotu typu variant.|
|[swap](../standard-library/variant-functions.md#swap)|Zamění **variant**.|
|[Navštivte web](../standard-library/variant-functions.md#visit)|Přesune k dalšímu **variant**.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|Objekty vyvolána sestavy neplatná přístupy k hodnotě objektu variant.|
|[Variant](../standard-library/variant.md)|Objekt buď uchování hodnoty jednoho z jeho alternativní typů nebo žádnou hodnotu.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[Hodnota hash](../standard-library/hash-structure.md)||
|[monostate](../standard-library/monostate-structure.md)|Alternativní typ, který pro hodnotu typu variant chcete nastavit jako výchozí typ variant constructible.|
|[uses_allocator –](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|Pomáhá zajistit variant objekty.|
|[variant_size](../standard-library/variant-size-structure.md)|Pomáhá zajistit variant objekty.|

### <a name="objects"></a>Objekty

|||
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)
