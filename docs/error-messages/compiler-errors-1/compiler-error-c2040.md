---
title: Chyba kompilátoru C2040
ms.date: 11/04/2016
f1_keywords:
- C2040
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
ms.openlocfilehash: 8002d7168354b1213d01ca390a03b1baa5e35c88
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740413"
---
# <a name="compiler-error-c2040"></a>Chyba kompilátoru C2040

' operator ': ' identifier1 ' se odlišuje od ' identifier2 ' úrovně dereference.

Výraz zahrnující zadané operandy má nekompatibilní typy operandů nebo implicitně převedené typy operandů. Jsou-li oba operandy aritmetické, nebo jsou obě nearitmetické (například pole nebo ukazatel), používají se beze změny. Je-li jeden operand aritmetický a druhý není, je aritmetický operand převeden na typ nearitmetického operandu.

Tato ukázka generuje C2040 a ukazuje, jak ji opravit.

```cpp
// C2040.cpp
// Compile by using: cl /c /W3 C2040.cpp
bool test() {
   char c = '3';
   return c == "3"; // C2446, C2040
   // return c == '3'; // OK
}
```
