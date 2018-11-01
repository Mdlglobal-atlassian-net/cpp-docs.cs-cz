---
title: '&lt;Nástroj&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: 318cd86832875f3701c5d164ce9150e6adddb242
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467197"
---
# <a name="ltutilitygt"></a>&lt;Nástroj&gt;

Definuje typy standardní knihovny C++, funkce a operátory, které pomáhají vytvářet a spravovat páry objekty, které jsou užitečné pokaždé, když se dva objekty, třeba zacházet, jako by byly jeden.

## <a name="syntax"></a>Syntaxe

```cpp
#include <utility>

```

## <a name="remarks"></a>Poznámky

Páry se často používá ve standardní knihovně jazyka C++. Jako argumenty a návratové hodnoty pro různé funkce a jako typy elementů pro kontejnery, jako jsou povinné [map – třída](../standard-library/map-class.md) a [multimap – třída](../standard-library/multimap-class.md). \<Nástroj > hlavičky je automaticky zahrnut objektem \<mapy > jako pomoc při správě jejich klíč/hodnota zadejte pár prvků.

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[tuple_element –](../standard-library/tuple-element-class-tuple.md)|Třída, která zabalí typu `pair` elementu.|
|[tuple_size –](../standard-library/tuple-size-class-tuple.md)|Třída, která zabalí `pair` počet prvků.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[Vpřed](../standard-library/utility-functions.md#forward)|Zachová typu odkazu (buď `lvalue` nebo `rvalue`) argumentu z právě zakrytý dokonalé předávání.|
|[get](../standard-library/utility-functions.md#get)|Funkce, která získá prvek z `pair` objektu.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Pomocná funkce šablony používá k vytvoření objektů typu `pair`, kde jsou typy komponenty založené na datové typy, které předávají jako parametry.|
|[Přesunutí](../standard-library/utility-functions.md#move)|Vrátí předaný argument jako `rvalue` odkaz.|
|[Prohození](../standard-library/utility-functions.md#swap)|Vymění prvky dvou `pair` objekty.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|Testuje, zda je objekt dvojice na levé straně operátoru není roven párový objekt na pravé straně.|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|Testuje, zda objekt dvojice na levé straně operátoru roven objektu pair na pravé straně.|
|[Operator <](../standard-library/utility-operators.md#op_lt)|Testuje, zda je pár objekt na levé straně operátoru je menší než objekt dvojice na pravé straně.|
|[– Operátor\<=](../standard-library/utility-operators.md#op_gt_eq)|Testuje, zda je pár objekt na levé straně operátoru je menší než nebo rovna hodnotě párový objekt na pravé straně.|
|[Operator >](../standard-library/utility-operators.md#op_gt)|Testuje, zda je objekt dvojice na levé straně operátoru větší než párový objekt na pravé straně.|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|Testuje, zda je objekt dvojice na levé straně operátoru větší než nebo rovna hodnotě párový objekt na pravé straně.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[Identita](../standard-library/identity-structure.md)||
|[dvojice](../standard-library/pair-structure.md)|Typ, který poskytuje možnost zpracovávat dva objekty jako jednoho objektu.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
