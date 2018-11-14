---
title: '&lt;ostream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
ms.openlocfilehash: eb73c77f0e2658cf750cf17ca85549a09d1cbe51
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523764"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Třída šablony definuje [basic_ostream –](../standard-library/basic-ostream-class.md), která zprostředkovává vložení pro iostreams. Záhlaví také definuje několik souvisejících manipulátory. (Toto záhlaví je obvykle součástí za vás jiným iostreams záhlaví. Zřídka musíte zahrnout přímo.)

## <a name="syntax"></a>Syntaxe

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Vytvoří typ z `basic_ostream` , který se specializuje na **char** a `char_traits` specializované na **char**.|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|Vytvoří typ z `basic_ostream` , který se specializuje na **wchar_t** a `char_traits` specializované na **wchar_t**.|

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Ukončení řádku a vyprázdní vyrovnávací paměť.|
|[končí](../standard-library/ostream-functions.md#ends)|Ukončí řetězec.|
|[Vyprázdnění](../standard-library/ostream-functions.md#flush)|Vyprázdní vyrovnávací paměť.|
|[Prohození](../standard-library/ostream-functions.md#swap)|Vymění hodnoty levé straně `basic_ostream` parametru objektu pro ty pravé `basic_ostream` parametru objektu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor <<](../standard-library/ostream-operators.md#op_lt_lt)|Různé typy zapíše do datového proudu.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_ostream –](../standard-library/basic-ostream-class.md)|Třída šablony popisuje objekt, který řídí vkládání prvků a kódovaného objekty do vyrovnávací paměti datového proudu.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
