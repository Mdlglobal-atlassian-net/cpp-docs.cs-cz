---
title: '&lt;iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: b9da0de64bbb0ef48a6a9741ff941e6abda0e705
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449211"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

Zahrňte \<standardní hlavičku iomanip > k definování několika manipulátorů, které každý z nich vezme jeden argument. `iostreams`

## <a name="syntax"></a>Syntaxe

```cpp
#include <iomanip>
```

## <a name="remarks"></a>Poznámky

Každý z těchto `T1` manipulací vrátí nespecifikovaný typ, \< `basic_istream`který je `T10`volán pomocí, který přetížení **elem**, **TR**>`::`[operator > >](../standard-library/istream-operators.md#op_gt_gt) a `basic_ostream` **Elem,** [operátor](../standard-library/ostream-operators.md#op_lt_lt) **TR**<<.> \<`::`

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|Získá peněžní částku, volitelně v mezinárodním formátu.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Získá čas v časové struktuře pomocí zadaného formátu.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|Poskytuje peněžní částku, volitelně v mezinárodním formátu.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|Poskytuje čas v časové struktuře a řetězec formátu, který se má použít.|
|[uvedená](../standard-library/iomanip-functions.md#quoted)|Umožňuje pohodlné kulaté Trip řetězců s operátory vložení a extrakce.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Vymaže zadané příznaky.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|Nastaví základ pro celá čísla.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|Nastaví znak, který se použije k vyplňování mezer v zobrazení zarovnaném vpravo.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Nastaví zadané příznaky.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Nastaví přesnost hodnot s plovoucí desetinnou čárkou.|
|[setw](../standard-library/iomanip-functions.md#setw)|Určuje šířku pole zobrazení.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
