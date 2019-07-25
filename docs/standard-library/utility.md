---
title: '&lt;spuštění&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: eaae94bcffcda6e113001dd7070bcc80e7c14d09
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458070"
---
# <a name="ltutilitygt"></a>&lt;spuštění&gt;

Definuje C++ standardní typy knihoven, funkce a operátory, které vám pomohou sestavit a spravovat páry objektů, které jsou užitečné, když se dva objekty musí zacházet, jako kdyby byly v jednom.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> nástrojů

**Obor názvů:** std

## <a name="remarks"></a>Poznámky

Páry se běžně používají ve C++ standardní knihovně. Jsou vyžadovány jako argumenty a návratové hodnoty pro různé funkce a jako typy prvků pro kontejnery, jako jsou [třídy map](../standard-library/map-class.md) a [třídy multimap](../standard-library/multimap-class.md). Záhlaví nástroje > automaticky obsahuje mapu >, která pomáhá při správě jejich prvků typu dvojice klíč/hodnota. \< \<

> [!NOTE]
> Nástroj > záhlaví používá příkaz `#include <initializer_list>`. \< Odkazuje také na `class tuple` definování v \<řazené kolekci členů >.

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|||
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|Formát s plovoucí desetinnou čárkou pro primitivní číselný převod.|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|Třída, která zabalí typ `pair` elementu.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Třída, která obaluje `pair` počet prvků.|

### <a name="objects"></a>Objekty

|||
|-|-|
|[index_sequence](../standard-library/utility-functions.md#index_sequence)||
|[index_sequence_for](../standard-library/utility-functions.md#index_sequence_for)||
|[make_index_sequence](../standard-library/utility-functions.md#make_index_sequence)||
|[make_integer_sequence](../standard-library/utility-functions.md#make_integer_sequence)||

### <a name="functions"></a>Funkce

|||
|-|-|
|[as_const](../standard-library/utility-functions.md#asconst)|Vrátí typ.|
|[declval –](../standard-library/utility-functions.md#declval)|Zkrácené vyhodnocení výrazu.|
|[exchange](../standard-library/utility-functions.md#exchange)|Přiřadí novou hodnotu objektu a vrátí jeho starou hodnotu.|
|[Komisi](../standard-library/utility-functions.md#forward)|Zachová odkazový typ ( `lvalue` buď `rvalue`nebo) argumentu, ze kterého je zakryto dokonalým přesměrováním.|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|Funkce, která získá prvek z `pair` objektu.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Pomocná funkce šablony použitá k sestavení objektů typu `pair`, kde jsou typy komponent založeny na datových typech předaných jako parametry.|
|[Pøesunout](../standard-library/utility-functions.md#move)|Vrátí předaný argument jako `rvalue` referenci.|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[swap](../standard-library/utility-functions.md#swap)|Vyměňuje prvky dvou `pair` objektů.|
|[to_chars](../standard-library/utility-functions.md#to_chars)|Převede hodnotu na řetězec znaků.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|Testuje, zda dvojice objektu na levé straně operátoru není rovna objektu páru na pravé straně.|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|Testuje, zda je objekt dvojice na levé straně operátoru roven objektu páru na pravé straně.|
|[podnikatel\<](../standard-library/utility-operators.md#op_lt)|Testuje, zda je objekt dvojice na levé straně operátoru menší než objekt dvojice na pravé straně.|
|[podnikatel\<=](../standard-library/utility-operators.md#op_gt_eq)|Testuje, zda je objekt dvojice na levé straně operátoru menší než nebo roven objektu páru na pravé straně.|
|[operátor >](../standard-library/utility-operators.md#op_gt)|Testuje, zda je objekt dvojice na levé straně operátoru větší než dvojice objektu na pravé straně.|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|Testuje, zda je objekt dvojice na levé straně operátoru větší než nebo roven objektu páru na pravé straně.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|Struktura použitá pro `from_chars`.|
|[odcizen](../standard-library/identity-structure.md)|Struktura, která poskytuje definici typu jako parametr šablony.|
|[in_place_t](../standard-library/in-place-t-struct.md)|Zahrnuje také struktury `in_place_type_t` a `in_place_index_t`.|
|[integer_sequence](../standard-library/integer-sequence-class.md)|Představuje posloupnost celého čísla.|
|[spojení](../standard-library/pair-structure.md)|Typ, který poskytuje schopnost zacházet se dvěma objekty jako s jedním objektem.|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|Typ, který slouží k zachování samostatného přetížení konstruktoru a funkce.|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|Struktura použitá pro `to_chars`.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
