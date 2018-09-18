---
title: Chyba kompilátoru C2040 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2040
dev_langs:
- C++
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccfbacff97550e20c0dd0202e0737585ffd39d6d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016465"
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