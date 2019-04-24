---
title: '&lt;fstream –&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 20efdc755b7f706fc6ee962daa32bd352df39d45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159766"
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
