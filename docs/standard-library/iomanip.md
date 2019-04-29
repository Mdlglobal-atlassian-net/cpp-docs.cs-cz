---
title: '&lt;iomanip –&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: 983fbc190fb83b81534e3888c748c0bf9c235638
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404933"
---
# <a name="ltiomanipgt"></a>&lt;iomanip –&gt;

Zahrnout `iostreams` standardní hlavičku \<iomanip > k definování několika manipulátory, které každý přijímají jediný argument.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iomanip>
```

## <a name="remarks"></a>Poznámky

Každá z těchto manipulátory vrací neurčeného typu, volá `T1` prostřednictvím `T10`, které obě přetížení `basic_istream` \< **Elem**, **Tr** > `::` [operátor >>](../standard-library/istream-operators.md#op_gt_gt) a `basic_ostream` \< **Elem**, **Tr** > `::` [operátor <<](../standard-library/ostream-operators.md#op_lt_lt).

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|Získá peněžní částku, volitelně v mezinárodním formátu.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Získá čas ve struktuře čas pomocí určeného formátu.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|Poskytuje peněžní částku, volitelně v mezinárodním formátu.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|Poskytuje čas ve struktuře čas a řetězec formátu použitý.|
|[v uvozovkách](../standard-library/iomanip-functions.md#quoted)|Umožňuje pohodlný dopad na dobu odezvy řetězce s operátory vložení a extrakce.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Vymaže zadané příznaky.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|Nastavte základ pro celá čísla.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|Nastaví znak, který se použije k vyplnění mezer v zobrazení zarovnána vpravo.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Nastaví zadané příznaky.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Nastaví přesnosti pro hodnoty s plovoucí desetinnou čárkou.|
|[setw](../standard-library/iomanip-functions.md#setw)|Určuje šířku pole zobrazení.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
