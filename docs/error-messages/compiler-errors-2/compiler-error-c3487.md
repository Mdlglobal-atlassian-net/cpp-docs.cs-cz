---
title: Chyba kompilátoru C3487
ms.date: 11/04/2016
f1_keywords:
- C3487
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
ms.openlocfilehash: a1c4b667e23ff167b28b9f22f93b0930545c915c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492590"
---
# <a name="compiler-error-c3487"></a>Chyba kompilátoru C3487

Typ vrácené: všechny návratové výrazy se musí odvozovat na stejný typ: dřív to bylo "návratovým typem.

Výraz lambda musíte zadat její typ vrácené hodnoty, pokud obsahuje jeden návratový příkaz. Pokud výraz lambda obsahuje více návratovými příkazy, musí všechny mají stejného typu.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Zadejte ukončovací návratový typ pro výraz lambda. Ověřte, že všechny vrátí z výrazu lambda jsou stejného typu nebo může být implicitně převeden na typ vrácené hodnoty.

## <a name="example"></a>Příklad

Následující příklad generuje C3487, protože se neshodují návratové typy výrazu lambda:

```
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

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)