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
ms.openlocfilehash: 8de66718dab10b5c95e8c1ab7fd0bd17e9b4ee5e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448175"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Definuje třídu šablony [basic_ostream](../standard-library/basic-ostream-class.md), která řeší vložení pro iostreams. Záhlaví také definuje několik souvisejících manipulací. (Tato hlavička je obvykle zahrnutá v jiné hlavičce iostreams. Jenom zřídka je potřeba ho zahrnout přímo.)

## <a name="syntax"></a>Syntaxe

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Vytvoří typ z `basic_ostream` tohoto typu, který je specializovaný na `char_traits` **char** a specializovaný na **char**.|
|[wostream –](../standard-library/ostream-typedefs.md#wostream)|Vytvoří typ z `basic_ostream` , který je specializovaný na **wchar_t** a `char_traits` specializovaný na **wchar_t**.|

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Ukončí řádek a vyprázdní vyrovnávací paměť.|
|[přípon](../standard-library/ostream-functions.md#ends)|Ukončí řetězec.|
|[zaznamenány](../standard-library/ostream-functions.md#flush)|Vyprázdní vyrovnávací paměť.|
|[swap](../standard-library/ostream-functions.md#swap)|Vyměňuje hodnoty levého `basic_ostream` objektu parametru pro objekty správného `basic_ostream` parametru objektu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor < <](../standard-library/ostream-operators.md#op_lt_lt)|Zapisuje do datového proudu různé typy.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|Třída šablony popisuje objekt, který řídí vložení prvků a zakódovaných objektů do vyrovnávací paměti datového proudu.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
