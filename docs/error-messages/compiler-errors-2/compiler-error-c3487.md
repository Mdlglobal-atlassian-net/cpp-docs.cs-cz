---
title: Chyba kompilátoru C3487
ms.date: 11/04/2016
f1_keywords:
- C3487
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
ms.openlocfilehash: 7b38755470e3746066711382b2ed471badc8e197
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738437"
---
# <a name="compiler-error-c3487"></a>Chyba kompilátoru C3487

návratový typ: všechny návratové výrazy se musí odvozovat na stejný typ: dřív byl návratový typ.

Lambda musí specifikovat svůj návratový typ, pokud neobsahuje jediný návratový příkaz. Pokud lambda obsahuje více příkazů Return, musí mít všechny stejný typ.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Zadejte koncový návratový typ pro lambda. Ověřte, zda jsou všechny návraty z výrazu lambda stejného typu nebo lze implicitně převést na návratový typ.

## <a name="example"></a>Příklad

Následující příklad generuje C3487, protože návratové typy výrazu lambda se neshodují:

```cpp
// C3487.cpp
// Compile by using: cl /c /W4 C3487.cpp

int* test(int* pi) {
   // To fix the error, uncomment the trailing return type below
   auto odd_pointer = [=]() /* -> int* */ {
      if (*pi % 2)
         return pi;
      return nullptr; // C3487 - nullptr is not an int* type
   };
   return odd_pointer();
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
