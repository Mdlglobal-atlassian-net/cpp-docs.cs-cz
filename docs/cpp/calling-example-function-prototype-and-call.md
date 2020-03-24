---
title: 'Příklad volání: prototyp a volání funkce'
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: c41d7679be8b7faa3c8df1368d14815a1b840284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190167"
---
# <a name="calling-example-function-prototype-and-call"></a>Příklad volání: prototyp a volání funkce

**Specifické pro společnost Microsoft**

Následující příklad ukazuje výsledky volání funkce použitím různých konvencí volání.

Příklad je založen na následující kostře funkce. Nahraďte `calltype` příslušnou konvencí volání.

```cpp
void    calltype MyFunc( char c, short s, int i, double f );
.
.
.
void    MyFunc( char c, short s, int i, double f )
    {
    .
    .
    .
    }
.
.
.
MyFunc ('x', 12, 8192, 2.7183);
```

Další informace najdete v tématu [Výsledky příkladu volání](../cpp/results-of-calling-example.md).

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Konvence volání](../cpp/calling-conventions.md)
