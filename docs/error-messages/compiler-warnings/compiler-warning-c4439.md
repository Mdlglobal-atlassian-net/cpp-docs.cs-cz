---
title: Upozornění kompilátoru C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: 7cab2e55fca640438051fbb79ac933e83d5f3cbb
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623659"
---
# <a name="compiler-warning-c4439"></a>Upozornění kompilátoru C4439

' function ': definice funkce se spravovaným typem v podpisu musí mít konvenci volání __clrcall

Kompilátor implicitně nahradil konvenci volání s [__clrcall](../../cpp/clrcall.md). Chcete-li vyřešit toto upozornění, odeberte `__cdecl` nebo `__stdcall` konvence volání.

C4439 se vždy vydá jako chyba. Toto upozornění můžete vypnout pomocí `#pragma warning` nebo **/WD**; Další informace najdete v tématech [Upozornění](../../preprocessor/warning.md) nebo [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4439.

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```