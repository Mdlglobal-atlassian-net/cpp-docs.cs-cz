---
title: '&lt;ostream &gt;'
ms.date: 11/04/2016
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
ms.openlocfilehash: 3838e215ffac42ec6902ab6a9837f638153cf184
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689170"
---
# <a name="ltostreamgt"></a>&lt;ostream &gt;

Definuje šablonu třídy [basic_ostream](../standard-library/basic-ostream-class.md), která opravuje vložení pro iostreams. Záhlaví také definuje několik souvisejících manipulací. (Tato hlavička je obvykle zahrnutá v jiné hlavičce iostreams. Jenom zřídka je potřeba ho zahrnout přímo.)

## <a name="syntax"></a>Syntaxe

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Vytvoří typ z `basic_ostream`, který je specializovaný na **char** a `char_traits` specializované na **char**.|
|[wostream –](../standard-library/ostream-typedefs.md#wostream)|Vytvoří typ z `basic_ostream` specializovaného na **wchar_t** a `char_traits` specializované na **wchar_t**.|

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Ukončí řádek a vyprázdní vyrovnávací paměť.|
|[přípon](../standard-library/ostream-functions.md#ends)|Ukončí řetězec.|
|[zaznamenány](../standard-library/ostream-functions.md#flush)|Vyprázdní vyrovnávací paměť.|
|[adresu](../standard-library/ostream-functions.md#swap)|Vymění hodnoty levého `basic_ostream` parametru objektu u pravého parametru objektu `basic_ostream`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor < <](../standard-library/ostream-operators.md#op_lt_lt)|Zapisuje do datového proudu různé typy.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|Šablona třídy popisuje objekt, který řídí vložení prvků a zakódovaných objektů do vyrovnávací paměti datového proudu.|

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[iostream – programování](../standard-library/iostream-programming.md) \
[iostreams – konvence](../standard-library/iostreams-conventions.md)
