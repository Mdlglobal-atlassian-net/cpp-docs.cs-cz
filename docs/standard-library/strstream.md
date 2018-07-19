---
title: '&lt;strstream –&gt; | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <strstream>
dev_langs:
- C++
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1695306ddc53a8150917eef8b27f5d3edce2bf3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961861"
---
# <a name="ltstrstreamgt"></a>&lt;strstream –&gt;

Definuje několik tříd, které podporují operace iostreams na pořadí, které jsou uložené v přidělené pole **char** objektu. Tato sekvence jsou snadno převést do a z řetězců C.

## <a name="syntax"></a>Syntaxe

```cpp
#include <strstream>

```

## <a name="remarks"></a>Poznámky

Objekty typu `strstream` fungují s `char` *, které jsou C řetězce. Použití [ \<sstream >](../standard-library/sstream.md) pro práci s objekty typu [basic_string](../standard-library/basic-string-class.md).

> [!NOTE]
> Třídy v \<strstream – > jsou zastaralé. Zvažte použití třídy v \<sstream > místo toho.

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[strstreambuf – třída](../standard-library/strstreambuf-class.md)|Tato třída popisuje vyrovnávací paměť datového proudu, který řídí přenosu prvky do a z pořadí prvků uložených v **char** objektu array.|
|[istrstream – třída](../standard-library/istrstream-class.md)|Tato třída popisuje objekt, který řídí extrakce prvků a kódovaného objekty z vyrovnávací paměti datového proudu třídy [strstreambuf –](../standard-library/strstreambuf-class.md).|
|[ostrstream – třída](../standard-library/ostrstream-class.md)|Tato třída popisuje objekt, který řídí vkládání prvků a kódovaného objekty do vyrovnávací paměti datového proudu třídy [strstreambuf –](../standard-library/strstreambuf-class.md).|
|[strstream – třída](../standard-library/strstream-class.md)|Tato třída popisuje objekt, který řídí vkládání a extrakci prvků a kódovaného objektů pomocí vyrovnávací paměť datového proudu třídy [strstreambuf –](../standard-library/strstreambuf-class.md).|

## <a name="see-also"></a>Viz také:

[\<strstream – >](../standard-library/strstream.md)<br/>
[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
