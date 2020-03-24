---
title: Upozornění kompilátoru C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: c125fa84119c62e3090611c9a841f46eee759711
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165207"
---
# <a name="compiler-warning-c4439"></a>Upozornění kompilátoru C4439

' function ': definice funkce se spravovaným typem v podpisu musí mít konvenci volání __clrcall

Kompilátor implicitně nahradil konvenci volání pomocí [__clrcall](../../cpp/clrcall.md). Chcete-li vyřešit toto upozornění, odeberte `__cdecl` nebo `__stdcall` konvence volání.

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
