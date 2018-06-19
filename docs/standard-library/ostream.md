---
title: '&lt;ostream –&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
dev_langs:
- C++
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf7b8bf3015879643728358258cfe4a67536b3ea
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863784"
---
# <a name="ltostreamgt"></a>&lt;ostream –&gt;

Definuje třídu šablony [basic_ostream](../standard-library/basic-ostream-class.md), která zprostředkovává vložení pro iostreams. Záhlaví také definuje několik související manipulátory. (Tuto hlavičku je obvykle zahrnuté pro můžete jiným iostreams záhlaví. Je potřeba jen zřídka ho zahrňte přímo.)

## <a name="syntax"></a>Syntaxe

```cpp
#include <ostream>

```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[ostream –](../standard-library/ostream-typedefs.md#ostream)|Umožňuje vytvořit typ z `basic_ostream` který se specializuje na `char` a `char_traits` specializované na `char`.|
|[wostream –](../standard-library/ostream-typedefs.md#wostream)|Umožňuje vytvořit typ z `basic_ostream` který se specializuje na `wchar_t` a `char_traits` specializované na `wchar_t`.|

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Ukončí řádku a vyprázdní vyrovnávací paměť.|
|[ukončení](../standard-library/ostream-functions.md#ends)|Ukončí řetězec.|
|[Vyprázdnění](../standard-library/ostream-functions.md#flush)|Vyprázdní vyrovnávací paměť.|
|[Swap](../standard-library/ostream-functions.md#swap)|Výměny hodnoty doleva `basic_ostream` objektu parametr pro ty právo `basic_ostream` parametru objektu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor <<](../standard-library/ostream-operators.md#op_lt_lt)|Různé typy zapíše do datového proudu.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_ostream –](../standard-library/basic-ostream-class.md)|Šablony třídy popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
