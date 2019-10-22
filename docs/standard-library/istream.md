---
title: '&lt;istream &gt;'
ms.date: 11/04/2016
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
ms.openlocfilehash: 8e9675a673462c8eaab94d29a3ae36a4786737b7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687855"
---
# <a name="ltistreamgt"></a>&lt;istream &gt;

Definuje šablonu třídy basic_istream, která vymezuje extrakce pro iostreams, a šablonu třídy basic_iostream, která řeší vložení i extrakci. Záhlaví také definuje související manipulátor. Tento hlavičkový soubor obvykle obsahuje jinou hlavičku iostreams; Jenom zřídka je budete muset zahrnout přímo.

## <a name="syntax"></a>Syntaxe

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[iostream –](../standard-library/istream-typedefs.md#iostream)|Typ `basic_iostream` specializované na **char**.|
|[IStream](../standard-library/istream-typedefs.md#istream)|Typ `basic_istream` specializované na **char**.|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Typ `basic_iostream` specializované na **WCHAR**.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Typ `basic_istream` specializované na **WCHAR**.|

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[specifikace](../standard-library/istream-functions.md#ws)|Přeskočí prázdné znaky v datovém proudu.|
|[adresu](../standard-library/istream-functions.md#istream_swap)|Vyměňuje dva objekty streamu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor > >](../standard-library/istream-operators.md#op_gt_gt)|Extrahuje znaky a řetězce z datového proudu.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Třída streamu, která může provádět vstup i výstup.|
|[basic_istream](../standard-library/basic-istream-class.md)|Šablona třídy popisuje objekt, který ovládá extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu pomocí prvků typu `Elem`, označovaného také jako [char_type](../standard-library/basic-ios-class.md#char_type), jejichž znakové vlastnosti jsou určeny `Tr` třídy, označované také jako [ traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[iostream – programování](../standard-library/iostream-programming.md) \
[iostreams – konvence](../standard-library/iostreams-conventions.md)
