---
title: Upozornění kompilátoru C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: d604c234b9445a7e5304118124620f0057f30975
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541736"
---
# <a name="compiler-warning-c4439"></a>Upozornění kompilátoru C4439

'function': definice funkce se spravovaným typem v podpisu musí mít konvenci volání __clrcall

Kompilátor implicitně nahradit konvence volání s [__clrcall](../../cpp/clrcall.md). Pokud chcete vyřešit toto upozornění, odeberte `__cdecl` nebo `__stdcall` konvence volání.

C4439 je vždy vyvoláno jako chyba. Můžete vypnout toto upozornění se `#pragma warning` nebo **/wd**; naleznete v tématu [upozornění](../../preprocessor/warning.md) nebo [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md)Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C4439.

```
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```