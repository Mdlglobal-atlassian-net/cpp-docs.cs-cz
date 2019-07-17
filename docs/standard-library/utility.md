---
title: '&lt;Nástroj&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: 76b04c3c26f6ec49f1d816feaeec7e21312d79a9
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246285"
---
# <a name="ltutilitygt"></a>&lt;Nástroj&gt;

Definuje typy standardní knihovny C++, funkce a operátory, které pomáhají vytvářet a spravovat páry objekty, které jsou užitečné pokaždé, když se dva objekty, třeba zacházet, jako by byly jeden.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nástroje >

**Namespace:** std

## <a name="remarks"></a>Poznámky

Páry se často používá ve standardní knihovně jazyka C++. Jako argumenty a návratové hodnoty pro různé funkce a jako typy elementů pro kontejnery, jako jsou povinné [map – třída](../standard-library/map-class.md) a [multimap – třída](../standard-library/multimap-class.md). \<Nástroj > hlavičky je automaticky zahrnut objektem \<mapy > jako pomoc při správě jejich klíč/hodnota zadejte pár prvků.

> [!NOTE]
> \<Nástroj > hlavičky používá příkaz `#include <initializer_list>`. Také odkazuje na `class tuple` jak jsou definovány v \<řazené kolekce členů >.

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|||
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|S plovoucí desetinnou čárkou formát pro primitivní číselný převod.|
|[tuple_element –](../standard-library/tuple-element-class-tuple.md)|Třída, která zabalí typu `pair` elementu.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Třída, která zabalí `pair` počet prvků.|

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
|[as_const](../standard-library/utility-functions.md#asconst)|Vrátí hodnotu typu.|
|[declval –](../standard-library/utility-functions.md#declval)|Zkrácený tvar vlastností vyhodnocení výrazu.|
|[exchange](../standard-library/utility-functions.md#exchange)|Přiřadí novou hodnotu na objekt a vrátí jeho starou hodnotu.|
|[Vpřed](../standard-library/utility-functions.md#forward)|Zachová typu odkazu (buď `lvalue` nebo `rvalue`) argumentu z právě zakrytý dokonalé předávání.|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|Funkce, která získá prvek z `pair` objektu.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Pomocná funkce šablony používá k vytvoření objektů typu `pair`, kde jsou typy komponenty založené na datové typy, které předávají jako parametry.|
|[Přesunutí](../standard-library/utility-functions.md#move)|Vrátí předaný argument jako `rvalue` odkaz.|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[swap](../standard-library/utility-functions.md#swap)|Vymění prvky dvou `pair` objekty.|
|[to_chars](../standard-library/utility-functions.md#to_chars)|Převede hodnotu na řetězec znaků.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|Testuje, zda je objekt dvojice na levé straně operátoru není roven párový objekt na pravé straně.|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|Testuje, zda objekt dvojice na levé straně operátoru roven objektu pair na pravé straně.|
|[– Operátor\<](../standard-library/utility-operators.md#op_lt)|Testuje, zda je pár objekt na levé straně operátoru je menší než objekt dvojice na pravé straně.|
|[– Operátor\<=](../standard-library/utility-operators.md#op_gt_eq)|Testuje, zda je pár objekt na levé straně operátoru je menší než nebo rovna hodnotě párový objekt na pravé straně.|
|[Operator >](../standard-library/utility-operators.md#op_gt)|Testuje, zda je objekt dvojice na levé straně operátoru větší než párový objekt na pravé straně.|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|Testuje, zda je objekt dvojice na levé straně operátoru větší než nebo rovna hodnotě párový objekt na pravé straně.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|Použít pro struktury `from_chars`.|
|[Identita](../standard-library/identity-structure.md)|Struktura, která obsahuje definici typu jako parametr šablony.|
|[in_place_t](../standard-library/in-place-t-struct.md)|Zahrnuje také struktury `in_place_type_t` a `in_place_index_t`.|
|[integer_sequence –](../standard-library/integer-sequence-class.md)|Představuje celé číslo sekvence.|
|[dvojice](../standard-library/pair-structure.md)|Typ, který poskytuje možnost zpracovávat dva objekty jako jednoho objektu.|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|Typ použitý udržovat samostatnou konstruktor a přetížení funkce.|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|Použít pro struktury `to_chars`.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
