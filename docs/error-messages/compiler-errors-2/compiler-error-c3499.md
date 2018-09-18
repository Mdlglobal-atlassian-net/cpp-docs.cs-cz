---
title: Chyba kompilátoru C3499 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3499
dev_langs:
- C++
helpviewer_keywords:
- C3499
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd4fbd928637eacaac3316ff2f4a1e6855365395
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054464"
---
# <a name="compiler-error-c3499"></a>Chyba kompilátoru C3499

výraz lambda, který byl zadán mít návratový typ void nemůže vracet hodnotu.

Kompilátor vygeneruje tuto chybu, pokud výraz lambda, který určuje `void` jako návratový typ, vrátí hodnotu; nebo pokud výraz lambda obsahuje více než jeden výraz a vrátí hodnotu, ale neurčuje její typ vrácené hodnoty.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Nesmí vracet hodnotu z výrazu lambda nebo

- Zadejte návratového typu výrazu lambda nebo

- Kombinace příkazů, které společně tvoří hlavní část výrazu lambda v jediném příkazu.

## <a name="example"></a>Příklad

Následující příklad generuje C3499 vzhledem k tomu, že hlavní část výrazu lambda obsahuje více příkazů a vrátí hodnotu, ale výraz lambda není určení návratového typu:

```
// C3499a.cpp

int main()
{
   [](int x) { int n = x * 2; return n; } (5); // C3499
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje dvě možná řešení pro C3499. První řešení poskytuje návratového typu výrazu lambda. Druhé řešení kombinuje příkazy, které tvoří hlavní část výrazu lambda v jediném příkazu.

```
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

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)