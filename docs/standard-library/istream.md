---
title: '&lt;istream&gt;'
ms.date: 11/04/2016
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
ms.openlocfilehash: 2e39c0de5b11c9aa0a4c69f0142841469ef798c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413278"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Definuje basic_istream – třída šablony, která zprostředkovává extrakce pro iostreams, a basic_iostream – třída šablony, která zprostředkovává vložení a extrakce. Záhlaví definuje také související manipulátor. Tento soubor hlavičky je obvykle součástí za vás pomocí jiné záhlaví iostreams; obvykle nemusí obsahovat přímo.

## <a name="syntax"></a>Syntaxe

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|Typ `basic_iostream` specializované na **char**.|
|[istream](../standard-library/istream-typedefs.md#istream)|Typ `basic_istream` specializované na **char**.|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Typ `basic_iostream` specializované na **wchar**.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Typ `basic_istream` specializované na **wchar**.|

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|Přeskočí prázdné místo v datovém proudu.|
|[swap](../standard-library/istream-functions.md#istream_swap)|Vyměňuje dva objekty stream.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|Extrahuje z datového proudu znaků a řetězce.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Datový proud třídu, která můžete provést jak vstupu a výstupu.|
|[basic_istream](../standard-library/basic-istream-class.md)|Třída šablony popisuje objekt, který řídí extrakce prvků a kódovaného objekty z vyrovnávací paměti datového proudu s prvky typu `Elem`, označované také jako [char_type](../standard-library/basic-ios-class.md#char_type), jehož vlastnosti znaků jsou určené třídy `Tr`, označované také jako [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
