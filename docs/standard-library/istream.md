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
ms.openlocfilehash: 0ad27bf849e8d4b9188868b9a29bf423b4cafafa
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458732"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Definuje třídu šablony basic_istream, která vymezuje extrakce pro iostreams, a třídu šablony basic_iostream, která řeší vložení i extrakci. Záhlaví také definuje související manipulátor. Tento hlavičkový soubor obvykle obsahuje jinou hlavičku iostreams; Jenom zřídka je budete muset zahrnout přímo.

## <a name="syntax"></a>Syntaxe

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|Typ `basic_iostream` specializovaný na **char**.|
|[istream](../standard-library/istream-typedefs.md#istream)|Typ `basic_istream` specializovaný na **char**.|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Typ `basic_iostream` specializovaný na **WCHAR**.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Typ `basic_istream` specializovaný na **WCHAR**.|

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|Přeskočí prázdné znaky v datovém proudu.|
|[swap](../standard-library/istream-functions.md#istream_swap)|Vyměňuje dva objekty streamu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor > >](../standard-library/istream-operators.md#op_gt_gt)|Extrahuje znaky a řetězce z datového proudu.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Třída streamu, která může provádět vstup i výstup.|
|[basic_istream](../standard-library/basic-istream-class.md)|Třída šablony popisuje objekt, který ovládá extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu pomocí prvků typu `Elem`, označovaného také jako [char_type](../standard-library/basic-ios-class.md#char_type), jejichž znakové vlastnosti jsou určeny třídou `Tr`, také označuje se jako [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
