---
title: Chyba kompilátoru C3487 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3487
dev_langs:
- C++
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acd0dad31a565b9e75741e3a66a5d48dfedec69f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087107"
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