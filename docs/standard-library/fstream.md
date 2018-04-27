---
title: '&lt;fstream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <fstream>
dev_langs:
- C++
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fe86803f986853335fbad15e0c3323d9365d381
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

Definuje několik tříd, které podporují operace iostreams v pořadí, které jsou uložené v externích souborů.

## <a name="syntax"></a>Syntaxe

```cpp
#include <fstream>

```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Typ `basic_filebuf` specializované na `char` parametry šablony.|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|Typ `basic_fstream` specializované na `char` parametry šablony.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Typ `basic_ifstream` specializované na `char` parametry šablony.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Typ `basic_ofstream` specializované na `char` parametry šablony.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Typ `basic_fstream` specializované na `wchar_t` parametry šablony.|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Typ `basic_ifstream` specializované na `wchar_t` parametry šablony.|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Typ `basic_ofstream` specializované na `wchar_t` parametry šablony.|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Typ `basic_filebuf` specializované na `wchar_t` parametry šablony.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|Šablony třídy popisuje datový proud vyrovnávací paměť, která řídí přenos elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**, do a z pořadí elementů uložená v externí soubor.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|Šablony třídy popisuje objekt, který řídí vložení a extrakce elementů a kódovaného objekty pomocí datového proudu vyrovnávací paměti třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**,  **Tr**>, elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|Šablony třídy popisuje objekt, který řídí extrakce elementů a kódovaného objekty z datového proudu vyrovnávací paměti třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|Šablony třídy popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
