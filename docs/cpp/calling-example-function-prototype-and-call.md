---
title: 'Příklad volání: Prototyp a volání'
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: f89f4f1917810baa585dd1661428e0809b93cca0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345112"
---
# <a name="calling-example-function-prototype-and-call"></a>Příklad volání: Prototyp a volání

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