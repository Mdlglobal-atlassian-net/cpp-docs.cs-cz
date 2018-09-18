---
title: Chyba kompilátoru C3488 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3488
dev_langs:
- C++
helpviewer_keywords:
- C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15e1a21781eed96ee3a2a1430da8e43013393912
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061786"
---
# <a name="compiler-error-c3488"></a>Chyba kompilátoru C3488

'příkaz var' není povolený, pokud výchozí režim sběru je podle odkazu

Pokud určíte, že výchozí režim sběru pro výraz lambda je podle odkazu, nelze předat proměnnou s odkazem na klauzuli capture výrazu Tento výraz.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Proměnné explicitně nepředávejte klauzuli zachycení, nebo

- Nezadávejte výchozí režim sběru dat podle odkazu nebo

- Zadejte podle hodnoty jako výchozí režim sběru dat, nebo

- Předejte klauzule zachycení proměnné podle hodnoty. (To může změnit chování část výrazu lambda.)

## <a name="example"></a>Příklad

Následující příklad generuje C3488, protože odkaz na proměnnou `n` se zobrazí v klauzuli capture výrazu lambda výraz, jehož výchozí režim je podle odkazu:

```
// C3488a.cpp

int main()
{
   int n = 5;
   [&, &n]() { return n; } (); // C3488
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje na C3488 čtyři možná řešení:

```
// C3488b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass &n to the capture clause.
   [&]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-reference as the default capture mode.
   [&n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-value as the default capture mode.
   [=, &n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by value to the capture clause.
   [n]() { return n; } ();
}
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)