---
title: '&lt;fstream –&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: ba6a4152b8d37f5b0186f9d05c6ba850e8c2e54c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454024"
---
# <a name="ltfstreamgt"></a>&lt;fstream –&gt;

Definuje několik tříd, které podporují operace iostreams na sekvencích uložených v externích souborech.

## <a name="syntax"></a>Syntaxe

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Typ `basic_filebuf` specializovaný na parametry **znak** šablony.|
|[fstream –](../standard-library/fstream-typedefs.md#fstream)|Typ `basic_fstream` specializovaný na parametry **znak** šablony.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Typ `basic_ifstream` specializovaný na parametry **znak** šablony.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Typ `basic_ofstream` specializovaný na parametry **znak** šablony.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Typ `basic_fstream` specializovaný v parametrech šablony **wchar_t** .|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Typ `basic_ifstream` specializovaný v parametrech šablony **wchar_t** .|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Typ `basic_ofstream` specializovaný v parametrech šablony **wchar_t** .|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Typ `basic_filebuf` specializovaný v parametrech šablony **wchar_t** .|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|Třída šablony popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků typu `Elem`, jejichž znakové vlastnosti jsou určeny třídou `Tr`, na a z sekvence prvků uložených v externím souboru.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|Třída šablony popisuje objekt, který ovládá vkládání a extrakci prvků a kódovaných objektů pomocí vyrovnávací paměti datového proudu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**elem**, **TR**> s prvky typu `Elem`, jejichž vlastnosti znaků jsou určeny třídou `Tr`.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|Třída šablony popisuje objekt, který ovládá extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**elem**, **TR**>, s prvky typu `Elem`, jejichž znaky jsou. jsou určeny třídou `Tr`.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|Třída šablony popisuje objekt, který řídí vložení prvků a zakódovaných objektů do vyrovnávací paměti datového proudu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**elem**, **TR**>, s prvky typu `Elem`, jejichž vlastnosti znaku jsou. jsou určeny třídou `Tr`.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
