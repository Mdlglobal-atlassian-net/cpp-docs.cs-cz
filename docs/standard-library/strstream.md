---
title: '&lt;strstream –&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: 72b96c300aba1729823462ce6671e2f9a5285761
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523712"
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
