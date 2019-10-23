---
title: '&lt;map &gt;'
ms.date: 11/04/2016
f1_keywords:
- <map>
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
ms.openlocfilehash: 2e861d2250585fbcdf3e1ef63d92f18185fc7f1c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687781"
---
# <a name="ltmapgt"></a>&lt;map &gt;

Definuje šablony tříd kontejneru mapy a multimap a jejich podpůrné šablony.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<map >

**Obor názvů:** std

> [!NOTE]
> Knihovna \<map > používá také příkaz `#include <initializer_list>`.

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|Verze mapy|Verze multimap|Popis|
|-----------------|----------------------|-----------------|
|[operator! = (map) – operátor](../standard-library/map-operators.md#op_neq)|[operator! = (multimap) – operátor](../standard-library/map-operators.md#op_neq)|Testuje, zda objekt map nebo multimap na levé straně operátoru není roven mapě nebo objektu multimap na pravé straně.|
|[operátor < (map)](../standard-library/map-operators.md#op_eq_eq)|[operátor < (multimap)](../standard-library/map-operators.md#op_eq_eq)|Testuje, zda je objekt map nebo multimap na levé straně operátoru menší než mapa nebo objekt multimap na pravé straně.|
|[operátor < = (map)](../standard-library/map-operators.md#op_lt)|[operator \< = (multimap) – operátor](../standard-library/map-operators.md#op_lt)|Testuje, zda je objekt map nebo multimap na levé straně operátoru menší než nebo roven mapě nebo objektu multimap na pravé straně.|
|[operator = = (map) – operátor](../standard-library/map-operators.md#op_eq_eq)|[operator = = (multimap) – operátor](../standard-library/map-operators.md#op_eq_eq_multimap)|Testuje, zda je objekt map nebo multimap na levé straně operátoru roven mapě nebo objektu multimap na pravé straně.|
|[operátor > (map)](../standard-library/map-operators.md#op_gt)|[operátor > (multimap)](../standard-library/map-operators.md#op_gt_multimap)|Testuje, zda je objekt map nebo multimap na levé straně operátoru větší než mapa nebo objekt multimap na pravé straně.|
|[operátor > = (map)](../standard-library/map-operators.md#op_gt_eq)|[operator > = (multimap) – operátor](../standard-library/map-operators.md#op_gt_eq_multimap)|Testuje, zda je objekt map nebo multimap na levé straně operátoru větší než nebo roven mapě nebo objektu multimap na pravé straně.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|Verze mapy|Verze multimap|Popis|
|-----------------|----------------------|-----------------|
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|Vyměňuje prvky dvou map nebo více map.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[value_compare – třída](../standard-library/value-compare-class-map.md)|Poskytuje objekt funkce, který může porovnat prvky mapy porovnáním hodnot jejich klíčů a určením jejich relativního pořadí v mapě.|
|[map – třída](../standard-library/map-class.md)|Používá se pro ukládání a načítání dat z kolekce, ve které každý z elementů má jedinečný klíč, se kterým jsou data automaticky řazena.|
|[multimap – třída](../standard-library/multimap-class.md)|Používá se pro ukládání a načítání dat z kolekce, ve které každý z elementů má klíč, se kterým jsou data automaticky řazena a klíče nemusí mít jedinečné hodnoty.|

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
