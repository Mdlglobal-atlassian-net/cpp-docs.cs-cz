---
title: Přiřazení znaků
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
ms.openlocfilehash: 88c42435d336ba78e87c9acfe3ada5fddbd18fb8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410743"
---
# <a name="character-assignment"></a>Přiřazení znaků

Zvažte následující příklad, ve kterém **při** smyčky vyhledá v řetězci, zkopíruje všechny znaky s výjimkou "X" do jiného řetězce:

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
        *sz1++ = *sz2++;
    else
        sz2++;
}
```

Kód zkopíruje bajt `sz2` do umístění, na které odkazuje `sz1`, pak inkrementuje `sz1` přijímat další bajt. Avšak v tom případě další znak v `sz2` je dvoubajtové znakové přiřazení `sz1` zkopíruje pouze první bajt. Následující kód používá přenosné funkce znak bezpečně zkopírovat a druhý se zvýší `sz1` a `sz2` správně:

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
    {
        _mbscpy_s( sz1, 1, sz2 );
        sz1 = _mbsinc( sz1 );
        sz2 = _mbsinc( sz2 );
    }
    else
        sz2 = _mbsinc( sz2 );
}
```

## <a name="see-also"></a>Viz také:

[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)<br/>
[Porovnávání znaků](../text/character-comparison.md)
