---
title: Chyba kompilátoru C3499
ms.date: 11/04/2016
f1_keywords:
- C3499
helpviewer_keywords:
- C3499
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
ms.openlocfilehash: e50aaeac4a9f02cf3e67c25a08afdc2df0f1c62f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738008"
---
# <a name="compiler-error-c3499"></a>Chyba kompilátoru C3499

lambda, která je zadaná tak, aby měla návratový typ void, nemůže vracet hodnotu.

Kompilátor vygeneruje tuto chybu, pokud výraz lambda, který určuje `void` jako návratový typ, vrátí hodnotu. nebo pokud výraz lambda obsahuje více než jeden příkaz a vrátí hodnotu, ale neurčuje jeho návratový typ.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Nevracet hodnotu z výrazu lambda nebo

- Zadejte návratový typ výrazu lambda nebo

- Kombinovat příkazy, které tvoří tělo výrazu lambda, do jediného příkazu.

## <a name="example"></a>Příklad

Následující příklad generuje C3499, protože tělo výrazu lambda obsahuje více příkazů a vrací hodnotu, ale výraz lambda neurčuje návratový typ:

```cpp
// C3499a.cpp

int main()
{
   [](int x) { int n = x * 2; return n; } (5); // C3499
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje dvě možná řešení pro C3499. První řešení poskytuje návratový typ výrazu lambda. Druhé řešení kombinuje příkazy, které tvoří tělo výrazu lambda, do jediného příkazu.

```cpp
// C3499b.cpp

int main()
{
   // Possible resolution 1:
   // Provide the return type of the lambda expression.
   [](int x) -> int { int n = x * 2; return n; } (5);

   // Possible resolution 2:
   // Combine the statements that make up the body of
   // the lambda expression into a single statement.
   [](int x) { return x * 2; } (5);
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
