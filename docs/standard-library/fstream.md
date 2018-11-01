---
title: '&lt;fstream –&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: fcfb020bab2cb85b13caac9cdceee2359a7294d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476567"
---
# <a name="ltfstreamgt"></a>&lt;fstream –&gt;

Definuje několik tříd, které podporují operace iostreams na pořadí, které jsou uložené v externích souborech.

## <a name="syntax"></a>Syntaxe

```cpp
#include <fstream>

```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Typ `basic_filebuf` specializované na **char** parametry šablony.|
|[fstream –](../standard-library/fstream-typedefs.md#fstream)|Typ `basic_fstream` specializované na **char** parametry šablony.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Typ `basic_ifstream` specializované na **char** parametry šablony.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Typ `basic_ofstream` specializované na **char** parametry šablony.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Typ `basic_fstream` specializované na **wchar_t** parametry šablony.|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Typ `basic_ifstream` specializované na **wchar_t** parametry šablony.|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Typ `basic_ofstream` specializované na **wchar_t** parametry šablony.|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Typ `basic_filebuf` specializované na **wchar_t** parametry šablony.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|Třída šablony popisuje vyrovnávací paměť datového proudu, který řídí přenosu prvky typu `Elem`, jehož vlastnosti znaků určuje třídu `Tr`, do a z pořadí prvků, které jsou uložené v externím souboru.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|Třída šablony popisuje objekt, který řídí vkládání a extrakci prvků a kódovaného objektů pomocí vyrovnávací paměť datového proudu třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md)\<**Elem**,  **Tr**>, s prvky typu `Elem`, jehož vlastnosti znaků určuje třídu `Tr`.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|Třída šablony popisuje objekt, který řídí extrakce prvků a kódovaného objekty z vyrovnávací paměti datového proudu třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, s prvky typu `Elem`, jehož vlastnosti znaků určuje třídu `Tr`.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|Třída šablony popisuje objekt, který řídí vkládání prvků a kódovaného objekty do vyrovnávací paměti datového proudu třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, s prvky typu `Elem`, jehož vlastnosti znaků určuje třídu `Tr`.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
