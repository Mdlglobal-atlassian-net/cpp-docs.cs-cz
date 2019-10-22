---
title: '&lt;fstream &gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 1f85367b9ae527c9387d085acc1496bfbbf7cc9e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688040"
---
# <a name="ltfstreamgt"></a>&lt;fstream &gt;

Definuje několik tříd, které podporují operace iostreams na sekvencích uložených v externích souborech.

## <a name="syntax"></a>Syntaxe

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Typ `basic_filebuf` specializované na parametrech **char** Template.|
|[fstream –](../standard-library/fstream-typedefs.md#fstream)|Typ `basic_fstream` specializované na parametrech **char** Template.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Typ `basic_ifstream` specializované na parametrech **char** Template.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Typ `basic_ofstream` specializované na parametrech **char** Template.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Typ `basic_fstream` specializované na parametry šablony **wchar_t** .|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Typ `basic_ifstream` specializované na parametry šablony **wchar_t** .|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Typ `basic_ofstream` specializované na parametry šablony **wchar_t** .|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Typ `basic_filebuf` specializované na parametry šablony **wchar_t** .|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|Šablona třídy popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků typu `Elem`, jejichž znakové vlastnosti jsou určeny třídou `Tr`, do a z sekvence prvků uložených v externím souboru.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|Šablona třídy popisuje objekt, který ovládá vkládání a extrakci prvků a kódovaných objektů pomocí vyrovnávací paměti datového proudu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **TR**>, s prvky typu `Elem`, jejichž znak vlastnosti jsou určeny `Tr` třídy.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|Šablona třídy popisuje objekt, který řídí extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **TR**>, s prvky typu `Elem`, jejichž znaky jsou určeno `Tr` třídy.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|Šablona třídy popisuje objekt, který řídí vložení prvků a zakódovaných objektů do vyrovnávací paměti datového proudu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **TR**>, s prvky typu `Elem`, jejichž znaky jsou určeny. třídou `Tr`.|

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[iostream – programování](../standard-library/iostream-programming.md) \
[iostreams – konvence](../standard-library/iostreams-conventions.md)
