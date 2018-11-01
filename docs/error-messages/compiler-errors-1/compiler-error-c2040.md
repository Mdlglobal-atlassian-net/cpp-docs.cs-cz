---
title: Chyba kompilátoru C2040
ms.date: 11/04/2016
f1_keywords:
- C2040
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
ms.openlocfilehash: b45ec25f1ed516ae73b242fdcc7c66f68c92f724
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624715"
---
# <a name="compiler-error-c2040"></a>Chyba kompilátoru C2040

'operator': "identifier1" se liší úrovněmi indirekce z "identifier2.

Zahrnující zadané operandy výrazu má nekompatibilní operandem nebo implicitně převeden typy operandů. Pokud jsou oba operandy aritmetického nebo obojí jsou nonarithmetic (například pole nebo ukazatel), použijí se beze změny. Je-li jeden operand je aritmetické a druhá ne, aritmetický operand je převeden na typ nonarithmetic operandu.

Tato ukázka generuje C2040 a ukazuje, jak ho opravit.

```
// C2040.cpp
// Compile by using: cl /c /W3 C2040.cpp
bool test() {
   char c = '3';
   return c == "3"; // C2446, C2040
   // return c == '3'; // OK
}
```