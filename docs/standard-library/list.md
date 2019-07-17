---
title: '&lt;list&gt;'
ms.date: 11/04/2016
f1_keywords:
- <list>
- std::<list>
helpviewer_keywords:
- list header
ms.assetid: 2345823b-5612-44d8-95d3-aa96ed076d17
ms.openlocfilehash: f2c04bb73bfa379ea87ba4c950bf805931c16ba1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245568"
---
# <a name="ltlistgt"></a>&lt;list&gt;

Definuje kontejner šablony třídy seznamu a několik podpůrných šablon.

## <a name="syntax"></a>Syntaxe

```cpp
#include <list>
```

> [!NOTE]
> \<Seznamu > Knihovna také používá `#include <initializer_list>` příkazu.

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/list-operators.md#op_neq)|Testuje, zda je objekt seznamu na levé straně operátoru není roven objektu seznamu na pravé straně.|
|[Operator <](../standard-library/list-operators.md#op_lt)|Testuje, zda je objekt seznamu na levé straně operátoru menší než objekt seznamu na pravé straně.|
|[– Operátor\<=](../standard-library/list-operators.md#op_gt_eq)|Testuje, zda je objekt v seznamu na levé straně operátoru je menší než nebo roven objektu seznamu na pravé straně.|
|[operator==](../standard-library/list-operators.md#op_eq_eq)|Testuje, zda je objekt seznamu na levé straně operátoru roven objektu seznamu na pravé straně.|
|[Operator >](../standard-library/list-operators.md#op_gt)|Testuje, zda je objekt seznamu na levé straně operátoru větší než objekt seznamu na pravé straně.|
|[operator>=](../standard-library/list-operators.md#op_gt_eq)|Testuje, zda je objekt seznamu na levé straně operátoru větší než nebo roven objektu seznamu na pravé straně.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[swap](../standard-library/list-functions.md#swap)|Vymění prvky dvou seznamů.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[list – třída](../standard-library/list-class.md)|Třída šablony kontejnery sekvence, které zachovávají prvky ve lineární uspořádání a umožní efektivní vložení a odstranění v libovolném umístění v rámci pořadí.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
