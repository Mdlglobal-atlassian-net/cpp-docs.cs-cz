---
title: '&lt;Mapa&gt;'
ms.date: 11/04/2016
f1_keywords:
- <map>
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
ms.openlocfilehash: 96ca19b2562c3f145555c3c1b1d8db4fc700ed91
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243310"
---
# <a name="ltmapgt"></a>&lt;Mapa&gt;

Definuje kontejner šablony třídy map a objektu multimap a jejich podpůrných šablon.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<mapy >

**Namespace:** std

> [!NOTE]
> \<Mapy > Knihovna také používá `#include <initializer_list>` příkazu.

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|Verze mapy|Multimap – verze|Popis|
|-----------------|----------------------|-----------------|
|[Operator! = (map)](../standard-library/map-operators.md#op_neq)|[Operator! = (multimap)](../standard-library/map-operators.md#op_neq)|Testuje, zda je objekt map nebo multimap na levé straně operátoru není roven mapy nebo multimap objekt na pravé straně.|
|[Operator < (map)](../standard-library/map-operators.md#op_eq_eq)|[Operator < (multimap)](../standard-library/map-operators.md#op_eq_eq)|Testuje, zda je objekt map nebo multimap na levé straně operátoru menší než mapy nebo multimap objekt na pravé straně.|
|[Operator < = (map)](../standard-library/map-operators.md#op_lt)|[operátor\<= (multimap)](../standard-library/map-operators.md#op_lt)|Testuje, zda je objekt map nebo multimap na levé straně operátoru menší než nebo rovna hodnotě mapy nebo objektem multimap na pravé straně.|
|[Operator == (map)](../standard-library/map-operators.md#op_eq_eq)|[operator== (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|Testuje, zda mapování nebo multimap objekt na levé straně operátoru roven objektu map nebo multimap na pravé straně.|
|[Operator > (map)](../standard-library/map-operators.md#op_gt)|[Operator > (multimap)](../standard-library/map-operators.md#op_gt_multimap)|Testuje, zda je objekt map nebo multimap na levé straně operátoru větší než mapy nebo multimap objekt na pravé straně.|
|[Operator > = (map)](../standard-library/map-operators.md#op_gt_eq)|[operator>= (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|Testuje, zda je objekt map nebo multimap na levé straně operátoru větší než nebo rovna hodnotě mapy nebo multimap objekt na pravé straně.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|Verze mapy|Multimap – verze|Popis|
|-----------------|----------------------|-----------------|
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|Vymění prvky dvou mapy nebo multimaps.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[value_compare – třída](../standard-library/value-compare-class-map.md)|Poskytuje objekt funkce, který může porovnat prvky objektu map porovnáním hodnot jejich klíče pro určení jejich relativního pořadí v objektu map.|
|[map – třída](../standard-library/map-class.md)|Používá pro ukládání a načítání dat z kolekce, ve kterém každý prvek má jedinečný klíč, pomocí kterého jsou data automaticky uspořádávána.|
|[multimap – třída](../standard-library/multimap-class.md)|Používá pro ukládání a načítání dat z kolekce, ve kterém každý prvek má klíč, pomocí kterého jsou data automaticky uspořádávána a klíče nemusí mít jedinečné hodnoty.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
