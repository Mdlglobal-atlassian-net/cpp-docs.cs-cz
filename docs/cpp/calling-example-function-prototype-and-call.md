---
title: 'Příklad volání: prototyp a volání funkce'
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: cbe9ee16db502c9e27dcbd74da4ef6a85f00960f
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857629"
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

## <a name="see-also"></a>Viz také:

[Konvence volání](../cpp/calling-conventions.md)