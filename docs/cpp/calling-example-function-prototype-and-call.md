---
title: 'Příklad volání: prototyp a volání funkce'
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: f89f4f1917810baa585dd1661428e0809b93cca0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508177"
---
# <a name="calling-example-function-prototype-and-call"></a>Příklad volání: prototyp a volání funkce

## <a name="microsoft-specific"></a>Specifické pro Microsoft

Následující příklad ukazuje výsledky volání funkce použitím různých konvencí volání.

Příklad je založen na následující kostře funkce. Nahraďte `calltype` příslušnou konvencí volání.

```
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

Další informace najdete v tématu [výsledky příkladu volání](../cpp/results-of-calling-example.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Konvence volání](../cpp/calling-conventions.md)